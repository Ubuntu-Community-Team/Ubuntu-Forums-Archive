---
title: "Kwrite vs Abiword"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by siddartha on 2007-10-16
As I am not getting too far on an older thread about free Office packs I would ask for something more precise: a personal comparison between Kwrite and Abiword. So far I am using Ubuntu with the default Gnome but some of the apps I use are made for KDE, meaning I work in a mixed environment. Thus sticking with GTK vs QT is not a discrimination reason. I am looking more for functionality.

So what do you preffer and why: Abiword or Kwrite?

Cheers,
Sidd

---

### Post by Dr Small on 2007-10-16
Never used any of them. What is wrong with OpenOffice ?

---

### Post by megabyte405 on 2007-10-16
I may be biased (I'm an AbiWord volunteer developer and a Google Summer of Code participant working on AbiWord) but I really like AbiWord, way better than OOo and I haven't used KWrite.  The upcoming 2.6 version contains real-time collaboration technology, which is awesome.  The existing version is fast, highly compatible with tons and tons of file formats, and generally respects your systems settings: isn't there a QT GTK theme or something like that?

Anyway, a plug for AbiWord. :D

Ryan

---

### Post by siddartha on 2007-10-16
> **Dr Small said:**
> Never used any of them. What is wrong with OpenOffice ?

Well, it's too big in any sense. The packs are imense - the biggest I suppose on the Ubuntu CD. The memory footprint is excellent for a Panzer Tank, not for an office pack. This means awful loading times, partly because of this huge amount of data having to be transferred from disk to memory. It does work well if you have enough memory, but lately most developers in the world of free software have taken the same approach as the windows developers years ago. "It's enough by today's memory standards". No, it isn't. A stupid gnome applet has 2 to 6 megs. Add some toys like that, a memory leaking browser like Firefox, maybe some database helping you with cacheing the fields in the memory for fast access and the memory becomes way too small. Dunno way, but although I use a multitasking system the reasoning is like for a DOS game - free some conventional memory and it will fly.

Add to that - OO is loading java for many tasks which leads to more overhead.

No, I am not talking about getting it to work on a low-resource system. I have a decent system and I want that system to work, not to way for some applet to start in order to check a one page word file that was sent by somebody. Yes, evince should do this. This is what is stated on the web page. Anyway this means 5 years to not at all when it comes to office support as they keep polishing the pdf support - which is bad anyway compared with the acrobat.

So... Kwrite or Abiword?

---

### Post by siddartha on 2007-10-16
> **megabyte405 said:**
> The upcoming 2.6 version contains real-time collaboration technology, which is awesome.

Is there a roadmap published somewhere as well as a list of features and a sincere compatibility report with the doc formats? I sincerely dislike people sending word documents, yet there are offices where they specifically ask for word. A pdf would solve the problem right away (I mean it should look the same on my computer and on their), but they keep asking for .doc.

---

### Post by Paulmd on 2007-10-17
> **siddartha said:**
> Is there a roadmap published somewhere as well as a list of features and a sincere compatibility report with the doc formats? I sincerely dislike people sending word documents, yet there are offices where they specifically ask for word. A pdf would solve the problem right away (I mean it should look the same on my computer and on their), but they keep asking for .doc.

OpenOffice reads and Writes Word. (I know this doesn't help much ). You are out of luck, for the moment with the newer Word 2007 .docx format.

As for people ASKING for Word.... Word opens .rtf documents just fine. RTF is VERY standard.

---

### Post by FredB on 2007-10-17
> **megabyte405 said:**
> I may be biased (I'm an AbiWord volunteer developer and a Google Summer of Code participant working on AbiWord) but I really like AbiWord, way better than OOo and I haven't used KWrite.  The upcoming 2.6 version contains real-time collaboration technology, which is awesome.  The existing version is fast, highly compatible with tons and tons of file formats, and generally respects your systems settings: isn't there a QT GTK theme or something like that?

Anyway, a plug for AbiWord. :D

Ryan

I used Abiword before OOo became really usable. And a 2.6 version of Abiword ? great !

Let's hope it will be available really soon.

---

### Post by hyper_ch on 2007-10-17
Well, I think the default memory settings in OOo suck and make it slow to load... if you alter them and deactivate java it's much bettetr to use.

---

### Post by mivo on 2007-10-17
KWrite is nicely integrated into KOffice, and has document tabs. The KOffice developers are moving away from supporting closed formats, though, so if you relay on the ability to open MS Office documents, it is not a good choice. Very fast in a KDE environment though, although it has crashed for me a few times (usually when closing it). OpenOffice is bloated and slow even on a relatively fast machine, and loading times are not impressive either, but it does offer the best MS Office compatibility by far if this is desired. I usually use it for composing simple WYSIWYG HTML documents, which neither KWrite nor Abiword are even decent at. Abiword is very snappy, stable. easy to use, not overloaded or bloated, fun to use, and it has a small memory footprint. I use it as my standard word processor (I don't require MS compatibility for my job), and if it supported decent export of HTML documents, I could do completely without OpenOffice.

---

### Post by Sef on 2007-10-17
Try them both and see what you prefer.   KWrite does make .odf the default format.

---

### Post by hyper_ch on 2007-10-17
If you want to speed up OOo a bit, do this:

(1) Open any Openoffice.org application

(2) Go to Tools--->Options

(3) Under Openoffice.org select Memory and use the following settings/apply the following changes:
[LIST]
[*]Undo: Number of steps = 25
[*]Graphics cache: Use for OOo = 128MB
[*]Memory per object = 20.0MB
[*]Cache for inserted objects: Number of objects = 20
[*]Uncheck OOo Quickstarter
[/LIST]

(4) Click on the Java section
[LIST]
[*]Uncheck "Use a Java runtime environment"
[/LIST]

(5) Select OK

(6) Restart Openoffice and feel the new speed

---

### Post by xc3RnbFO8P on 2007-10-17
Abiword!

---

### Post by siddartha on 2007-10-17
> **hyper_ch said:**
> If you want to speed up OOo a bit, do this:

Well... I can bet from now that it would still be larger in terms of memory consumption as both Abiword and Kwrite loaded together. :( And it is a pitty as I am not sure that the extra functions it offers should weight so much in terms of lowered performance in comparison with the 'lighter' siblings. Than, disabling java would reduce its advantages as some modules do require Java to work.

---

### Post by maybeway36 on 2007-10-17
The thing I hate about AbiWord is it uses .abw instead of .odt.

---

### Post by siddartha on 2007-10-17
[QUOTE=mivo;3548560I usually use it for composing simple WYSIWYG HTML documents, which neither KWrite nor Abiword are even decent at.[/QUOTE]

Have you tried NVU for this job alone?

---

