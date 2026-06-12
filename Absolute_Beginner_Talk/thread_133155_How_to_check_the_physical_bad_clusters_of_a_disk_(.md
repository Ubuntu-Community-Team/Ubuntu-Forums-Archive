---
title: "How to check the physical bad clusters of a disk (/dev/hda2) ? (ntfs partition)"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-02-19
How to check the physical bad clusters of a disk (/dev/hda2) ? (ntfs partition)
  (damaged after a windows virus on a friend's pc)
  Can it make a list of damaged clusters ?
  
Thank you very much,

Patrick

---

### Post by patrick295767 on 2006-02-20
man badblocks
  
  
[http://snow.nl/dist/xhtmlc/ch03s02.html](http://snow.nl/dist/xhtmlc/ch03s02.html)

Greetz


> Der Befehl badblocks durchsucht und liefert die Information über fehlerhafte Blöcke
des Dateisystems und es geht ganz einfach mit:

badblocks /dev/hda

Da auf der Konsole standardmäßig nichts ausgeschrieben wird, ist der Parameter -s anzugeben. Dadurch werden die jeweils geprüften Blöcke ausgegeben. Es ist sogar möglich einen zu prüfenden Bereich festzulegen, wobei erst der letzte Block und dann der erste Block bestimmt werden muss. Sobald der Befehl fertig ist steht nur noch die Meldung done auf dem Bildschirm und -v ist für sogennaten verbose mode.

# badblocks -vs /dev/hda
Checking for bad blocks in read-only mode
From block 0 to 19531250
Checking for bad blocks (read-only test): badblocks -vs /dev/hdadone
Pass completed, 0 bad blocks found.


oder radikal mit:

# badblocks -ws /dev/hda

wo jeden Block überprüft, indem zunächst in ihn hineinschreibt
und danach aus ihm liest.
Verwende nie badblocks mit -w option an einem existierendem file system !
Diese option vernichtet daten.
Wenn man write-mode test an einem existierendem file system will,
sollte man -n verwenden.
Ist zwar langsamer, aber behält die Daten.


Wer nur eine Blockangabe macht, legt damit fest, dass im Bereich Null bis Blockangabe zu Prüfen ist:

# badblocks /dev/hda -s 100
Checking for bad blocks (read-only test): done


Weitere Parameter sind ein Umlenken in eine Ausgabedatei durch
die Option -o, oder ?i , das ein Einlesen aus einer Datei bestimmt,
so dass bereits als fehlerhaft erkannte Blöcke nicht wieder ausgeworfen werden.
Der Sinn ist schnell erklärt. Das Formatieren einer neuen Partition wird durch einen Parameter gesteuert, so dass bereits Blöcke, die im Vorfeld als Fehlerhaft erkannt wurden automatisch ausgespart werden.
Diese Option wird bei dem Kommando mke2fs -l ebenso eingesetzt wie bei dem Kommando mkfs. Eine weitere Möglichkeit ist es wirklich einen Schreibtest auf der Festplatte mit der Option -w durchzuführen, doch dies ist langwierig.

Andere Informationen findet man natürlich mit man badblocks.

Gruss
Christoph


To recover ur data (if bad clusters):
[http://www.abul.org/article335.html](http://www.abul.org/article335.html)

---

