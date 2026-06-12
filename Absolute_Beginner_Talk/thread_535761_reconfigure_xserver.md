---
title: "reconfigure xserver?"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by chaddiesel on 2007-08-26
Well, i messed with something i shouldn't have. I had everything working fine except the video was choppy. I decided to run 
```

dpkg-reconfigure xserver-xorg
```

When I was done there was no difference. When I rebooted I don't get a welcome screen. Just a prompt like the terminal. I tried running the same command and it says...

/usr/sbin/dpkg-reconfigure must be run as root

How do I reconfigure the xserver to get it working again?

---

### Post by S15_88 on 2007-08-26
sudo dpkg-reconfigure xserver-xorg   - sudo gives you root priveliges
      or in recovery mode 
dpkg-reconfigure xserver-xorg            - no need for sudo as you are root in recovery mode

---

### Post by Majorix on 2007-08-26
Do you have a backup of xorg.conf? If so you can replace it with the faulty one.

---

### Post by finer recliner on 2007-08-26
to elaborate on s15_88's comment.

putting the command "sudo" infront of any command will execute that command as root. root is the administrator of the computer and has access to everything.

---

### Post by chaddiesel on 2007-08-26
I don't have the back up. I am new to these commands... I knew it would be something simple. Thanks

---

### Post by chaddiesel on 2007-08-26
Well, I went through the process and still have the same problem. I don't know what I can do to fix it.

Any ideas?

---

### Post by chaddiesel on 2007-08-26
it tells me that the markers are

(==) Log file: "var/log/Xorg.0.log"
(==) Using config file: "etc/X11/xorg.conf "

---

### Post by S15_88 on 2007-08-26
just to clear this up you have no GUI, when u turn ur computer on it gives u the "cannot start the X server" error and then puts you to the commad line?  adn you've tried dpkg-reconfigure xserver-xorg...no luck?  tell us what u have in etc/X11 folder by doing:
> 
cd etc/X11
dir


i am currently having the same problem, i've had this problem many times but for some reason this time none of my back up files are working and whenever i do dpkg-reconfigure xserver-xorg i get my log in screen but noooooo desktop!!!! ahhhh!! so frsutrating haha and that concludes my rant!

Thanks, Alain

---

### Post by chaddiesel on 2007-08-26
I finally got it correct. The only thing I changed was my mouse set up. Then it worked fine. I don't understand it fully but I got it to work.

thanks:)

---

### Post by S15_88 on 2007-08-26
be careful editing ur xorg file because the slightest change can screw u over big time!  take a look at this [http://www.deesaster.org/progxorg.php](http://www.deesaster.org/progxorg.php) although this program can still mess things up, personally i've never used it so i'm not recommending it but give it a peak.

---

