---
title: "just getting started"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by Android565 on 2006-07-22
When i first boot from the DVD i get an error with the X server (Failed to start the X server...), i have tried going through the manual config for it but i dont really know if its worked (if it has i havent managed to get from there to the installer)

Have i done the right thing? And how do i get to the installer from the command line after i configure the X server?

---

### Post by taurus on 2006-07-22
Looks like the desktop version is having problem with your video card.  So, you can use the alternate CD to install it since it uses text base.  Just follow the instructions on the screen and once it's finished, see if it can boot into GUI.  Otherwise, you can configure your X with

```

sudo dpkg-reconfigure xserver-xorg

```
p.s.  What is the brand of your video card anyway?

---

### Post by DSn0wMan on 2006-07-22
Are you running off the live cd, or did you install ubuntu on your hard drive?

---

### Post by taurus on 2006-07-22
> **DSn0wMan said:**
> Are you running off the live cd, or did you install ubuntu on your hard drive?

I think he is having problem running off the DVD as in his first sentence!!!

---

### Post by steve.horsley on 2006-07-22
DVD? I don't know of a live DVD, but never mind. I will talk about the live CD since that's all I know. 

If you have X problems, how did you "do a manual config"? Did you manage to get a text prompt and run the command **sudo dpkg-reconfigure xorg-xserver**? IF so, you need to restart X with the command **sudo /etc/init.d/gdm restart**. If you fixed it, you will get the graphical login page. Then after logging in, the installer is an icon on the desktop.

If you can't get the live CD/DVD going, you could try the text-mode installer CD.

**Edit:** Whoops! That should be **sudo dpkg-reconfigure xserver-xorg**

---

### Post by Android565 on 2006-07-22
Yes, after the error i used the command: sudo dpkg-reconfigure xserver-xorg, i will try to restart the X server after that then and see if it works, and i believe its a live DVD (bottom of the downloads page: Ubuntu DVD Releases)

I believe i am currently running from a live DVD but i am attempting to install on my HD (i now have 40GB of free space + a FAT32 partition)

Thanks for all the help

---

### Post by taurus on 2006-07-22
You can configure all you want because the next time you boot from the DVD again, you will have to reconfigure it all over again!  So if you plan to install Dapper on your machine, use the alternate CD so you don't have to boot into LiveCD first before you install it...

---

