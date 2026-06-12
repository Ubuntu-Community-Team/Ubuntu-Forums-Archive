---
title: "Keep having to reinstall! :-("
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by Satummoo on 2007-08-23
I really want to get into linux and am determined to figure out everything but so far it's not been going well.  I recently went from x64 to x86 after a few suggestions that it would be easier.  The only thing succesfull I got so far is the ability to get flash.  My biggest problem is with video drivers.  Everytime I try to enable them or try to install them by imputing codes into the terminal, ubuntu loads the boot screen and then goes blank.  I'm stuck from here and my only option is to completly reinstall.  I know there is a way to reinstall xserver(?) and I tried a code line but it took me through an entire mini reinstall where I had to pick out all my options which didn't let me go back into the graphical ubuntu.

The major thing I don't understand is if I need to enable the "disabled drivers" before I input the comands or after?  I've tried the ATI guide in the beginers forum and the one in the multimedia/video forum and nothing has worked.  The only semi succesfull way i've been able to install the video drivers is by using envy when I used x64.  This caused my auto updater not to work anymore and a few other 3D features were disabled :( I'm not sure if ENVY is x64 compatible and that's why it messed up but if anyone can help me I'd greatly appreciate it!

Also, how do I do a "system restore"?  After I have everything installed, is there a way to save all my settings so if something goes wrong (like the black screen) I don't have to redo every little comand (such as picking my keyboard and mousetype) and can just go back to my existing settings?

---

### Post by Satummoo on 2007-08-23
bump

---

### Post by nitro_n2o on 2007-08-23
so what i understand from your post is that you have a problem with the video decoders?.. but  installing these are pretty simple and you dont have to do anything in Feisty for that matter.. 
it'll do this automatically... anyways.. 
what did you do exactly to install them and what is the state of your system now.. do you have X

---

### Post by Hitchhiker42 on 2007-08-23
Are you using Feisty? Did you go to System> Administration>Restricted Drivers Manager and load the drivers from there? My understanding is that that *should* be all you need to do.

---

### Post by Blutack on 2007-08-23
Once you have a working xorg.conf, copy it to your home folder like this...
cp /etc/X11/xorg.conf /home/satummoo/xorg.conf-backup

When it all goes horrible, boot in recovery mode and type
cp /home/satummoo/xprg.conf-backup /etc/X11/xorg.conf

---

### Post by Satummoo on 2007-08-23
> **Blutack said:**
> Once you have a working xorg.conf, copy it to your home folder like this...
cp /etc/X11/xorg.conf /home/satummoo/xorg.conf-backup

When it all goes horrible, boot in recovery mode and type
cp /home/satummoo/xprg.conf-backup /etc/X11/xorg.conf

thanks this will help out a bunch.

I used envy again (except in x86) and it works!

To the above poster,  everytime I enabled my ATI driver in the rescricted drivers it would ask for a reboot and then after the reboot i'd get a blank screen.  I don't even see how you could install drivers after that.  Even though I fixed the problem, i'd still like to know for future problems how I would beable to do this if I were not able to use Envy and follow the scripts that everyone posted.

as of right now, i'm going to back up my files :)

---

### Post by Blutack on 2007-08-23
EEK!  Watch the typo, sorry.
cp /home/satummoo/xprg.conf-backup /etc/X11/xorg.conf

should be
cp /home/satummoo/xorg.conf-backup /etc/X11/xorg.conf

---

### Post by bjarneh on 2007-08-23
hi

do you have problems with video-codes (playing different media you find online or so) or do you have a problem with you nvidia or ati-card?

don't go for a re-install before a few things have been investigated....

---

### Post by anewguy on 2007-08-24
Some of the things suggested here require that you open a command line when your screen goes blank.  To do that, hold ctrl alt and press F2 then release the keys.  This should get you to a command line.  The blank screen after the log on screen usually indicates a video driver problem with the X server, but you can still get to the command line even though the screen is blank.

Also, any copy TO /etc/X11/xorg.conf is going to require the super user, so you need to preface the copy statement with "sudo ".  You'll just get a permissions error if you try it otherwise and it won't copy the file.

:)

---

