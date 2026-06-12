---
title: "Change resolution"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by USR612 on 2008-03-02
Hi, 
Yesterday while fiddling with Ubuntu (I'm quite new to Linux), I accidentally changed the resolution higher than I meant (to whatever is higher than 1024 x 768 ).  Unfortunately, my monitor can't cope with this, and I'm stuck with a black screen.  Is there any way to change the resolution before logging in?
Thanks!

---

### Post by Crooksey on 2008-03-02
Yea, edit your...

/etc/X11/xorg.conf 

Edit the file only allowing 1024x768.

---

### Post by USR612 on 2008-03-03
Hi,
Thanks for the help, but I'm not sure how to edit the file before I log in (the screen goes blank upon logging in, and I have less command line experience than I have Linux experience - little to none).  I can open the file in my windows partition with notepad but I'm not sure what to put in it.
Any help would be greatly appreciated!
Thanks.

---

### Post by taurus on 2008-03-03
Press <Ctrl><Alt>F2 and log in with your username and password.  Then, edit /etc/X11/xorg.conf with

```
sudo nano -Bw /etc/X11/xorg.conf
```
When you are done with making the changes, save it with <Ctrl>o and exit with <Ctrl>x.  Now, get back to the GUI login screen with <Alt>F7 and restart X server again, <Ctrl><Alt>Backspace.

---

### Post by USR612 on 2008-03-05
Sorry, you'll have to forgive my Linux incompetence, but when I press <Ctrl><Alt>F2 my screen goes blank, as if on sleep.  As well as this, when I open the xorg.conf file, what should I be changing?
Thanks!

---

### Post by taurus on 2008-03-05
In that case, just boot into recovery mode from GRUB menu and edit from there.

```
nano -Bw /etc/X11/xorg.conf
```
Again, save the changes with <Ctrl>o and exit with <Ctrl>x.  Now, reboot and see what happens.

```
shutdown -r now
```

---

### Post by USR612 on 2008-03-05
Thanks for the reply, but I'm still unable to do this.  I reach the login screen fine but as usual, when I log in the screen simply goes blank. As mentioned, I can open the xorg.conf file in the Windows partition but I'm not sure what I should be looking for/changing.
Thanks!

---

### Post by taurus on 2008-03-05
If you look near the end of /etc/X11/xorg.conf, you would see a bunch of resolutions.  Remove the one that your monitor doesn't support.  Save it and reboot into Ubuntu and see if that fixes the problem.

---

### Post by USR612 on 2008-03-14
Hi,
Sorry I'm so late getting back.  Before messing around from the windows partition, I was able to log into the failsafe terminal and remove the highest resolution.  Unfortunately, now when I log in, I am able to see the Ubuntu default background colour, and a message comes up for a very short period of time telling me of some error while loading/saving configuration information.  It never stays long enough for me to read entirely.  After this I'm just stuck with the default background/splash screen and a cursor.
  Is this a problem that can be remedied?
Thanks!

- I almost forgot, I would like to post the contents of the xorg.conf file, but when opening it from the windows partition, its not in its proper order, I'd be glad to post it though, if it's of any help.
Thanks!

---

