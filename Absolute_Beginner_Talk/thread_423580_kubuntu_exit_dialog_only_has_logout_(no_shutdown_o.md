---
title: "kubuntu exit dialog only has logout (no shutdown or other options)"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by ubnewbie2 on 2007-04-26
I installed kubuntu-desktop recently, and I notice when I try to logout/exit, I don't see the usual options I normally find from KDE.  Instead there is just a large pale mostly-empty rectangle with one option stuck in the middle - and this is the logout option.  

It takes me out of KDE back to the gdm login screen, where, of course, I can shutdown.  It's just that it's extra steps, when most distros just let you shutdown from within KDE.  Also that mostly-empty rectangle looks to me like there's other things should be there, but are missing for some reason.

---

### Post by igknighted on 2007-04-26
> **ubnewbie2 said:**
> I installed kubuntu-desktop recently, and I notice when I try to logout/exit, I don't see the usual options I normally find from KDE.  Instead there is just a large pale mostly-empty rectangle with one option stuck in the middle - and this is the logout option.  

It takes me out of KDE back to the gdm login screen, where, of course, I can shutdown.  It's just that it's extra steps, when most distros just let you shutdown from within KDE.  Also that mostly-empty rectangle looks to me like there's other things should be there, but are missing for some reason.

K Menu -> System Settings -> advanced -> Session manager and select "offer shutdown options"

I think the issue comes from the Kubuntu-desktop package, as my Kubuntu install has all the proper options.  It might also be that you are using gdm not kdm (not a problem, just confuses KDE).

---

### Post by rillip on 2007-04-26
If you do not see the options after enabling them as igknighted instructed, I have had one other issue come up with this.  When I ran out of disk space, I had to login to a recovery session to remove the files. After that, it continued to log me back into the same recovery session each time I booted.  I had to boot, and from the kdm chose to use a new session.  If you've done any work in a recovery mode lately that could be affecting you as well.  It's worth a try if nothing else works at least.

---

### Post by ubnewbie2 on 2007-04-26
> **igknighted said:**
> K Menu -> System Settings -> advanced -> Session manager and select "offer shutdown options"

I think the issue comes from the Kubuntu-desktop package, as my Kubuntu install has all the proper options.  It might also be that you are using gdm not kdm (not a problem, just confuses KDE).

The proper options are already set.  You might be right about gdm confusing KDE though.

---

### Post by ubnewbie2 on 2007-04-26
> **rillip said:**
> If you do not see the options after enabling them as igknighted instructed, I have had one other issue come up with this.  When I ran out of disk space, I had to login to a recovery session to remove the files. After that, it continued to log me back into the same recovery session each time I booted.  I had to boot, and from the kdm chose to use a new session.  If you've done any work in a recovery mode lately that could be affecting you as well.  It's worth a try if nothing else works at least.

Never used recovery mode, nor filled my disk up (it's a new install from 2 days ago).

---

### Post by igknighted on 2007-04-26
Are you using XGL with beryl or compiz?  That can cause this issue as well, but to get around it there is some weird workaround...

---

### Post by ubnewbie2 on 2007-04-26
> **igknighted said:**
> Are you using XGL with beryl or compiz?  That can cause this issue as well, but to get around it there is some weird workaround...

Actually, I don't even know what they are :(

---

### Post by drsaamah on 2007-05-04
nooooooooooo.... somebody suggest something else!!
I have looked forever to find a thread with this problem!
The weird thing is, when I first came to Ubuntu I was using Edgy.  And i installed KDE when I was on Edgy, and this was never an issue.  I culd suspend, hibernate, restart, whatever RIGHT from kde.
Then AFTER the Fiesty Fawn upgrade these options disappeared.  Its weird because KDE didnt even upgrade... its still version 3.5.
This is a big pain in the @$$. ANY other suggestions??

---

### Post by drsaamah on 2007-05-31
hey i dont know about you ubnewbie2 but I got a bunch of updates on adept_updater last week that finally fixed the problem.  I hope the same happened for you, good luck!

---

### Post by ubnewbie2 on 2007-06-01
> **drsaamah said:**
> hey i dont know about you ubnewbie2 but I got a bunch of updates on adept_updater last week that finally fixed the problem.  I hope the same happened for you, good luck!

I am not using kubuntu anymore, I've decided I like the plainer gnome desktop - for now anyway :-)  Glad to hear it's fixed though.

---

### Post by Nythain on 2007-06-01
not sure how much of this has already been solved or not, but this problem usually occurs from installing kubuntu-desktop and running kde through GDM instead of KDM like already mentioned... there's a terminal command to switch from one to the other but i dont know/cant remember what that command is

---

### Post by Jazkal on 2007-09-20
The command is: dpkg-reconfigure kdm

I am running Gutsy, and I have this issue.

I have run that command, and verified that I am not running GDM.

This is an install from Kubuntu, I've never even had gnome running on it.

Anyone else have any ideas on what to check?



EDIT: I figured out what my problem is. After getting the lattest updates today, compiz stopped working, and I had install a xgl package to get it to work. Well with this new combo, I loose the reboot and shutdown buttons. If I remove the xgl package, I get the buttons back, but compiz stops working.

---

### Post by mstreibe on 2007-10-21
This is just a me too response. I recently upgraded to kubuntu gutsy, and when ativating Xgl, there will only be a logout button. I have KDM running.

In the german ubuntu forum there was a solution for feisty which is related to xauth:

[http://wiki.ubuntuusers.de/Xgl](http://wiki.ubuntuusers.de/Xgl)

You'd need to add the following lines to the xgl start script:

cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"

On gutsy this would be /usr/share/xserver-xgl/Xgl-session, and this script already contains these xauth commands. But it still doesn't work.

I have no further idea how to sovle this. If anyone has another hint, I'd be glad to hear about it.

---

### Post by mmmiiikkkeee on 2007-10-24
I use kubuntu and have this problem since gutsy

clearly i do not have gdm installed:

sudo apt-get remove gdm
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package gdm is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I noticed this problem only started after I upgraded to gutsy.  I also noticed that if I change from using the "nvidia" closed source driver to the free "nv" driver then this problem goes away.  But i want to use the nvidia driver :( .   Do the other people with this problem also have nvidia cards.  does changing xorg.config to  device "nv" do any thing for you?

If any one has any more information on this i have submitted a bug report here: [https://bugs.launchpad.net/ubuntu/+bug/154668](https://bugs.launchpad.net/ubuntu/+bug/154668)
thanks hope this get fixed :)

---

### Post by kevin79 on 2008-01-24
> **mstreibe said:**
> This is just a me too response. I recently upgraded to kubuntu gutsy, and when ativating Xgl, there will only be a logout button. I have KDM running.

In the german ubuntu forum there was a solution for feisty which is related to xauth:

[http://wiki.ubuntuusers.de/Xgl](http://wiki.ubuntuusers.de/Xgl)

You'd need to add the following lines to the xgl start script:

cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"

On gutsy this would be /usr/share/xserver-xgl/Xgl-session, and this script already contains these xauth commands. But it still doesn't work.

I have no further idea how to sovle this. If anyone has another hint, I'd be glad to hear about it.

Did you by chance ever find a fix for this?

---

### Post by kaiguy57 on 2008-01-29
I definitely have the same problem here, including the nvidia vs. nv driver issue. I hope this gets resolved soon!

---

### Post by TuxLove on 2008-02-11
This definitely seems related to Xgl -- though mstreibe's suggestions of changing  [COLOR=Purple]/usr/share/xserver-xgl/Xgl-session[/COLOR] didn't fix it for me.

What *does* fix it is removing** xserver-xgl**. Then I get the proper shutdown menu -- but no compiz.

The interesting thing is it only occurs on my laptop (with an ATI graphics card). I don't get in on my desktop (with an NVidia card), even though both were installed with same Gutsy CD.

---

### Post by tesseract_rider on 2008-04-28
same issue including nv vs nvidia option - this has been the case for edgy. gutsy and hardy for me.

---

