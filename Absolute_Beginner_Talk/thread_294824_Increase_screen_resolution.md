---
title: "Increase screen resolution"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by col_b on 2006-11-07
Hello,

Just installed 6.10.  Have another thread on the go regarding an ssh connection.

Anyway, I also want to increase the screen resolution to 1280x1024, but I don't have the option for this in the Screen Resolution section.  I've read about altering the xorg.conf file, but it opens it as a readonly file, and says I don't have permission to save changes, even thought I've created a .bak and a .org.  

Can anyone give me any clues as to what to do?

Thanks again in advance.

Col

---

### Post by sbassett on 2006-11-07
have you tried opening the terminal and typing:

```
gksudo gedit /etc/X11/xorg.conf
```

?

---

### Post by Bachstelze on 2006-11-07
1) What kind of videocard do you have ?

2) To edit files outside your home directory, you need to be root. In Ubuntu, this is done by adding *sudo* before the command, like this :

```
sudo nano /etc/X11/xorg.conf
```

3) To configure your X server, you might want to run this :

```
sudo dpkg-reconfigure xserver-xorg
```

It will launch a wizard which will help you configuring it.

---

### Post by col_b on 2006-11-07
Thanks for the replies.

Ok, i tried gksudo gedit /etc/X11/xorg.conf and that worked.  I altered the file to include "1280x1024" and have saved the changes.  Do I just need to reboot now?

Cheers

Col

---

### Post by sbassett on 2006-11-07
Or simply restart the X server. Close everything and Ctrl+Alt+BackSpace will do the trick, and take you back to the logon screen.

---

### Post by col_b on 2006-11-07
Ok, I altered the xorg.conf file, rebooted, but I'm still at 1024x768 with no option to go to 1280x1024.  Also, the screen refresh rate is REALLY slow, i.e. it takes ages to scroll to the bottom of a web page etc.

I tried rebooting completely, but it's still the same... 

Any suggestions?

Thanks in advance,

Col

---

### Post by Bachstelze on 2006-11-07
> **HymnToLife said:**
> 1) What kind of videocard do you have ?


...

---

### Post by col_b on 2006-11-07
OK.

HymnToLife, I ran this sudo dpkg-reconfigure xserver-xorg as you suggested.
I selected 1280x1024, rebooted, and I now have 1280x1024 screen resolution :) :) :) :) :) 

But!  The rendering is still awful!  The graphics card is NVIDA GFORCE 7300LE (I think).

Any suggestions to sort the poor rendering (i.e it takes ages to move/scroll down a page?)

Thanks, once again, in advance

Col

---

### Post by findus on 2006-11-07
If you have an nvidia graphics card, and you have installed nvidia-glx, you can alter your resolution by using the nvidia settings program.  If not,

sudo dpkg-reconfigure xserver-xorg

and add 1280 x 1024 by pressing space when you get to the resolution menu.  Restart x and you should be able to go to a higher resolution

---

### Post by Bachstelze on 2006-11-07
```
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```

Restart X with Ctrl+Alt+BkSp, voilà :) Much easier than installing them in FreeBSD, I had a hard time with those :p

---

### Post by findus on 2006-11-07
forget my last post then!

Are you running nvdia-glx? might solve your problems!

---

### Post by Imsati on 2006-11-07
Ahhh, Nvidia... click here and you may find it helpful. Basically there are two drivers for NVidia cards, depenging on how old they are.


[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by col_b on 2006-11-07
HymnToLife, 

ok, i ran sudo apt-get install nvidia-glx and it installed it fine.  However, when I ran sudo nvidia-glx-config enable, I received the following error message:

Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.

Any ideas on how to solve?

Thanks once again!

Col

---

### Post by Bachstelze on 2006-11-07
hmm, do you have the restricted modules for your current kernel installed ? I thought nvidia-glx installed them as dependencies but it seems it doesn't... Try to run this

```
sudo apt-get install linux-restricted-modules-$(uname -r)
```

and if it installed something, try *sudo nvidia-glx-config enable* again.

---

### Post by col_b on 2006-11-07
:) :) :) 

OK.  everything's sorted now.  Not sure what I did tho...

I went to this page:

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

Typed in this command:

sudo nvidia-xconfig

Then it gave me some errors, but it told me how to sort them.  Can't remember what it told me to type...  But I then typed the nvidia enable command, and it told me to restart X.  So I did, and now I've got 1280x1024 resolution and the rendering is fine.

Thanks for all your help folks!

Cheers,
Col

---

