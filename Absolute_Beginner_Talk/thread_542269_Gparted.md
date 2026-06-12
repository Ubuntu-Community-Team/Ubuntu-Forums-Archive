---
title: "Gparted"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by D_2 on 2007-09-03
I am dual booting with WinXP and Ubuntu. When I installed Ubuntu I gave it WAY more HDD space than I wanted to. So I went and got gparted and launched it and it has a lock by all of the partitions. So I closed gparted down, went to a terminal screen did sudo gparted put in my password and still locks by the partitions. I then rebooted my system with the Ubuntu 7.04 disk in the CD ROM drive and went to Gparted and no locks by the partition so I thought good, things might be looking up now. Well I told it to resize the linux partition and gparted came back saying there is something wrong with the disk. Go fix the problems and come back. Well ok fine, where is that program to have it check the HDD for problems. I know in windows I can just tell it chkdsk c: then have a message come back saying it will do that when I reboot the system.

So for Linux/Ubuntu what is a program for me to have it check the linux partitions or even better have it check all of the partitions, the NTFS and the ones Ubuntu created so it can get fixed and I can go back to the live CD and rerun gparted

---

### Post by taurus on 2007-09-03
GParted LiveCD works better since it comes with the latest version of gparted.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

And the command you are talking about is fsck.

```
sudo fsck /dev/sda1
```
If your Ubuntu is on /dev/sda1.

---

### Post by pizzutz on 2007-09-03
fsck

type 

man fsck 

for details

---

### Post by D_2 on 2007-09-03
Ok I did that and now I will go and try to re-run gparted from the live cd
I thought about getting the gparted live cd but if that is the only thing on there and no other utilities like the fsck program or something stronger, why waste the CD for one small program, or does the version that is on the Ubuntu live CD have bugs in it and not as stable

One other question that I was trying to find the answer to. Because I am dual booting, when the I think its call the GRUB loader or the one that comes up asking what OS comes up, the timer is only set for 3 seconds and it is starting to load Ubuntu before my screen is ready. How can I extend that time form 3 seconds to say 10 to give my screen more time to catch up. So far I have just been hitting the down arrow on the keyboard to get the timer to stop and I have more of a chance to pick what OS I am wanting, but I forget about the 3 seconds to choose and before I know it I am going into Ubuntu when I was wanting to go to XP

---

### Post by Duck2006 on 2007-09-03
I have a gparted + super grub +puppy linux all on the same CD. You run the live CD and then chose witch one you need to run, to do repaire the system. Forget where i got the project page from but it may be worth googleing for it.

---

### Post by antoz on 2007-09-03
One other question that I was trying to find the answer to. Because I am dual booting, when the I think its call the GRUB loader or the one that comes up asking what OS comes up, the timer is only set for 3 seconds and it is starting to load Ubuntu before my screen is ready. How can I extend that time form 3 seconds to say 10 to give my screen more time to catch up. So far I have just been hitting the down arrow on the keyboard to get the timer to stop and I have more of a chance to pick what OS I am wanting, but I forget about the 3 seconds to choose and before I know it I am going into Ubuntu when I was wanting to go to XP[/QUOTE]

**You need to edit your menu lst and change the time to what ever you want**

---

### Post by Duck2006 on 2007-09-03
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Build_a_Super_Grub_DiskGParted](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Build_a_Super_Grub_DiskGParted)

---

### Post by D_2 on 2007-09-03
> **antoz said:**
> 
 
**You need to edit your menu lst and change the time to what ever you want**
 
Sorry for having to ask this noob question. But where is this menu located and I am guessing I can just nano it and find it in there. What would the line look like.

---

### Post by D_2 on 2007-09-03
Ok I broke down and got the live CD for Gparted and it doesn't like my video card. When I do lspci it says my viedo card is VGA compatable controller: nVidea Corporation NV18 [GeForce4 MX 400 AGP 8X] (rev a2)
 
So I thougt ok cool I can go to /bin and run Forcevideo and tell it to run VGA at 1024x768 (that is what I have Windwos and Ubuntu running at) Gparted came back with (EE) VGA(0): Driver can't support depth 24
Then lower it says
Fatal server error:
no screens found
 
so now I am going HUH whats up with this basic program just use some very generic driver, get me some xwindow system screen so I can repartition this thing. Not sure why this has to be this hard to get it done. But I guess its going to be tonights project to get this done.

---

### Post by uglykigjoe on 2007-09-03
:razz:Refer that `herman zone` guide as suggested by the above msg.
It helped me for my vista-ubuntu dual boot.
it should hlp you with your xp too :)


:razz:

---

### Post by antoz on 2007-09-04
> **D_2 said:**
> Sorry for having to ask this noob question. But where is this menu located and I am guessing I can just nano it and find it in there. What would the line look like.

sudo gedit /boot/grub/menu.lst

Just paste the above command into a terminal and change the timeout

---

### Post by mlentink on 2007-09-04
> **antoz said:**
> ```
sudo gedit /boot/grub/menu.lst
```

Just paste the above command into a terminal and change the default time

I might add that you can also change the default OS to be started. So If you want to start Windows as default, you could change the appropriate number to the number Windows is listed. Rememeber that the first one listed is "0", not "1"!

---

