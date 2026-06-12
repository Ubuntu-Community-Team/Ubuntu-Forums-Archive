---
title: "Recovery mode with yaboot?"
date: 2010-05-18
forum: Apple Hardware Users
---

### Post by Iren007 on 2010-05-18
I'm running 9.04 on a Powerbook G4 and, long story short, I accidentially put it into hibernate mode. When I try to turn it on, I am greeted with a blank screen after the bootloader. Unfortunately I can find no way to get out of this, since I'm using yaboot instead of grub. I can access my yaboot.conf file if I mount the HD from a live CD, but is there something I can put in there to tell it not to try to resume from hibernation? Or would deleting the swap partition at hda4 that apparently contains my hibernation data solve the problem? Thanks for any suggestions.

---

### Post by linuxopjemac on 2010-05-19
Cannot you just force to turn it off ? Just press the turn on/off button for about 5 seconds. Sometimes resetting PRAM works too. After boot boing you press Option+Command+p+r

---

### Post by Iren007 on 2010-05-19
> **linuxopjemac said:**
> Cannot you just force to turn it off 

I can, but it still tries to return from hibernation the next time I start it up. Apparently I can append "no_console_suspend" to the boot parameters on the yaboot.conf file on my boot partition...but I can only mount it as read-only for some reason with an 8.10 Live CD.

---

### Post by linuxopjemac on 2010-05-20
If you chroot into the system as root from the liveCD you have to be able to change yaboot.
[http://mac.linux.be/content/chroot-system-livecd](http://mac.linux.be/content/chroot-system-livecd)

---

### Post by oswaldkelso on 2010-05-20
opps wrong thread!

---

### Post by Iren007 on 2010-05-22
I can change the file at /etc/yaboot.conf on my Ubuntu partition fine but I think the file that needs to be changed is on a separate partition at /dev/hda2 that just has three files: offboot.b, yaboot, and yaboot.conf. I can mount this partition fine, there's just no way to edit anything in it.

---

### Post by Iren007 on 2010-05-22
fdisk tells me it's a small partition of type Apple_Bootstrap.

---

### Post by linuxopjemac on 2010-05-23
After editing a yaboot.conf file, you should also not forget to write it into the bootloader with:

```
sudo ybin -v
```

---

### Post by Iren007 on 2010-05-24
You, my friend, are a hero. Using ybin worked perfectly, and as a bonus I was able to remove the "quiet splash" boot parameters which solved my problems with the splash screen -- and I can actually use hibernate mode! Thanks for the tip!

---

