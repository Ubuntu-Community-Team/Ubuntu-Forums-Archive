---
title: "Do you recommend VMware?"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by milad on 2006-12-22
I have seen a HOWTO on installing Windows XP virtually in Ubuntu using VMware. I just wanna know if you actually recommend it or should I stick to my Dual boot?
What are the cons and pros?

I know it's not that fast, but I don't use my windows for gaming or heavy graphical jobs, I just need some small programs which I haven't been able to make them run in Ubutnu using Wine.

---

### Post by insane_alien on 2006-12-22
dual booting is probably best. Virtulisation is mainly for developers i think so they can test on multiple platforms or something.

---

### Post by dbbolton on 2006-12-22
i personally just dual boot. i really only use xp for multimedia production.

---

### Post by xopher on 2006-12-22
I use vmware for apps I need and aren't available in ubuntu/linux.

XP is reasonably fast, near native speed actually. When in full screen mode it's hard to tell the difference ;)

Games, of course, do not work. So this would only give you the vast array of applications that are only supported on windows.. I use it as a last resort if all else fails :)

I recommend you try it out, and see for yourself, the best opinion to rely on is your own.

---

### Post by userundefine on 2006-12-22
I definitely say use VMWare.  Dualbooting can really be the pits, and I disagree that virtualization is only for developers -- it's going mainstream very quickly.  Put it to you this way: would you rather work in windows in an environment you know is safe and secure (Linux) and only use Windows for programs you absolutely *can't* find a usable equivalent for in Linux, or would you rather reboot your Ubuntu every time you have to use X program into a full Windows environment and have to set up a firewall, antivirus, antispyware, antimalware, etc etc?  What if that installation gets hosed--you'll have to reinstall Windows.  With VMWare, you can just take "snapshots" of your Windows installation at any given time, and backup that snapshot whenever you want.  Takes mere seconds really.  Virtualization is awesome, and it isn't just for devs anymore, IMO.

---

### Post by PilotJLR on 2006-12-22
Depends on how much RAM you have, and processor speed. With a recent CPU (past couple years) and enough RAM, XP in VMware is great.
I have 2 GB of RAM, and I routinely use Quicken and some Windows-only tasks in VMware. It runs very well... provided you are not playing games with it. Anything that requires hardware video accelerate would not work well.

Overall I recommend VMware Server very much!

---

### Post by raul_ on 2006-12-22
Yeap. VMware runs just like the real deal =) and you don't need to spend time rebooting

---

### Post by anaconda on 2006-12-22
I recommend it! VMWare runs everything I need from windows and it works very well.

An added bonus is that the "hardware" always remains the same, so no reactivations etc.. even if you copy the image to a new computer..

---

### Post by MrKlean on 2006-12-22
You can run just fine under VMware...until you realize you don't need Windows anymore LOL!  I found everything for my business under Ubuntu and ditched Windows for ever ; )   Look and yee shall find ; )  It may take work...but you'll learn along the way !!

---

### Post by milad on 2006-12-22
thanks for your replies, I think I'll give it a try.
I've got an AMD 3600 with 1GB RAM. I don't know if it's enough or not.

And what about hardware support? Will I be able to use my printer or my flash drive in Virtual Windows?

---

### Post by MrKlean on 2006-12-22
yep..but you'll have to enable USB support in the VM machine ..there's only 2 slots available...

---

### Post by PilotJLR on 2006-12-22
> **milad said:**
> thanks for your replies, I think I'll give it a try.
I've got an AMD 3600 with 1GB RAM. I don't know if it's enough or not.

And what about hardware support? Will I be able to use my printer or my flash drive in Virtual Windows?

I have found it is simpler to enable network printing from your ubuntu machine, and then setup the printer as an IPP printer in XP in VMware.
But yes, you can attach USB devices.

---

### Post by MrKlean on 2006-12-22
I only have 512 and it works fine.  The USB will work...but after you setup your VM.. you'll have to enable it under VM .

---

### Post by dbqp on 2006-12-22
> I definitely say use VMWare. Dualbooting can really be the pits, and I disagree that virtualization is only for developers -- it's going mainstream very quickly. 

I completely agree. Dual booting has led me to some corruption on my hard disk going back into Windows. And when you are in Ubuntu and you need to do something in XP, W2K, Win98, Win95...you just launch the VM Ware Server Console.  No more dual-booting.

Like others have said, you do need the processing power and RAM, but from your recent post, you definitely are good to go!

Just remember, if your wireless card doesn't work in Ubuntu - you won't be able to get it working in a VM Ware XP.  VM Ware only passes along to the virtual machines what the native OS has available.

It's a great tool!

:D

---

### Post by tiddy on 2006-12-22
Yes I recommend it, it is brilliant (on SUSE anyway -- I'm getting Ubuntu in a couple of weeks) I have a 2.4GHz processor (single) and when I had it I had 1280MB RAM (now only 1024MB) and I could hardly tell the difference. I found the USB stuff a bit complicated and I was feeling tired so I set it up as a samba share on the host and mapped a network drive in XP to the share on the host and it worked very well with M$ Visual C#.

---

### Post by SurferJoe on 2006-12-22
I know where you are coming from - I tried Ubuntu about 12 months ago ( I think! ) and found about 60% of the software I NEEDED to use , could be found with Linux alternatives , but it wasn't enough.
Downloaded and installed as a dual boot with XP the new 6.1 Edgy Ubuntu and found almost all of my requirements have been met.
Right now , I am doing data backups so I can do a full install across my system on 600GB of storage. Then I will set up VMWare and install the programs I haven't found alternatives for YET.
However I think it will only be a short term measure - I expect that with time I will find all the relevant software I need to run and can then ditch VMWare and Windows.


Good luck and most of all have fun!

---

### Post by mangurian on 2006-12-22
I use ubuntu running under the free VMPlayer.

Mostly for visiting potentially unsafe web sites.
There is no danger of getting a virus or malware.

I would like to try Xubuntu, but I have only found the virtualized version as a torrent and when I try to download it, there seem to be only a few (and slow) seeders.   It would take weeks to download.  If anyone knows where I can ftp or http it please let me know.


thanks,

---

### Post by raul_ on 2006-12-22
[http://www.xubuntu.org/get]("http://www.xubuntu.org/get")

---

### Post by BarfBag on 2006-12-22
I'm dual booted, but if the apps I need weren't so heavy, I'd switch to a virtual machine.

VMware is definitely the best virtualization software.  I remember running it back in the day when I had 512 MB of RAM (now I have 1 GB).  It was pretty snappy.

Before I switched to Linux, I also used and liked Microsoft Virtual PC.  To this day, I still prefer the interface to VMware.  Problem is - it was SLOW AS HELL!

---

### Post by milad on 2006-12-23
Ok, I installed VMware last night and it really looks perfect. I only have one question left, is there any easy way to move a file from my Virtual windows to ubuntu?

For example, I prefet to use uTorrent in windows instead of Azureus, but how should I use the downloaded file in Ubuntu?

---

### Post by milad on 2006-12-23
no one?

---

### Post by raul_ on 2006-12-23
[http://www.faqts.com/knowledge_base/view.phtml/aid/23667]("http://www.faqts.com/knowledge_base/view.phtml/aid/23667")

---

### Post by Dr. C on 2006-12-23
> **milad said:**
> Ok, I installed VMware last night and it really looks perfect. I only have one question left, is there any easy way to move a file from my Virtual windows to ubuntu?

For example, I prefet to use uTorrent in windows instead of Azureus, but how should I use the downloaded file in Ubuntu?

I have Samba installed on Ubuntu. The Windows VM then becomes a networked Windows computer and can transfer files etc.

---

### Post by Doug11 on 2006-12-23
I have an AMD also with 764 mb of RAM and have no probs what soever. I ony dual booted long enough to get a good feel for Ubuntu, then i ditched windows and went full ubuntu with mv ware.

---

### Post by milad on 2006-12-24
Where can I find out more about this Samba thing?
Sorry, I'm a real newbie

---

### Post by milad on 2006-12-24
There is something funny about this vmware, although I have installed it and it works perfectly, but occasionally when i try to run it, nothing happens. when i try terminal, i get :

vmilad@milad-desktop:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

and when I re-configure it, accepting all default options it starts to work again.
Does anybody know what's wrong with it?

---

### Post by spockrock on 2006-12-24
I have gotten that before, I think it happened when I updated the kernel.....

---

### Post by Zimmer on 2006-12-24
> **milad said:**
> There is something funny about this vmware, although I have installed it and it works perfectly, but occasionally when i try to run it, nothing happens. when i try terminal, i get :

vmilad@milad-desktop:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

and when I re-configure it, accepting all default options it starts to work again.
Does anybody know what's wrong with it?

Have a look at this thread for a potential solution (I was scanning for VMWare and found this thread and the one in the link :) )
[http://ubuntuforums.org/showthread.php?t=323661](http://ubuntuforums.org/showthread.php?t=323661)

---

### Post by milad on 2006-12-26
Tx man, it worked! I guess my next issue is going to be Samba.

Tx again!

---

### Post by Zimmer on 2006-12-26
> **milad said:**
> Tx man, it worked! I guess my next issue is going to be Samba.

Tx again!

[http://ubuntuforums.org/showthread.php?t=10895](http://ubuntuforums.org/showthread.php?t=10895)

May help, somewhere from post #5 onwards.. :)  depending on your problems...

---

