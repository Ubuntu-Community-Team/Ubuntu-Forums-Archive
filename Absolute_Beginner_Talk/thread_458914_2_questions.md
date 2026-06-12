---
title: "2 questions"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by quinnten83 on 2007-05-30
I have 2 questions.
I would like to know how to play DVD on my laptop under Ubuntu. I tried with the instructions here
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28dvd%29%7C%28playback%29]("http://https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28dvd%29%7C%28playback%29")
But at the step where you have to do the shell script, I get an error.
I tried using it in VLC mediaplayer, but I have no idea how to get that working.
if anyone can enlighten me?

I also tried installing openoffice draw, but both add remove programs and synaptic tell me it is already installed.
I can't see it under applications or in systems, though.
I tried deinstalling it and reinstalling, but there was no change.
apt-get and aptitude tell me the same thing. I tried starting it from the command line using the line: openoffice.org2-draw
I also have automatix installed, but I haven't used it to install this, but i heard that automatix sometimes causes problems with installations. 
Anybody have an idea why i can't see it in de applications list or get it started?

---

### Post by Simran on 2007-05-30
To use open office draw, just use open office word; then 

File > New > Drawing ... and your into open office draw :)

Simran

---

### Post by TwistesdTexan on 2007-05-30
Have you tried automatix?
[http://www.getautomatix.com/]("http://www.getautomatix.com/")
This is a great source for adding codecs for new users.

---

### Post by mlentink on 2007-05-30
> **quinnten83 said:**
> I also tried installing openoffice draw, but both add remove programs and synaptic tell me it is already installed.
I can't see it under applications or in systems, though.
I tried deinstalling it and reinstalling, but there was no change.
apt-get and aptitude tell me the same thing. I tried starting it from the command line using the line: openoffice.org2-draw
I also have automatix installed, but I haven't used it to install this, but i heard that automatix sometimes causes problems with installations. 
Anybody have an idea why i can't see it in de applications list or get it started?

Start OOo (any document, Writer, Calc ...].
As soon as your new empty document has appeared, click on File>New 
You can then select a drawing, which will open up Draw.
Perhaps you can make a new launcher for it as well, but I'm at work behind a Windows machine right now, so I can't check that out for you

Edit: sorry, duplicate post

---

### Post by justifier on 2007-05-30
With automatix, that you have installed use it to install all the media codecs, then try to play your DVD, MP£ or anyother propiertary format, should work

---

### Post by quinnten83 on 2007-05-30
Soooo...
open office draw is not a separate program like it is on windows. Ok, that would explain a few things.
i  think i have all the codecs installed, since i used automtix from the start. I just don't know how to operate the software.
When i select open DVD in VLC mediaplayer, the program just closes (i have a separate animation for closing in beryl and it is performed).

---

### Post by mlentink on 2007-05-30
> **quinnten83 said:**
> Soooo...
open office draw is not a separate program like it is on windows. Ok, that would explain a few things.

I think it is. There's  just no launcher for it. I don' know the command to start OOo from the commandline, but it's  something like "ooffice -writer" You should be able to start Draw with "ooffice -draw", afaik. You can then make a separate launcher (and separate menu-item) for it, if you wish.

---

### Post by eldepeche on 2007-05-30
I think OpenOffice Draw goes under Applications -> Graphics rather than Office with the rest of OO. Not sure though...

---

### Post by quinnten83 on 2007-06-03
> **eldepeche said:**
> I think OpenOffice Draw goes under Applications -> Graphics rather than Office with the rest of OO. Not sure though...

allready looked,
it's not there.
I've installed dia and kivio though, they sorta do the same thing I needed done in Draw.

---

### Post by mrreality13 on 2007-06-03
try installing KMPlayer and all its codecs thats what i use to watch movies

---

