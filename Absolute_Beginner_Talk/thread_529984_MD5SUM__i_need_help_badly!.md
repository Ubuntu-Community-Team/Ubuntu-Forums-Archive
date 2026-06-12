---
title: "MD5SUM  i need help badly!"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by redfox1160 on 2007-08-19
I really dont understand MD5SUM at all. I havent installed it yet and i dont want to. Is there another way to do this? Please help!

---

### Post by Bachstelze on 2007-08-19
To do what ? The md5sum is used only to ensure that the ISO file wasn't corrupted during download.

---

### Post by redfox1160 on 2007-08-19
Thats what i need help with, i dont know where to get it or if i have to use it...also, how do i use it (i was getting confused reading the guide)

---

### Post by Bachstelze on 2007-08-19
You don't *have* to use it, but it is recommended because if you have a corrupted ISO file, it won't work and you will have wasted a CD for nothing. To get it, just google for "md5sum win32" (if you're on Windows).

---

### Post by Ek0nomik on 2007-08-19
For Windows:

[http://www.irnis.net/gloss/md5sum-windows.shtml](http://www.irnis.net/gloss/md5sum-windows.shtml)
[http://etree.org/md5com.html](http://etree.org/md5com.html)

For Ubuntu:

Accessories/Terminal:

```
md5sum imagename.iso
```

---

### Post by redfox1160 on 2007-08-19
thanks.

---

### Post by redfox1160 on 2007-08-19
do i just hit 'download' at the bottom of [http://www.irnis.net/gloss/md5sum-windows.shtml]("http://www.irnis.net/gloss/md5sum-windows.shtml")?

---

### Post by Ek0nomik on 2007-08-19
Yep.  :)

---

### Post by Ek0nomik on 2007-08-19
You can also use:

[http://www.pc-tools.net/win32/md5sums/](http://www.pc-tools.net/win32/md5sums/)

[http://www.openoffice.org/dev_docs/using_md5sums.html](http://www.openoffice.org/dev_docs/using_md5sums.html)

and probably hundreds more.

---

### Post by redfox1160 on 2007-08-19
thanks

---

### Post by redfox1160 on 2007-08-19
how do i uninstall it before the 30 days are up (in the License agreement it says it expires in 30 days unless you buy a license)?

---

### Post by Ek0nomik on 2007-08-19
> **redfox1160@verizon.net said:**
> thanks

Anytime.  :)

Also, might I suggest you change your user name on the forums?  It will probably increase the amount of spam you get in your verizon.net mailbox.  :)

---

### Post by Ek0nomik on 2007-08-19
> **redfox1160@verizon.net said:**
> how do i uninstall it before the 30 days are up (in the License agreement it says it expires in 30 days unless you buy a license)?

Doh.  I didn't know any of the links I provided you with were shareware.

Personally I'd uninstall it now and download a different one that is free for life.

---

### Post by wolfen69 on 2007-08-19
if you're on linux using k3b for burning, it will automatically generate an MD5sum, which you can (quickly) visually compare to the MD5sum you have.

---

### Post by redfox1160 on 2007-08-19
do you know any other links (also, can i change my name without making a new profile)

---

### Post by redfox1160 on 2007-08-19
im using windows xp

---

### Post by euler_fan on 2007-08-19
If you search sourceforge.net for "md5" there are any plenty of good open source apps for doing what you want to do.

---

### Post by Ek0nomik on 2007-08-19
Changing your username:

[http://ubuntuforums.org/showthread.php?t=431652](http://ubuntuforums.org/showthread.php?t=431652)

I would just private message an Admin and they can probably change it for you.  :)

Surely one of the four links I gave you is a freeware md5sum checker?

---

### Post by Ek0nomik on 2007-08-19
Yes... even more...

[http://md5deep.sourceforge.net/](http://md5deep.sourceforge.net/)

[http://www.brandonstaggs.com/filecheckmd5/](http://www.brandonstaggs.com/filecheckmd5/)

[http://www.md5summer.org/](http://www.md5summer.org/)

---

### Post by redfox1160 on 2007-08-19
Do i need to extract it into System32?

---

### Post by VraiChevalier on 2007-08-19
Hey redfox,

I use this one with my Win XP. Seems to work quite well. Just install it as you would any other app.

[http://www.nullriver.com/](http://www.nullriver.com/)

---

### Post by redfox1160 on 2007-08-19
thanks!

---

### Post by asmoore82 on 2007-08-19
also, it can be very help to run an md5 check on a CD after burning to make sure its perfect.
and even better, if the CD is a few months old and you feel like checking it again;
place the cd in the drive, don't close the drive, open a terminal, and ...
```
~ $ dd if=/dev/cdrom | md5sum
```
this operation should take about 6~7 minutes but it's very good to know that the CD is perfect.
On a side note, all this jargon about burning at lower speeds is nonsense, I routinely burn
distros at max speed and always check them with md5 and never have a problem.

---

### Post by redfox1160 on 2007-08-19
where do i get the MD5sum? Also, Thanks guys for all your help cause im really new to all this...

---

### Post by Ek0nomik on 2007-08-19
> **asmoore82 said:**
> also, it can be very help to run an md5 check on a CD after burning to make sure its perfect.
and even better, if the CD is a few months old and you feel like checking it again;
place the cd in the drive, don't close the drive, open a terminal, and ...
```
~ $ dd if=/dev/cdrom | md5sum
```
this operation should take about 6~7 minutes but it's very good to know that the CD is perfect.
On a side note, all this jargon about burning at lower speeds is nonsense, I routinely burn
distros at max speed and always check them with md5 and never have a problem.

He stated he was running Windows multiple times.

**redfox**:  The md5sum, with most software displays it in the program itself.  I suppose some software won't, but most will.  It will will a long line of text of numbers and letters.

---

### Post by redfox1160 on 2007-08-19
i need it for the compare thing, is it on the site?

---

### Post by Ek0nomik on 2007-08-19
> **redfox1160 said:**
> i need it for the compare thing, is it on the site?

Which version of Ubuntu did you download?  The md5sum is different for each version.

---

### Post by redfox1160 on 2007-08-19
nvm... i found it... and it was correct...\\:D/

---

### Post by Ek0nomik on 2007-08-19
> **redfox1160 said:**
> nvm... i found it... and it was correct...\\:D/

[http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/)

The above link is for Feisty 7.04.

Edit:  I see you got it.  Excellent.  :)

---

### Post by redfox1160 on 2007-08-20
now i just need to burn the image to a disk...

---

### Post by redfox1160 on 2007-08-20
There's only one problem, i need to get a monitor. I'll probably get one tomorrow, but that means i have to w8 till then to use ubuntu:cry::-({|=:cry:.

---

### Post by Ek0nomik on 2007-08-20
> **redfox1160 said:**
> There's only one problem, i need to get a monitor. I'll probably get one tomorrow, but that means i have to w8 till then to use ubuntu:cry::-({|=:cry:.

A monitor usually helps.  :)

If you are just going to use the box to serve data (acting as a server) you could probably just go to Goodwill and keep a cheap one.

---

