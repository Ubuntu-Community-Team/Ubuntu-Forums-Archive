---
title: "Nondestructively resize existing XP partition to make room for Ubuntu?"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Kethinov on 2008-01-29
I'm not exactly new to Linux or Ubuntu, but I've never done anything like this before.

I've got a WinXP laptop that I'd like to dualboot with Ubuntu. There's plenty of room on the hard drive, so ideally I'd like to free up around 35gb of it for Ubuntu and keep my Windows XP installation the way it is - except with less hard drive space formatted as NTFS.

What's the fastest, safest way to do this in Gutsy? Losing my existing XP install is NOT an option. I can't wipe the disk, repartition, and reinstall the operating systems "properly" like I would just normally do.

---

### Post by philinux on 2008-01-29
Backup, backup and backup. While that's going on read the links below/

Clean up the xp disk, defrag twice. 

Use the live cd and boot up, then use the install icon. Use the guided option repartition your xp drive from the live cd as part of the install. Or if your familiar use manual.

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Ex-windows on 2008-01-29
You should be able to use the live cd and go to  System> Admin> Gpartred. This will show you the HDD and any Partitions on it   Then decide how much space for Ubuntu and resize accordingly. I am not sure if you have played with Gparted But it has a cute lil slider bar for resizing .., It is real easy  and Quick  However  I would back up ALL files First Just to be safe. There is a great apge here for more help
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
Good luck

QUICK EDIT: philinux makes a good point .  ( I am a dummy for forgeting this)
You should really clean up xp ie Adware scan, Cookies tif and  windows temp files as well as a virus scan. Then a check disc and defrag

---

### Post by (((X))) on 2008-01-29
GPARTED livecd, it´s able to merge/expand partitions, both Windows, Linux
It´s an iso

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by the_sorrow on 2008-01-29
I recommend you that BACKUP every single date in your Windows partition, Gparted is reliable, but there is always a possibility of losing your data, it is 99 to 1, but it s there.

---

### Post by Kethinov on 2008-01-31
The install went well. Nothing blew up. XP survived. Linux and Windows somehow coexist on this machine. But I'm sad to say dual monitor support is not Ubuntu's strong point these days. Boo.

---

### Post by tenjin1 on 2008-01-31
Dual Monitors work very well in Ubuntu. As with most things in Linux you will need to configure it yourself. Dual Monitors will need to be setup as it's not there by default. Just search the forums for your vid card + Dual Monitors and you will find what you need. Ultimately, you will need to edit your /etc/X11/xorg.conf file to allow for Dual Monitors. 

Good Luck Mate!

---

### Post by Kethinov on 2008-02-05
Yeah, I've done the xorg.conf thing for dual monitors before. It's decent enough for desktops, but it's not a very good solution for me here.

Setting aside the fact that it's pretty sad that in 2008, *nix systems running X11 are the only mainstream desktop OS without competent graphical display config options (something Windows and Macs have had for >10 years), it just wouldn't work for me anyway, since my configuration would need to be dynamic.

The monitor needs to be hotpluggable. If I remove the laptop from the monitor, I want the screen to revert to only using a single display, without restarting X11. AFAIK, X11 can't do this presently. Bulletproof X can't come soon enough.

---

### Post by Ex-windows on 2008-02-05
which graphics card r u using? Nvidia has a cute lil gui to help configure your monitors and works very well on both my Desktops. I have yet to get that far on my laptop though.  It even has a "hotplugable" feature Though I have not tried it since I have no need "Yet"

---

### Post by Kethinov on 2008-02-06
It's an NVidia card, but I don't see that graphical config widget anywhere in Synaptic. What's it called?

---

