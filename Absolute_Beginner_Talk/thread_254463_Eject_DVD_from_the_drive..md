---
title: "Eject DVD from the drive."
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by harerama on 2006-09-10
I've installed Mplayer. I am able to watch dvd. But I am not able to eject dvd from the drive. Can anyone help

I can open the dvd/rw drive just pushing the button. But not cd drive.:( 

Thank you.

---

### Post by ruppmeister on 2006-09-10
If you can see the drive mount on your desktop, try to right mouse click on the drive with the cd in it and click "eject". That should take care of it.

---

### Post by harerama on 2006-09-10
No I don't see it on my desktop.

---

### Post by YeahBuntu on 2006-09-10
I have this problem with one of my CD drives it freaked me out in the begining but now I just right click and eject.  Are you using the gnome desktop or some other desktop?

---

### Post by teet on 2006-09-10
> **harerama said:**
> I've installed Mplayer. I am able to watch dvd. But I am not able to eject dvd from the drive. Can anyone help

I can open the dvd/rw drive just pushing the button. But not cd drive.:( 

Thank you.

Make sure you close Mplayer first...the DVD won't eject if something is trying to access or play it.

If that doesn't work, just pop open a terminal (either gnome-terminal or konsole depending on whether you use KDE or gnome) and type (you guessed it) 'eject' at the command prompt...easy as pie.

If you're really lazy like me and don't want to reach down and push the button to close your DVD drive, you can then just type 'eject -t' at the command prompt to close the drive.

-teet

---

### Post by harerama on 2006-09-10
You know when I put music cd or data cd icon appears on desktop. However when 
 I put this dvd(movie) then nothing appears on desktop and pushing button won't work. I can play this dvd though. or maybe only this particular dvd disk it won't work. I have only one this particular dvd so I will try with other dvd disk some day.

Thanks

---

### Post by Blur-king on 2006-09-10
Somehow dapper only allow one cdrom drive to be able to eject the cd  manually. You need to use the following HOwTo that I found and use on two of my box.

This HOWTO is just for trick to make the cd eject by pressing the eject button on the cd drive which has been included into dapper, but this is how to do it on breezy

Open Terminal and type/ cut&paste

Code:
sudo sysctl dev.cdrom.lock=0

now your cd can be ejected by simply clicking on the eject button but if you restart it will no longer be available, to make it permanent, 
then type

Code:
sudo sh -c 'echo "dev.cdrom.lock=0" >> /etc/sysctl.conf'

Now it will be permanent.  :wink:

cherio

         [IMG]http://www.ubuntuforums.org/images/misc/progress.gif[/IMG]                                                                                                                            [[IMG]http://www.ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://www.ubuntuforums.org/editpost.php?do=editpost&p=1381813")

---

