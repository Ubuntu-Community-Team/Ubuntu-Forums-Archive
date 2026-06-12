---
title: "Not your average idiot!"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by online14230 on 2006-10-05
Hello.
Seems I REALLY have a knack for breaking things...
This time, the victim was Wine. :)
OK. Lemme go through the problems 1 at a time.
My current situation goes like so: I have Dapper installed on a Dell Optiplex GX150, 20GB HDD (because Im saving the big HDD for my mp3 library), 326MB SDRAM (Dont ask, sdram is expensive. the machine came with 256, I had 64), blah blah blah... 
Anyways, heres the problem: I dont have gparted. I would like to resize the drive as it is currently partitioned in 2 : / and /swap. I want to reduce the root partition to 10GB and use the rest for data storage (My wife wants somewhere to keep those damn recipes, dont ask!). 
1. Can it be done?
2. How? I know that ./parted can do it, but Im not too funky at the command line. Also, it says I shouldnt forget to edit the fstab . Can someone please elaborate?
3. Dependencies: Since this Ububox doesnt have netaccess, how would one install additional software? I tried installing wine at the commandline.  you should see the mess. Anyway, Ive since discovered that package installer thing that checks for dependencies. It gave 1 depend for wine. I downloaded it. The depend gave another depend. Eventually, I had a list of depends so long ... AAAARRRRRRGGGGHHHHH! I dont want to reinstall dapper. See the last time I installed a package from the command line, it was broken. So synaptic proceeded to remove it. and a LOT of other stuff. THATS why startx ewasnt working: There was nothing to start!!! Synaptic removed EVERYTHING except the kernel and bash :) Yes, it was funny. I dont want that to happen again, so is there ANY way I could get the repositories recorded onto disc? Its just an idea, but it would save me a LOT of hassle. If I did though, I would need the backports too, because most of the GOOD stuff is there... There IS a freedom toaster in town but Im wondering how long it would take to get the repositories :(. How big are they anyway???

4. A friend is trying to install Dapper on her machine. She cant change resolution beyond 480 x 600, hence she cant install...duh.
Someone replied to the mailing list saying she should press CTRL ALT "+" or "-" (on the number pad) to cycle through the available resolutions. If this doesnt work, is there anything else she can do?
Thanks many times.

---

### Post by Crooksey on 2006-10-05
For your probelm, learn the command line, it helps.

Get your friend to install in safe graphics mode.

---

### Post by dmizer on 2006-10-05
i assume you do have at least one machine that has internet access.

download knoppix and burn it to a cd:
[http://www.knoppix.com](http://www.knoppix.com)

boot to it on cd (live cd) instead of booting to ubuntu on your hard drive.  knoppix has qparted and will be able to resize your partition.

alternatively, you can use the ubuntu live cd for the same purpose.  it has gparted.

as far as dependencies are concerned ... surely you can come up with SOME way to get the box online? ;)  otherwise, i know there are howto's around (maybe in the wiki) for getting the repos' to cd or dvd.

---

### Post by bigken on 2006-10-05
The simplest way is to download [gparted]("http://gparted.sourceforge.net/livecd.php") liveCD

---

### Post by risbac on 2006-10-05
If you installed Dapper, you must have the CD, right? If it's the basic one, it's a liveCD, including Gparted. That's how to change my partitions. 

THen to install softwares without internet, it's complicated. You can't have all the packages on the CD. But then there is DVD version I think, maybe there are much more packages there?

---

### Post by petri on 2006-10-05
1. Yes, it can be done. You have to defragment ntfs first untill there is no fragments left. You have to leave room ntfs + 20%. If the ntfs partition is 8GB >> 8GB + 20% = 9,6GB to windows work properly. Any wife can use openoffice writer to play with their recipies, just use some theme which changes to blue adressbar at the top. ;)

2. [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)

3. No desktop left? ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```
Don't treat yourself like this, get internetacces to your ubuntu. 8) It's the only OS with a secure internet connection and required on installation.

4. She needs graphics drivers to her videocard. Tell her to write ```
lspci
``` in Terminal, there she will find what videocard she has and then make a **Search** at ubuntforums.org about: **howto install *****



EDIT: Next time do use an informative title, please.

---

### Post by online14230 on 2006-10-05
replies replies!!!
Thanks to all!!!
OK: 
DMizer: I looked for howtos. None around here dealing specifically with Ububoxes without net access. The only way I can get the box online is via dialup. Have you ANY idea what that will cost me? In that case, its cheaper to buy a new system, with Windows Pre-installed (but is windows worth it?)If I could download Knoppix, Id download the repositories... :)
Petri: Nice to see ya without your dish! (Sorry, I just couldnt resist. That WAS a joke... ) Thanks, and sorry about the title. Its just that Ive broken Ubuntu via gnome, then wine, 2 days in a row. Youve gotta be a super idiot to get THAT right. AnND then still watch Synaptic uninstall your system ... THAT was the funniest thing Ive seen in a while. Almost as funny as Windows 98! Now, thanks for the howto-fix-broken-gnome. My wife WANTS Word 2003 installed. Im gonna try using the "Right" icons in openoffice :)

Thanks for the help. Now all I need to know is what the fstab has to be edited for...

---

### Post by petri on 2006-10-05
fstab? It depends what you have done. Paste these three in terminal and paste the output here. ```
sudo fdisk -l
```
```
gedit /boot/grub/menu.lst
```
 ```
gedit /etc/fstab
```

EDIT: Use Code button (#) when you paste the long ones.

---

