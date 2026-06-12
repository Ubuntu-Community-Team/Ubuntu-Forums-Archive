---
title: "how to use ubuntu as a live cd?"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by narayanwaraich on 2008-04-12
I had requested for an ubuntu cd from ubuntu team.It was shipped to me in two weeks.Now the problem is i am completely new to linux and ubuntu but it is important to me as i am an engineering student.What i want to do is that use the cd as live cd without destroying windows xp installed on my laptop.I can afford to install it on a partitioned drive(**Is it possible to use two two OS from same computer?**)Plz help me and give me step by step instructions for using it.:confused:


Thanx you all guys ....I have successfully used this cd as live cd....infact I am writing this post from ubuntu.....It's really amazing....now i want to know how to install it...as designwiz told me there was no screen to install ubuntu rather after clicking"start or install ubuntu"it started ubuntu as live cd....but there is an icon on the desktop of the name"install"...do i have click on it to install ubuntu on a partiotioned drive....Thanx again to you all:)

---

### Post by sharks on 2008-04-12
First go to your BIOS and select the cdrom for boot. Then insert the CD and select install or install from safe graphics mode. Then you can use it as a live cd.

---

### Post by sharks on 2008-04-12
Yes it is possible to use 2 OS.Then install Ubuntu and u can the OS installed in the GRUB menu at the boot up. The installation is so simple.

---

### Post by SunnyRabbiera on 2008-04-12
well ubuntu should run as a live by default...
unless you have something in your bios blocking booting from CD drives

---

### Post by Master Yami on 2008-04-12
The install is simple, and usually risk-free. If you want your hand held through it, there are many, many tutorials on the net. Google it and the answers will flow. The live cd doesn't touch you computer at all either, so play with it as long as you want.

Its easy, and once you start using Linux you will love it.

---

### Post by Mick8882003 on 2008-04-12
Yes if you like it then think about a dual boot.

---

### Post by designwiz on 2008-04-12
Yes you can have two or more OS installed on a same computer, its known as dual booting. Heres a step by step guide as to how to dual boot. I presume win XP must be installed on C:/ you may choose to install Ubuntu or any other drive except for C:/ by mking sure its partioned as ext3.. Dnt worry its just as simple as a piece of cake.. So Lets start

**Install Ubuntu**
Boot the XP machine from the Live CD and select "Start or install Ubuntu".
[IMG]http://apcmag.com/system/files/images/vista_ubuntu_05.article-width.jpg[/IMG]

Once the Live CD has loaded, double-click the Install icon on the desktop to start the installation process.
On the Welcome screen, choose your language and select Forward.
[IMG]http://apcmag.com/system/files/images/vista_ubuntu_06.article-width.jpg[/IMG]

On the "Where are you" (timezone) page, select your location and then Forward.

Select appropriate time zone


On the next screen, choose the appropriate keyboard layout and then Forward.

[IMG]http://apcmag.com/system/files/images/vista_ubuntu_08.article-width.jpg[/IMG]

Now Ubuntu loads the disk partitioner. The first option, to resize the main partition and use the freed space, is pretty much the best one to go with. 

[IMG]http://apcmag.com/system/files/images/xp_ubuntu_07.article-width.jpg[/IMG]

The default recommendation for the new partition size is optimal, but you can move the slider up and down to change it as you see fit. If you&#8217;re feeling brave, you can also manually edit the partition table, but unless you&#8217;re really confident about what you're doing, this isn&#8217;t recommended.

Click Forward to continue.

Ubuntu now has enough information to install, so click Install and go make a coffee.

When the install is complete the system will reboot. When the GRUB boot menu is displayed, have a look at the last entry in the list. 

After the Ubuntu boot options, there will be an entry &#8220;Other operating systems&#8221; and beneath that &#8220;Microsoft Windows XP Professional&#8221; (or Home, whichever version you&#8217;re using). By default Ubuntu will load itself after 10 seconds. 

[IMG]http://apcmag.com/system/files/images/xp_ubuntu_09.article-width.jpg[/IMG]

If you choose to boot Windows XP at this point, it will probably launch a check on its partition. This is because the partition has been resized since last boot, and it will want to run a consistency check to make sure there are no problems. 

When XP loads, it will also probably detect new hardware (again, the resized partition) and will prompt to reboot. 

[IMG]http://apcmag.com/system/files/images/xp_ubuntu_10.article-width.jpg[/IMG]

**Dualboot - Reboot XP **

On reboot it will probably run through another, longer consistency check and then reboot. This is the last time you&#8217;ll need to do this. 


Thats about it and you can now have WIN XP and Ubuntu running together. 

I found this tut on pcmag site.. Hpe it helped. 
Cheers \\//

---

### Post by Mick8882003 on 2008-04-12
See my sig for a short guide to running the live cd.

---

### Post by sharks on 2008-04-12
If your system is running slow in Start or install ubuntu in live cd , select Start Ubuntu **in Safe graphics mode**

---

### Post by narayanwaraich on 2008-04-12
I found this tut on pcmag site.. Hpe it helped. 
Cheers \\//


Thanx buddy this was really a complete guide and i hope it helps.......let me give it a try...

---

### Post by Mick8882003 on 2008-04-12
I hope you relise thats a tutorial for installing ubuntu, not running the live cd

---

