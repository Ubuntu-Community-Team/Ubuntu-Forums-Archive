---
title: "Video Card Driver Death"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by triangleman on 2006-09-28
I dual boot my system Ubuntu 6.06 and Windows xp.  I am trying to get off windows but i'm not man enough to go cold turkey.  I was attempting to install video card drivers for my Radeon 9550.  Now when i start up ubuntu it is all crazy and i can't really do anything because the screen is all wigged out.  How can i revert to back to the driver i was using before i tryed to install some? What commands should i put in when i boot to ubuntu recovery mode?

Thanks

---

### Post by mejy on 2006-09-28
> **triangleman said:**
> I dual boot my system Ubuntu 6.06 and Windows xp.  I am trying to get off windows but i'm not man enough to go cold turkey.  I was attempting to install video card drivers for my Radeon 9550.  Now when i start up ubuntu it is all crazy and i can't really do anything because the screen is all wigged out.  How can i revert to back to the driver i was using before i tryed to install some? What commands should i put in when i boot to ubuntu recovery mode?

Thanks

On boot up, open the menu (you may have to press escape at a prompt that flashes up), and select the oldest kernel (lowest version number) available in safe mode.

You should now be able to boot to a screen telling you XOrg won't start.  Press Control + Alt + F1.  Login with your username and password.  Now, try the command

```
cd /etc/X11/
ls
```

If there is anything like xorg.conf.bak or xorg.conf.07122006, do

```
sudo cp [file name] xorg.conf
```

If that doesn't work, try

```
sudo dpkg-reconfigure xserver-xorg
```.

---

### Post by charles.g.moore on 2006-09-28
if you made a copy of your xorg.conf then  from a command line

sudo cp xorg.conf.backup xorg.conf

that should do the trick at least get you back to where you were...

---

### Post by petri on 2006-09-28
With an older kernel there is no problems with the driver issue. If the backup doesn't work do this:

Boot **recovery mode** and then you should get a root-prompt (commandline) there you paste this

```
dpkg-reconfigure xserver-xorg
```

Answer yse to everything else but the driver. There you have to choose **vesa**. Then reboot with ```
shutdown -r now
``` When you are at the **recovery mode** you are **root** and you don't have to use **sudo**.

Then you should be able to boot and login as normally but the screen resolution etc is not pretty. Here you can find a good howto for ATI, I think you will have to choose **Method 2** [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

