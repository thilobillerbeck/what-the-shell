---
# try also 'default' to start simple
theme: apple-basic
title: 'What the Shell?!'
titleTemplate: '%s'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
info: false
remoteAssets: true
download: true
exportFilename: 'what-the-shell-slides'
lineNumbers: false
favicon: 'https://thilo-billerbeck.com/favicon-32x32.png'
# some information about the slides, markdown enabled
# persist drawings in exports and build
drawings:
  persist: false
# use UnoCSS
css: unocss
layout: intro-image
image: 'https://unsplash.com/photos/xbEVM6oJ1Fs/download?ixid=MnwxMjA3fDB8MXxzZWFyY2h8OHx8Y29tcHV0ZXIlMjB0ZXJtaW5hbHxlbnwwfHx8fDE2NjU2MDQxNDU&force=true&w=1920'
---

<div class="absolute top-10">
  <span class="font-700">
    Thilo Billerbeck | 13.11.2022
  </span>
</div>

<div class="absolute bottom-10">
  <h1>What the Shell?!</h1>
  <p>Von schwarzen Fenstern mit weissem Text und Rohren</p>
</div>

---
layout: section
---

# Was ist diese Shell?

---
layout: image-right
image: 'https://cdn-learn.adafruit.com/assets/assets/000/021/847/original/raspberry_pi_800px-Two_women_operating_ENIAC_%28full_resolution%29.jpg?1418881181'
---
# Damals(TM)

- große Kellefüllende Maschinen
- Steckverbinder und Knöpfe
- kein wirklich interaktives graphisches Interface

---
layout: image-right
image: 'http://www.computersciencelab.com/ComputerHistory/HtmlHelp/Images2/TeletypeASR33.jpg'
---
# Teletype

- Im Prinzip besserer Telegraf
- konnte zur Kommunikation verwendet werden
- aber auch zur Interaktion mit Maschinen
- Grundstein für das heutige tty

---
layout: image-right
image: 'https://upload.wikimedia.org/wikipedia/commons/thumb/6/6a/Ibm_px_xt_color.jpg/800px-Ibm_px_xt_color.jpg'
---
# PCs

- Computer ziehen in Haushalte ein
- Anfangs nur Kommandozeilen (IBM PC, Apple II, etc.)
- Keine GUI von Haus aus

---
layout: image-right
image: 'https://cdn-learn.adafruit.com/assets/assets/000/021/976/original/raspberry_pi_Apple_Macintosh_Desktop.png?1419971362'
---
# GUIs

- Kommandozeilen werden nach und nach durch GUIs ersetzt
- Relevanz sinkt stark
- Heutzutage sind sie zur Arbeit im normalen Alltag eigentlich nicht mehr notwendig

---

# Terminals vs. Terminal Emulatoren

## Terminal
- Textmode
- Eingaben gehen direkt in die Shell, keine umliegende Form der Interaktion
- Quasi das Gehirn

## Terminal Emulator
- Wrapper um das Terminal
- Im GUI Betrieb notwendig
- Bietet Features um die Arbeit mit dem Terminal bequemer zu machen

---

# Prompt (prompt string 1)

<div class="text-2xl py-4">
<code lang="bash">
[user@machine ~]$
</code>
</div>

| Part | Bedeutung |
| --- | --- |
| `user` | Nutzername |
| `machine` | Hostname des Rechners |
| `~` | Ordner |


---
layout: section
---

# DEMO TIME

---

# Erstes Programm

- Immer essenzieller Output
- Shell arbeitet mit Argumenten

```bash
uname --operating-system
```

- Argument 0: uname
- Argument 1: operating system

---

# Aguments und Optionen

## Argumente

- Argument 0 ist immer das Programm
- Danach kommen weitere Argumente wie etwa Dateinamen

```bash
cat file.txt file2.txt
```

## Optionen

- Modifizieren die Ausfuehrung des Programms
- 2 Formen
  - Option: `--color red` setzte eine Option auf einen bestimmten Wert
  - Flags: `--flag` schaltet eine bestimmte Option ein
- Optionen haben meistens eine Kurzform (`--option` wird zu `-o`)

---

# Do one thing and do it well

Definiert durch Ken Thompson und dokumentiert durch Doug McIlroy im Bell System Technical Journal (1978)

1. Make each program do one thing well. [...]
2. Expect the output of every program to become the input to another [...]

tldr: Funktionaler Ansatz, analog zu Funktionsaufrufen, Argumenten und Rueckgabewerten d.h.:

- Programme sind Funktionen (arg 0)
- Flags und Optionen sind Argumente (arg 1...)
- Output ist der Rueckgabewert

---
layout: two-cols
---

<template v-slot:default>

# History

- Befehl `history`
- Aufrufen letzter Befehle mit den Pfeiltasten
- Manche Shells bieten auch Autocomplete an

</template>
<template v-slot:right>


```bash
[thilo@my-distrobox ~]$ history
    1  whereis zsh
    2  sudo nano /etc/fstab 
    3  sudo mkdir -p /data
    4  sudo mount -a
    5  ls
    6  cd /data/
    7  ls
    8  cd ..
    9  cd /home/thilo/
   10  clear
```

</template>

---

# Shell schliessen

- Befehl `exit`

---

# pwd

**`pwd` - Aktuellen Pfad anzeigen**

```bash
[thilo@my-distrobox ~]$ pwd
/home/thilo
```

---
layout: two-cols
---

<template v-slot:default>

# cd

- `cd path/to/directory` - gehe zu einem bestimmten Ordner
- `cd ..` - gehe einen Ordner zurueck
- `cd` - gehe ins Home Verzeichnis

</template>
<template v-slot:right>

# ls

- `ls` - listet aktuelles Verzeichnis auf
- `ls -a` - listat alle Dateien im Verzeichnis auf
- `ls -l` - listat aktuelles Verzeichnis detailliert auf

</template>

---

# file, less

- `file` - liefert Informationen über Dateien
- `less` - Datei lesen

---

# cp, mv, mkdir, rm, ln

- `cp` - Kopiere Dateien von a nach b
- `cp -r` - Kopiere Dateien rekursiv (also Ordner)
- `mv` - Verschiebe Dateien von a nach b
- `mkdir` - Erstelle Ordner
- `mkdir -p` - Erstelle Ordner und Elternordner falls nicht vorhanden
- `rm` - Dateien loeschen
- `ln -s` - Symlink erstellen

---

# Redirects

Programmausgaben können in Dateien geschrieben werden

```bash
command > file
command 1> file
```

Programmfehler ebenfalls

```bash
command 2> file
```

und auch gleichzeitig

```bash
command 2> errorfile 1> file
```

und auch beides in eine Datei

```bash
command &> file
```

---

## Pipes

Wir können jetzt Output in Dateien schreiben, aber wie verknüpfen wir Programme mitenander.

```bash
command1 | command2 | command3 | ...
```

Beispiel

```bash
uname -r | less
```

---

# cat, sort, uniq, grep, wc, head, tail

---

## cat - conCATinate

Dateien zusammenfuegen

```bash
cat file1 file2 file3
cat file1 file2 > output_file
```

## sort - sortieren

Sortiere Dateien oder Output

```bash
sort file
```

---

## uniq - Duplikate entferneen

```bash
sort file | uniq
```

## grep - Suche nach regulaeren Ausdruecken

```bash
grep "expr" file
```

## wc - count

```bash
wc --lines file
```

---

# head - Anfang einer Datei

```bash
head --lines 10 file
head --bytes 10 file
```

# tail -- Ende der Datei

Analog zu head

```bash
tail --follow file
```

---

# echo

Eigentlich ein einfaches print

```bash
echo "Hallo Welt"
echo "$PATH"
```

---

# Environment

Umgebungsvariablen sind quasi globale Variablen, auf die wir immer Zugriff haben.

```bash
echo "$HOSTNAME"
```

- speichern von Zustand
- Programmeinstellungen
- Fun Fac: Prompt ist eine Umgebungsvariable `PS1` (prompt string 1)

```bash
echo "$SHELL"
```

---
layout: two-cols
---

<template v-slot:default>

# Skripte

- Skriptsprache um Befehlsfolgen automatisieren zu können
- Möglichkeiten
  - normale Befehle
  - Variablen
  - Kontrollstrukturen
  - Loops
  - etc.


</template>
<template v-slot:right>

```bash
#!/usr/bin/env bash

# Befehl
echo Hallo

# Variable
Name="Thilo"

# Befehl mit Variable
echo $Name

# Kontrollstrukturen

if [ $Name != "Thilo" ]
then
    echo "Schade, du bist jemand anderes"
else
    echo "Freut mich, dass du es bist"
fi

# Loops

for Zahl in {1..5}
do
    echo "$Zahl"
done

```

</template>

