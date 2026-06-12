---
title: "[SOLVED] removing old versions"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by dpwilson on 2008-04-02
I have a probably rather unique situation.  I have 3 hard drives installed.  I have windows xp, ubuntu 7.04, 7.10 and kubuntu 7.10 installed.  The last installation was kubuntu 7.10 which just went south after an upgrade that didnt work out (which is another ongoing post I have).  When I boot up and get to the boot menu, I have options for all these with Kubuntu 7.10 as the default.   

When 8.04 is released, I would like to remove the others and just have windows and it installed.  If I would format the drives and remove all the older versions, would I still be given the option to boot into windows? Could I use Ubuntu 7.10 to remove the other versions now and still be able to boot up?  Sorry for all the questions, I am pretty new to the whole linux thing.

I dont want to have to reinstall it since it contains a lot of files and the fact that my wife uses it.  Also, its just a pure pain in the butt to go through all that activation crap again.

If anyone could guide me on the best way to do this, it would be appreciated.

Thanks.

---

### Post by bodhi.zazen on 2008-04-02
When it is released, go ahead and boot Ubuntu 8.04.

You can use gparted to manage (delete / resize) your partitions, keeping Windows if you wish. Then install 8.04.

Should be easy.

Here is a link to how-to gparted:

[Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by bumanie on 2008-04-02
If you leave windows intact and use the partitioner to remove all your other linux installations, 8.04 will recognise windows and allow you to choose which OS to boot into. Should work very well. Just a pointer (which you may already know), it is a good idea to make a separate /home, so that if you have to reinstall for some reason, all your saved data will be safe there as you will only have to reinstall to / As above, you could use gparted prior to the nstal of 8.04 to pre-partion your system.

---

### Post by dpwilson on 2008-04-02
> **bumanie said:**
>  Just a pointer (which you may already know), it is a good idea to make a separate /home, so that if you have to reinstall for some reason, all your saved data will be safe there as you will only have to reinstall to / As above, you could use gparted prior to the nstal of 8.04 to pre-partion your system.

Good point.  That I never really knew when I first installed ubuntu or kubuntu and now wish I did.  I will definitely do that in the next install.

Thanks for the advice from everyone.

---

### Post by indytim on 2008-04-02
Since you also have multiple flavors of Ubuntu-Kubuntu etc running, you might want to consider going with a dedicated GRUB partition.  At a minimum, it would keep things cleaner when we go through kernel upgrades.

IndyTim

---

### Post by bodhi.zazen on 2008-04-02
> **indytim said:**
> Since you also have multiple flavors of Ubuntu-Kubuntu etc running, you might want to consider going with a dedicated GRUB partition.  At a minimum, it would keep things cleaner when we go through kernel upgrades.

IndyTim

Not sure if you are referring to a dedicated /boot partition. Be careful with that as nowadays at installation a /boot partition will be re-formatted by most distros at the time of installation.

I wrote a how-to on multibooting using chainloader, you may be interested :

[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

---

### Post by Duck2006 on 2008-04-02
I believe he means to make a boot partition to boot what ever dirso you have on your system, using chainloader to load other dirso, i see there is some one in one of the other forms that uses it to boot 145 OS's on his system.

---

### Post by Duck2006 on 2008-04-02
Some reading on using multibootingt dirso's.

[http://www.justlinux.com/forum/showthread.php?t=143973](http://www.justlinux.com/forum/showthread.php?t=143973)

---

### Post by dpwilson on 2008-04-02
Sorry for the lack of proper nomenclature, I know it doesn't help much when asking for help.  I will definitely check out the links and learn more on this.  

What I want to do is wipe out the older versions and keep Windows and then of course when its released, add 8.04.  I think the bootloader is what I am talking about.  Where upon booting up, it gives you the options as to what OS you want to use.

---

