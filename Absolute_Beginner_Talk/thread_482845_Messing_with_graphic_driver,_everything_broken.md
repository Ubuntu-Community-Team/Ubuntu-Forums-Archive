---
title: "Messing with graphic driver, everything broken"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by kid.Koala on 2007-06-24
Ok,
I use Ubuntu 6.06 and I was trying to instal Beryl so I messed arount Beryl forum and
God knows why, I folowed this Guide ([COLOR="Blue"][Ubuntu Edgy Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")[/COLOR])

Now, when booting Ubuntu i can't get graphic look, i get login screen but in DOS mode if you understand.
(No typical login screen, only letters)

Graphic card:
NVIDIA GeForce4 Ti 4200 with AGP8X

I messed up big time.... :(

---

### Post by deanjm1963 on 2007-06-24
This might not work if you've done several "saves" of your xorg.conf file.

boot up ubuntu and log in as you at the command prompt.

type sudo cp /etc/X11/xorg.conf~ /etc/X11/xorg.conf

and restart the machine.

any file with a tilde " ~ " at the end of it is a "hidden backup file" so you might be lucky!

Fingers crossed.

Dean

---

### Post by Malta paul on 2007-06-24
Hi, I know what you mean it has happened to me!
What I did is not what our experts would do, but it did work. Perhaps some one will give you a better answer.
Anyway what I did  was first boot in the recover mode and checked what the problem is. I am sure it will be a corrupt Xorg.conf file.
Next boot into Ubuntu using your live boot disk. then go to /etc/X11 and copy the xorg.conf file to a USB pen drive or floppy dsk.
Reboot in recovery mode, cd to Root and etc/X11 rename you original xorg.conf to backup and copy in live dsk copied xorg.conf file. then reboot and it should work.
If you really get it all messed up you can reinstall Ubuntu - hope you have backed up your personnel files though.
Good luck hope this is of some help ;)

---

### Post by kid.Koala on 2007-06-24
ok, ill see today if any of this will help (I hope so!!)

I hope its oni xorg file....

THNX ALL! :D

---

### Post by Crafty Kisses on 2007-06-24
> **kid.Koala said:**
> Ok,
I use Ubuntu 6.06 and I was trying to instal Beryl so I messed arount Beryl forum and
God knows why, I folowed this Guide ([COLOR="Blue"][Ubuntu Edgy Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")[/COLOR])

Now, when booting Ubuntu i can't get graphic look, i get login screen but in DOS mode if you understand.
(No typical login screen, only letters)

Graphic card:
NVIDIA GeForce4 Ti 4200 with AGP8X

I messed up big time.... :(

You can try two things, first off reconfigure your X server:
```
sudo dpkg-reconfigure xserver-xorg
```
Then you might want to try to back up the X server file by doing the following:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
Then if anything ever goes wrong, you can recover the file by doing the following:
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

---

### Post by kid.Koala on 2007-06-25
OK, report:

When I copyed xorg.conf file from Live CD and pasted it in /etc/X11
and rebooted the system everything was doing gr8 and gray screen appeared with that round circly mouse that was spinning and then nothing happened,

i pressed CTRL+ALT+F8 and last line was "Running local boot scripts  /etc/rc.local"


Part 2.
I read more carefouly what the error says when booting normaly, with no changes:

Is says something about usr/share/X11/rgb
and
etc/X11/xorg.conf


so if u get me, help
can any1 send me their xorg.conf file?

;) THNX ALL

---

### Post by molly_001 on 2007-06-25
Looks like you're going to need to use (at command prompt)
    code:              
**sudo dpkg-reconfigure xserver-xorg**



Just hit CTRL + ALT + F1 as it boots up and then give your Username, your password,
and then type that command.

You'll go through about twenty questions in text mode, and you have to hit on the right combination of things.  Go through it once, you will see, then report back.

My suggestions:  use  i810 , 1024x768 res, 16 colors, monitor auto "on"

---

### Post by kid.Koala on 2007-06-25
I tryed,
i followed all the steps and when i got to the Colour mode (1,2,4,8,16,24)
what ever mode I select and press enter i get message like this:

New file is cr8ed xorg.conf.2XXXXXXXXXX (some number)
then i copyed it over existing xorg.conf file and rebooted, and nothing new happened....

Does the message:
"Couldn't open RGB-DB '/usr/share/X11/rgb'
means anything?


huh, hard to fix.... :(

---

