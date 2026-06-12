---
title: "[SOLVED] This is really embarrasing but..."
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by 449 on 2007-12-05
I can't seem to remember how to correctly burn files to a dvd. I attached an screenshot of all the files. Does it look like I have missing/extra files? I already tried to burn it twice ,but both times ended up not being able to be read by my 360. I tried just writing the files write to the dvd ,but that didn't work. Help... :confused:

---

### Post by -grubby on 2007-12-05
are you sure the Microsoft XBOX 360 can read normal DVDs?

---

### Post by 449 on 2007-12-05
> **nathangrubb said:**
> are you sure the Microsoft XBOX 360 can read normal DVDs?

Yeah, I burnt tons with Windoze.

---

### Post by skyjacker on 2007-12-05
What burning program are you using? I have burned a lot of music and data dvd's using k3b, and they sound great.

---

### Post by 449 on 2007-12-05
> **skyjacker said:**
> What burning program are you using? I have burned a lot of music and data dvd's using k3b, and they sound great.

Well the files I'm burning is a actual dvd. Like if I right click the folder and open in VLC it shows the menu and everything. I thought I could just make a data cd ,but I guess not...

---

### Post by scxtt on 2007-12-05
can't you make an ISO of the DVD, then burn the ISO?  and i thought K3B / Gnomebaker had (basic) dvd-authoring options ...

---

### Post by 449 on 2007-12-05
> **scxtt said:**
> can't you make an ISO of the DVD, then burn the ISO?  and i thought K3B / Gnomebaker had (basic) dvd-authoring options ...

How would I go about making an iso. :confused:

---

### Post by 449 on 2007-12-05
> **449 said:**
> How would I go about making an iso. :confused:

Can someone give me a link? I'm having trouble one. :confused:

---

### Post by scxtt on 2007-12-05
do you own the original DVD?  if so, it should be easy to make an ISO from it - should be a menu option ...

if not, and you're SURE you have all the files you could possibly use something like genisoimage to make one out of the directory and then burn that ISO ...

no guarantees, but that's my idea so far :p ...

---

### Post by GSF1200S on 2007-12-05
> **scxtt said:**
> do you own the original DVD?  if so, it should be easy to make an ISO from it - should be a menu option ...

if not, and you're SURE you have all the files you could possibly use something like genisoimage to make one out of the directory and then burn that ISO ...

no guarantees, but that's my idea so far :p ...

kiso will create and allow you to edit .iso as well, if I remember correctly..

---

### Post by SOULRiDER on 2007-12-05
I think it would be best if the topic was taken elsewhere, its something Illgeal youre talking about :P

---

### Post by Dr Small on 2007-12-05
K9Copy can create ISO files out of DVDs.
And SOULRiDER, it is not illigeal to make copies if you own it.

Dr Small

---

### Post by crjackson on 2007-12-05
> **Dr Small said:**
> K9Copy can create ISO files out of DVDs.
And SOULRiDER, it is not illigeal to make copies if you own it.

Dr Small

Dr. Small - You're exactly right!

I think the reason you can't burn your movie is because of copy protection.  Like Dr Small said - Try K9Copy.

---

### Post by ruibernardo on 2007-12-05
Hi 449,

from your screenshot, you have DeVeDe installed. You can use it to make your DVD. 

Add the video files and click "Advanced" and then the "Misc." tab. In that tab check "This file is allready in MPEG-PS format, ready to DVD/xCD." (or something like that). That option will prevent DeVeDe from reencoding the files. Then back in the main window select you want to create an ISO file. Then burn it with k3b if you want (in Gnome I just right-click on the file in Nautilus and select "Write to disc...").

Another GUI to create DVD-video is [qdvdauthor]("http://qdvdauthor.sourceforge.net/"). Another one could be [dvdstyler]("http://www.dvdstyler.de/"). Both are on the repositories. Both create DVD videos from already encoded video files. 

Just as a suggestion you can use [avidemux]("http://fixounet.free.fr/avidemux/") to encode video files, it has an "Auto" menu to encode many different video files types (avi, mpeg, etc) to mpeg-1 with PAL and SECAM output, sound settings, all this from a GUI. Avidemux is also on the repos.

To create an ISO file for a dvd video from files that are dvd ready on a directory in the console, type:
```
mkisofs --dvd-video directory/ > mydvd.iso
```EDIT: I thought that it was to burn files to a DVD, not copy one. As Dr. Small said, k9copy is very good for what you want. Now it's me who is embarrassed. :oops:

---

