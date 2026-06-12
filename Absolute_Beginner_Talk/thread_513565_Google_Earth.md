---
title: "Google Earth"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by bugster on 2007-07-30
I am trying to install Google Earth with Automatix.  Tried 3 times now and each time it proceeds until I get the error message

 Xlib:   extension  “Xfree86” missing on display “:0.0”

I have previously had difficulty getting my screen resolution to work in Ubuntu and wonder if I have messed up the xorg.conf file? Don't want to mess with that file because the screen is perfect now.

---

### Post by Peter76 on 2007-07-30
Use the medibuntu repositories; I'm hearing mixed stuff about Automatix ( though  I never used it myself, so I'm sorry if I piss someone off )

---

### Post by bugster on 2007-07-30
Thanks Peter will give it a try.

---

### Post by rocknrolf77 on 2007-07-30
Look here : [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth) :)

---

### Post by rfruth on 2007-07-30
I went straight to Google [http://earth.google.com/support/bin/answer.py?answer=44713&useful=1&show_useful=1]("http://earth.google.com/support/bin/answer.py?answer=44713&useful=1&show_useful=1")
and followed the instructions, no problem :)

---

### Post by bugster on 2007-08-01
At last progress.  I've now got an icon on my desktop reading GoogleEarthLinux.bin.

I'd appreciate some help on what to do next, thanks.

---

### Post by swoll1980 on 2007-08-01
Automatix only works half the time. A quarter of the time it doesn't do anything, the other quarter of the time it breaks your dpkg. Your not missing anything though google earth is buggy as hell on linux

---

### Post by Nezing on 2007-08-01
Copy and paste **all of this **in Terminal.and follow **all **instructions.It may take a little time,but it worked for me:

wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
sh GoogleEarthLinux.bin

---

### Post by bugster on 2007-08-01
Thanks swoll and nezing.  I did what you said nezing and the same fault occurred - I get

Xlib:  extension "XFree86-DRI" missing on display ":0.0".

then it hangs.

---

### Post by Paul820 on 2007-08-01
If you have the icon on your desktop do this

> cd ~/Desktop
sudo chmod +x GoogleEarthLinux.bin
./GoogleEarthLinux.bin

Assuming you got the file from google earth download site.

---

### Post by bugster on 2007-08-01
Thanks Paul - tried that and it hangs at the following point

Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...

Any ideas??

---

### Post by bugster on 2007-08-01
Perhaps it is best if I post my original query.

[B][I]"I am trying to install Google Earth with Automatix. Tried 3 times now and each time it proceeds until I get the error message

Xlib: extension “Xfree86” missing on display “:0.0”

I have previously had difficulty getting my screen resolution to work in Ubuntu and wonder if I have messed up the xorg.conf file? Don't want to mess with that file because the screen is perfect now."[/I][/B]
__________________

I've tried the solutions suggested in the thread above without success.  Would I be better posting the problem in another area of the forum ?

Thanks

Keith

---

### Post by justagamer on 2007-08-01
Well i know this is no help at all but i used automatix2 and it worked no problem also i went to google its self so ya i know this has been no help just wanted to let you know automatix does work and i have never had a problem with it.

---

### Post by bren on 2007-08-01
now I am not sure but I seem to recall getting the exact same failure message on google earth install.

it turned out (i think) that it was because accelerated graphics was not installed/enabled.


when i sorted this and ran glxgears (from the terminal) to check the frame rate was reasonable (try it before and after) I was able to install google earth no problem..

what is your graphics card and what does SYSTEM | ADMIN | RESTRICTED DRIVERS say about your current accel/non accell

hope that helps

bren

here is a link that was useful to me previously..
[http://groups.google.com/group/earth-linux/browse_thread/thread/6acf610c4de4ee01](http://groups.google.com/group/earth-linux/browse_thread/thread/6acf610c4de4ee01)

---

