---
title: "No &quot;Install Alongside Windows&quot; Option on Any Linux Distro"
date: 2013-04-21
forum: Any Other OS
---

### Post by Xatabsco on 2013-04-21
I've been getting this problem and it's been driving me insane, because i've been really wanting to dualboot Windows and Pear OS 7/Netrunner 12.12 Third Edition. I've been wanting to run one or the other, but it won't let me install alongside Windows 7. I only get two options. Erase disk and install or something else. Whenever I try, something else. It just shows my whole hard drive (which is 3 TB in size) but on Disk Management, it shows that I have one partition with 1023 GB unallocated and another partition with 748 GB unallocated and my main partition for Windows is 1024.50 GB, with 100 MB system reserve.

[IMG]http://i36.tinypic.com/o09i8.png[/IMG]

I've tried using Pear OS 7/Netrunner/Elementary OS Luna Beta and Linux Mint.
They all come up with the same thing.
Anybody know any way to fix this? I need Windows for the sole reason of gaming.

Specs if needed:
i5 3570k 3.5GHz Processor
3 TB Seagate Barracuda Harddisk
NVIDIA GeForce GTX 670 (Zotac AMP! Edition)
16 GB DDR3 Ram

Thank you. :)

---

### Post by Perfect Storm on 2013-04-21
Moved to Other OS/Distro Support.

---

### Post by MadmanRB on 2013-04-21
Well it looks like your drive has already been partitioned.
Maybe you can manually install them.
Those two unallocated drive spaces are not recognized by windows so are probably ready for a linux install.

Have you ever manually partioned a drive?
its not all that hard.
That will be the something else category in your installer

---

### Post by Xatabsco on 2013-04-21
It was :)
And as I said before, I had already tried that. But I tried again, for you. ^_^
But just like before, it just shows one whole hard drive and not any other partitions.
Is there any way to make the other partitions visible?

Edit: Is there any way to make the unallocated partitions visible and to also recognize the Windows partition *

---

### Post by MadmanRB on 2013-04-21
The other partitions wont become visible until you check the "something else"
option.
go into that and read me off what comes up in the list of partitions.

---

### Post by Xatabsco on 2013-04-21
That's the option I used, like I said.
It only comes up with one partition, which would be my whole harddrive.
:P

---

### Post by iamkuriouspurpleoranj on 2013-04-21
Download Ubuntu and run it as a live USB/DVD. Use GParted and see what partitions it presents. If those partitions that Windows sees appear in GParted and you know you won't miss them, delete them then go back to your Pear/Netrunner installer and see what you get.

Have you previously had Mageia on there, by any chance?

---

### Post by Xatabsco on 2013-04-21
I am on the Live CD version of Ubuntu 12.04 and here are my results:

[IMG]http://i33.tinypic.com/10hlmba.png[/IMG]

It doesn't recognize Windows 7 or that there's any data on it. :P

---

### Post by iamkuriouspurpleoranj on 2013-04-21
It may not help you but it concerns a drive of a similar size [https://forums.mageia.org/en/viewtopic.php?f=7&t=3269](https://forums.mageia.org/en/viewtopic.php?f=7&t=3269).

---

### Post by Xatabsco on 2013-04-21
That's more to do with extending the hard drive to meet the full 3 TB that is shown since Windows does not allow partitions more than 2 TB's. 
Seagate DiscWizard makes another partition with the rest of the space for me anyways, so yeah, that's not a problem. 
The main problem is that no Linux distros are able to recognize any data on the hard drives. :P

Edit: 
So I decided to install PearOS and delete Windows 7, but I still wanna dual boot with it after, upon installation. I got this error:

[IMG]http://i36.tinypic.com/f13ef.png[/IMG]

I don't know what that means, but I clicked no and it seemed to have worked.
If anyone can teach me how to dual boot with Windows 7 now, that'd be great. :P

---

### Post by monkeybrain2012 on 2013-04-21
Never used "install along Windows", even when I started dual booting Ubuntu 10.04 with Windows I used manual partition (now called "something else" in Ubuntu or "advanced" in some other distros) because I want to have separate / and /home. I have gotten rid of WIndows a while back and dual boot Fedora and Ubuntu, still use "advanced" instead of "install along.."  

Come to think about it, I am not even sure if there is an "Install along" option in Fedora's installer for dual booting with OSes other than Windoze.  it seems that the only option is to erase the other Linux os and install Fedora, so "advanced" install may be the only  option in that scenaro.

---

### Post by kevdog on 2013-04-21
I don't understand the question.  What do you want to install?  and how many partitions do you want?  This sounds like a perfect job for the Gparted Live CD for any distro you want.

---

### Post by UltimateCat on 2013-04-22
[**[COLOR=#000000]Xatabsco[/COLOR]**]("http://ubuntuforums.org/member.php?u=1813131"): Hi: ;)

Shrink your Windows 7 partition- (about 1/2 the size)
[http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html](http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html)

In a previous post I saw that you have:
```
944.64GB Free

```

Take advantage of that free space when your doing your Linux install.
Highlight that free space with the up or down arrows hit enter and work from that free-space to create your Ubuntu partitions--
Manual install is best; I have found **when you want to dual boot--**

When you are prompted by the *Ubuntu* **Partition Manager**: it should show you all partitions on that computer-
Manually create one partition from the free space for your **-** Ubuntu (/) **journaling file system** and allocate about 20GB
Than manually create another partition for the **-** **Swap** space about **2** to **4 GB** (depends on what you want)

When your done creating those partitions you should see something like "finish partitioning and write to disk"
Once you click that your done. The installer should take over; start and finish the rest of the installation and boom: your new distro will be installed--:-

I have never used G-parted; as I prefer to use what the Linux installer provides. 
After doing a few manual install's you'll get the hang of it--

Good luck!

---

### Post by arpanaut on 2013-04-22
Take a look at this thread from post #7 on, 
[http://ubuntuforums.org/showthread.php?t=1619381](http://ubuntuforums.org/showthread.php?t=1619381)  

Looks like the residual GPT signatures are preventing the installers from reading the partition tables correctly.
Some cleanup or decisions on partitioning scheme may be needed. Re: MBR vs. GPT

---

### Post by Xatabsco on 2013-04-26
Thank you so much. Surprisingly that worked.

I'm getting a new error now though.

[IMG]http://i44.tinypic.com/24ci7gg.png[/IMG]

Anybody know why? Did I do something wrong?

---

