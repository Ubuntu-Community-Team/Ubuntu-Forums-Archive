---
title: "Dual-Boot Ubuntu Instalation problems"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Cairna on 2007-01-12
As some of you know, I've been trying to set up a windows XP / Ubuntu 6.06 Dual-Boot. So today I managed to get partition magic working with my computer ( many scans had to be done, thanks lonewlf ).

But I've run into problems.

I created the linux partition this way: An ext2 ( 31.72 GB ) it's flags are: boot

Swap: linux-swap ( 1004.07 MB ) No flags, no used space

So when I run the Ubuntu instaler after booting up this partition it brings up it's partition manager and I'm not quite sure if I set up the partitions wrong initially or what...

Completely clueless as to what I should do...


P.S. Windows Partition flags are set as "hidden", that bad?

P.S.S. Do most wireless card makers have drivers that support linux? How should I set it up for an internet connection?

---

### Post by jas0 on 2007-01-12
First things first. When you install ubuntu you need to make 2 partitions (minimum): 1 for your swap file and the other for /. 

It looks like you only setup a /boot partition. This partition of only used to house your kernel and not the OS itself. If you install everything on /, then /boot will be installed as part of the process.

Also, it's a good idea to use ext3 as a file system. It's harder to mess it up :)

Let me know if I assumed something wrong.

---

### Post by Cairna on 2007-01-12
Alright, gotcha. Gonna give this a try!

---

### Post by Cairna on 2007-01-12
I can't seem to edit my own post ( connection problems today ) 

I forgot, but how should I set up my internet connection with Ubuntu? I have a wireless G PCI Adapter and a Wireless G router.

---

### Post by mongooseman1128 on 2007-01-12
for wireless just use windows to go to the manufacturers web site and there should be a downloads page, locate your product and if they have a wireless driver then download it and install it (you have to boot ubuntu to install, of course) if there is no driver on the web site, you can always google the card and add on "linux drivers"

---

### Post by jas0 on 2007-01-12
Once you have everything installed, open a Terminal window and type the following:

```
sudo gedit /etc/apt/sources.list
```

Delete the "#" in front of all the URLS and save.

```
sudo apt-get update
sudo apt-get install network-manager-gnome
sudo reboot
```

After you reboot, you will notice a new icon in your task bar. Right click the icon, click on your wireless network and enter the authentication information.

---

### Post by Cairna on 2007-01-12
I seem to have made a massive error during the partitionning and installation, I set for it to reformat the swap partition and then ext2 partition that it was intended to be installed upon, but now when I go into my windows partition, select windows XP home edition it can't start it up because it is missing two essential files.

All my windows files have been transferred to Ubuntu which I wasn't aware of, I believe I have a backup somewhere but it may have been trashed...

Even my Presario Backup folder is on the Ubuntu Desktop.

Any ideas to get me out of my situation and to what I may have done wrong?

---

### Post by jas0 on 2007-01-12
I've seen this happen after using partition magic. I'm assuming that the reason that you're seeing your windows folders in ubuntu is because they get automounted. They're still on the Windows partition, but you can also access them within ubuntu.

What's the error message you're presented with when you try to start Windows?

Try browsing through your Windows stuff in ubuntu. If you're able to do that then you have nothing to worry about file-losing-wise :)

---

### Post by Cairna on 2007-01-12
When I try and start windows it brings up a blue screen saying 


"xmnt2000 ( or 2002 ) not found - Autocheck not starting
autochk not found- Autocheck not starting


It then restarts.

So, I have no Windows XP install disk. So any idea of a way for me to set up both Ubuntu and Windows into working condition again?

---

### Post by ashokraja on 2007-01-12
Hey buddy if u are not able to connect to the internet throught your wlan than check for your driver .... The problem is that your card is been dectected and it has no appropeiate driver for it if you could say your wireless card chipset it is possible for me to give sugessions regarding this problem .

To see your wireless card chipset give
$ lspci

or 

$ lsusb

You can find your chipset there ...
if you dont know where to find post your output of those two command here lets analysis it and get a solution for your problem ..

---

### Post by jas0 on 2007-01-12
Well, now I know for sure that partition magic was the culprit. Don't worry, this is not very hard to fix.

Here's the solution:
[http://service1.symantec.com/SUPPORT/powerquest.nsf/56d21993ad4e6baa88256e91005066ad/b0316214f90fadd888256e9f00607ba5?OpenDocument&prod=PartitionMagic&ver=8.0&src=sg&pcode=pmagic&svy=&csm=no]("http://service1.symantec.com/SUPPORT/powerquest.nsf/56d21993ad4e6baa88256e91005066ad/b0316214f90fadd888256e9f00607ba5?OpenDocument&prod=PartitionMagic&ver=8.0&src=sg&pcode=pmagic&svy=&csm=no")

Try doing that in safe mode if you can. If you can't, you're doing to have to use the recovery console in order to merge that registry file.

---

### Post by Cairna on 2007-01-12
Unfortunetely I can't use that, I can't even get to desktop. Ubuntu is the only OS that loads.

When I go to Windows XP Home Edition  it just shows the windows loading screen, then the error and ( I see the the error screen for about 2 seconds, had to let it reboot itself 3 times to get it all down ) then the computer reboots.

When I try to use The Recovery option after going to windows XP ( which leads me to a screen where I choose Home Edition or Recovery ) it just shows up with a blank screen.


Well, the bad news is I don't know what to do, the good news is that the files are at least still in Ubuntu so it's not hopeless :}

At this point I'm really at a loss for a course of action. Is there any way I could re-mount the C: and D: files ( Main System files and Recovery Folder ) to my Windows? Right now I'm stuck without internet access and without most programs that I'm used to, not even sure how to use the CD Creator.

---

### Post by Cairna on 2007-01-12
I now understand what you meant after searching through the forums a good bit, lots of people had this problem. Apparently though I can't start windows in any safe mode, be it regular safe mode, safe mode with networking or not.

I'm currently just researching other possibilites.

---

### Post by jas0 on 2007-01-12
The easiest thing (for you) to do would be to put your Windows CD in and run a repair on your installation. Once you have it working, back up your important stuff and re-install Ubuntu.

---

