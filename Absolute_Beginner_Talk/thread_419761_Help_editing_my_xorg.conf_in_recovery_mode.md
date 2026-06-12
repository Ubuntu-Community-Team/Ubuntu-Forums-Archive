---
title: "Help editing my xorg.conf in recovery mode"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Gleep on 2007-04-23
After installing feisty, I wanted Beryl back, so, when simply installing all things 'beryl' through synaptic didn't work properly, I went to hunt down a tutorial.

I used this one: [http://www.arsgeek.com/?p=986](http://www.arsgeek.com/?p=986)

And followed the steps. Editing my xorg.conf like that was a bad idea, when I restarted gnome I got errors and X wouldn't start. 

So now i'm booted into recovery mode, but unsure how to edit my xorg.conf, so I can remove everything and change it back to how it was. I don't just want to break things more.

Any help would be appreciated.

---

### Post by taurus on 2007-04-23
```
nano -Bw /etc/X11/xorg.conf
```
<Ctrl>o to save and <Ctrl>x to exit.

---

### Post by Patrick K on 2007-04-23
Type:> nano etc/X11/xorg.confThis will bring up the nano editor.

---

### Post by Gleep on 2007-04-23
Thanks guys, I've edited it, fingers crossed it isn't broken!

---

### Post by Gleep on 2007-04-23
Woo it's fixed and not only that, but the wierd grey ugly background that came up on the splash screen has gone and is back to normal. I've no idea what this was, but it's gone now so... XD

---

### Post by taurus on 2007-04-23
> **Patrick K said:**
> Type:This will bring up the nano editor.

You need to include the leading /  like /etc/X11/xorg.conf or you would get an error message of file's not being found.

---

### Post by Patrick K on 2007-04-23
> **taurus said:**
> You need to include the leading /  like /etc/X11/xorg.conf or you would get an error message of file's not being found.You are correct.

---

### Post by Gleep on 2007-04-23
Here we go again >_<

This time I followed [www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

And again, it's buggered X.

This time I backed up my xorg.conf file, but I'm not sure how to revert to the backup, or if doing this will help, since I removed the fglrx driver.

Think the general lesson here is I should just stop following these...

---

### Post by pppetter on 2007-04-23
just type 
> cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

you did the same thing when you backed it up, but just reversed with the files :)

---

### Post by Gleep on 2007-04-23
Ok thanks I'll try that. Won't the fact I uninstalled the drivers matter?

---

### Post by Gleep on 2007-04-23
Nope I still get "Failed to start the X server (your graphical interface) It is likely that it is not set up correctly" etc and when I view the details it says it failed to load "fglrx" (module does not exist, 0) and no drivers available.

How to I install it again or whatever I need to do?

Obviously I can only boot into recovery mode.

---

### Post by taurus on 2007-04-23
```
dpkg-reconfigure xserver-xorg
```

---

### Post by Gleep on 2007-04-23
> **taurus said:**
> ```
dpkg-reconfigure xserver-xorg
```Thanks, will try that now.

---

### Post by Gleep on 2007-04-23
Ok in the middle of reconfiguring this it's given me this message:

"xserver-xorg postinst warning: overwritting possibly-customised configuration file; backup in /etc/X11/xorg.conf.2007043151812"

And then gives me the root@verena-desktop:~# so I don't know what to do, I don't want to type anything and break it, I don't know what it wants me to do, can anyone tell me?

---

### Post by Gleep on 2007-04-23
*bump* Not to be a pain, if anyone knows what it wants me to do could someone give me a hand?

It's just my computer is sat there waiting for me to tell it what to do and I can't use it till I've sorted this :(

---

### Post by silverglade00 on 2007-04-23
It means that it wrote you a new xorg.conf and backed up the old (broken) one as the file xorg.conf.2007043151812

Just go ahead and give it a shot. try typing 
```
startx
```

Oops, no, you should reboot out of recovery mode and log in under your normal username.

---

### Post by Gleep on 2007-04-23
Thanks I typed "reboot" and well, rebooted, so now it's up and running again. Now using this: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) to try sort out the drivers so I can get beryl.

Now I've got screen resolution to sort... it's at  1024x768 and er... everything is massive and ugly. Googling this found me this [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto) which looks good and has a quickfix for ATI cards with the fglrx driver, so I'll try that when I'm sure it's working.

---

