---
title: "Hosed important file. Help me fix."
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Front187 on 2007-07-25
Ahhh, it feels good to be back in my familiar Windows environment.  So far this has been a trek through the jungle for me.

This will be a two part question.

I managed to setup my system to dual boot Ubuntu and XP and the first and last thing I've done so far is attempting to change the resolution.

I have the intel 945 chipset and a bunch of resolutions that I cannot use.  I read many successful reports of people fixing their resolution problems, most of which differed in some way.  

Anyway, I logged in as root in order to edit xorg.conf, and yes I made a backup first.  Wierd thing is though, I can get a resolution up to 1280xSomething under root but only 6xx something under my regular username.

Anyway, I proceeded to edit xorg.conf and now I can't get the GUI portion of Ubuntu.  I simply need to rename the backup file from outside it.

Also, more tips on my resolution problem would be appreciated.

Thanks in advance :)

---

### Post by confused57 on 2007-07-25
> **Front187 said:**
> Ahhh, it feels good to be back in my familiar Windows environment.  So far this has been a trek through the jungle for me.

This will be a two part question.

I managed to setup my system to dual boot Ubuntu and XP and the first and last thing I've done so far is attempting to change the resolution.

I have the intel 945 chipset and a bunch of resolutions that I cannot use.  I read many successful reports of people fixing their resolution problems, most of which differed in some way.  

Anyway, I logged in as root in order to edit xorg.conf, and yes I made a backup first.  Wierd thing is though, I can get a resolution up to 1280xSomething under root but only 6xx something under my regular username.

Anyway, I proceeded to edit xorg.conf and now I can't get the GUI portion of Ubuntu.  I simply need to rename the backup file from outside it.

Also, more tips on my resolution problem would be appreciated.

Thanks in advance :)

Boot into recovery mode, then you can restore your backup:
```
cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```
After you make the change, press "Esc", I believe that will get you to a login screen.

This thread may help you with your resolution issues:
[http://ubuntuforums.org/showthread.php?t=269052&highlight=915resolution](http://ubuntuforums.org/showthread.php?t=269052&highlight=915resolution)

---

### Post by sad_iq on 2007-07-25
Also read this: [http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

---

### Post by Front187 on 2007-07-25
I've just made my way back into Ubuntu by accessing the tty (I think that's what it is called), and using the mv command to restore my backup file.  

I'm going to read that page you posted now, thanks! :)

Edit:

Awesome, I've just fixed my resolutions using the second method.

sudo apt-get install xserver-xorg-video-intel

Now I'm on to figuring out how to use dual monitors, each with different resolutions. :-X

---

