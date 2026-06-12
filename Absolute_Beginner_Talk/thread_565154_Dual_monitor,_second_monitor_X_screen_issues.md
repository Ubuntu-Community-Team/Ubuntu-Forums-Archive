---
title: "Dual monitor, second monitor X screen issues"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2007-10-01
I have finally got my screen resolution to how i want it, with the fantastic help from these forums.  The final issues with video i am having(before i move on to sound) is setting up my second monitor.  I can set it up as twin view but i want it has seperate X screen.  I setup as x screen and when i try to apply i get a message that i must save xorg and then restart but when i try to save i get this error:

ERROR: Unable to create backup file '/etc/X11/xorg.conf.backup'.

and when i restart nothing changes.  Any thoughts?

---

### Post by RyanZec on 2007-10-01
and i am doing this through the nvidia-settings program

---

### Post by RyanZec on 2007-10-01
I tried to copy and paste the preview into the xorg.conf myself and restart but when i restart  X server did not start so i had to use the backup and then restarted the X server.  Still trying to figure this out.

---

### Post by Beggar on 2007-10-02
You need to run 

```
 gksudo nvidia-settings
```

As the /etc/X11/xogr.conf file is not going to be owned by your user.

*snip*
since when does the nvidia-settings tool auto backup your xorg.conf? Shows how often I use it I guess :)
*/snip*

Oh and good luck with that, I hate the nvidia-settings tool, it always messes up my conf file, and adds tap to click to my touchpad, I usually just get the xorg.conf file it generates and use it as a template to change the file by hand :)

---

### Post by bodhi.zazen on 2007-10-02
That should be :

```
gksu nvidia-settings
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Usually it does not matter, but on those rare occasions where it does you can damage your system.

---

### Post by RyanZec on 2007-10-02
is there anyway i can setup my monitor like i can on windows.  basically both winodw are seperate and i can drag and drop from onr monitor to the other.  For instance if i max in Twinview it maxs it out on both of the screen but i can drag and drop but in X screen i can max normally but can't drag and drop.  it's not big deal i can max per screen manually in both screen, just annoying.

---

### Post by bodhi.zazen on 2007-10-02
Some window managers are more dual monitor aware then others.

Of the "big 3" xfce is best, so my advice would be to consider xfce.

The newer versions of KDE may also be better then gnome, I have not compared the two recently.

I use Fluxbox, but I have a custom configuration to go with it ...

---

### Post by RyanZec on 2007-10-02
will my window manager limit what applications i can use(like WIne or whatever)?

---

### Post by bodhi.zazen on 2007-10-02
NO

You can use KDE apps on Gnome (K3b for example) , xfce on gnome, etc

The downside is you will pull in the various kde/xfce libs and you will have some duplicate applications.

If you like xfce, you can fresh install xubuntu if you want to change.

You could also install xfce or kde without xubuntu-desktop or kubuntu-desktop. The desktop versions includes all the bells and whistles ...

---

### Post by RyanZec on 2007-10-02
so the only difference from kubuntu and xubuntu is the window manager?  I ther any way to install mutliple window managers on ubuntu and then select which one i want to use(i think Suse did this when i tried them)?

---

### Post by bodhi.zazen on 2007-10-02
yep

Install as many s you like 

At the log-in screen select the "session" you want ...

You can also run multiple sessions :

[http://ubuntuforums.org/showthread.php?t=271674](http://ubuntuforums.org/showthread.php?t=271674)

---

