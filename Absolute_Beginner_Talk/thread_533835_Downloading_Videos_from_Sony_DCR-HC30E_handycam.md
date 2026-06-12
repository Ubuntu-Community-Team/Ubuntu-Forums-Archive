---
title: "Downloading Videos from Sony DCR-HC30E handycam"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by pkj on 2007-08-24
Want to download video from my handycam.....

plugging it via USB port. The memory stick is detected and i am able to transfer all the pictures onto my desktop...But can't figure out how to go about downloading videos...

I have mplayer and VLC installed.....

Help will be highly appreciated.....

pkj

---

### Post by Amazona aestiva on 2007-08-24
Plug in the Firewire (IEEE 1394) and use Kino to capture it to the computer.
Use the link in my signature to install Kino.

And Firewire isn't USB!

---

### Post by pkj on 2007-08-24
I have Firewire card installed (i was earlier using it with windows)...I plug the camcorder in it but nothing happens....

How do i know if my firewire card has been accepted by ubuntu and working......
Will kino solve this issue


pkj

---

### Post by Amazona aestiva on 2007-08-24
This isn't an issue, don't worry!

Just install kino:
[http://www.getdeb.net/app.php?name=Kino]("http://www.getdeb.net/app.php?name=Kino")

After install run kino. Than Edit->Preferences
In preferences choose IEEE 1394
Two situation:
[SIZE="3"]1.[/SIZE]If there is an error message follow the instructions: (picture1)
-Open terminal
-type:```
sudo chown * /dev/raw1394
```
[COLOR="Red"]Don't forget to change * to your user name![/COLOR]
[COLOR="Red"]And[/COLOR] you might type this every time when you want to capture with kino!

[SIZE="3"]2.[/SIZE] If Kino find the camera You can start capture.(picture2)

Note:Kino records in dv format(9GB/40min). Don't worry, it can export to Xvid. (heavy compression & high quality)

There usually a few more problem. Post Your questions, I'll watch this thread.
Good luck!

---

### Post by pkj on 2007-08-25
Able to install kino....

after opening it, i am navigating to Edit > Preferances , to select IEEE 1394, but the following is displayed

IEEE 1394 sub-system is not responding
The raw 1394 module must be loaded and you must have read and write access to /dev/raw1394

Can't make out what to do further.......

pkj

---

### Post by Amazona aestiva on 2007-08-25
Open terminal and type:
```
sudo chown * /dev/raw1394
```
[COLOR="Red"]* must be Your _user name_[/COLOR]
Need to type this every time when You want to capture!(after reboot)

---

### Post by pkj on 2007-08-25
EUREKA !!!!!!!!!!!!!!!!!!!!

Its working......

Thanks a lot....

pkj

---

### Post by Amazona aestiva on 2007-08-25
Congratulation!
=D>=D>=D>=D>=D>

---

### Post by MrHat on 2007-08-26
I didn't want to start a new thread when this problem seems similar to mine. I'm getting the following, when I try to use capture on kino

" WARNING: dv1934 kernel module not loaded or failure to read/write /dev/dv1394/0 "

I've been trying to fix it with the help from this thread and [this other.]("http://ubuntuforums.org/showthread.php?t=142992&highlight=dv1934+kernel+module-loaded+OR+failure+to+read%2Fwrite+%2Fdev%2Fdv1394%2F0") which has only lead to the situation where the text is:

" WARNING: dv1934 kernel module not loaded or failure to read/write /dev/raw1394 "


I would really appreciate all the help I can get

---

