---
title: "ISO File"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by Keithod on 2006-09-30
Hi Im trying to install ubuntu-linux on my PC but I am coming across a problem...

I have downloaded Ubuntu.
I put it on a CD [the ISO file].
I start my computer with it set to boot first from my CD drive.
But it doesnt load, instead the Windows screen comes up...

I have also tried setting the disc to be of a boot up type but that just brings up the MS-DOS screen upon bootup!

Anyone able to help?

Also, is there anyone who can tell me how to partition my C drive without deleting windows and all my files etc?? Any free software to do it???

Thanks to anyone who can help! :-)

Keith.

---

### Post by Rui Pais on 2006-09-30
> **Keithod said:**
> Hi Im trying to install ubuntu-linux on my PC but I am coming across a problem...

I have downloaded Ubuntu.
I put it on a CD [the ISO file].
I start my computer with it set to boot first from my CD drive.
But it doesnt load, instead the Windows screen comes up...

I have also tried setting the disc to be of a boot up type but that just brings up the MS-DOS screen upon bootup!

How do you "put it on a CD"? 
you need to burn it as an cd image, not as a file.
Check you cd-record software options.

> 
Also, is there anyone who can tell me how to partition my C drive without deleting windows and all my files etc?? Any free software to do it???

Thanks to anyone who can help! :-)

Keith.

after boot from the cd you have an app on it called gparted that will do that. It's part of the installer anyway so you will have the opportunity to shrink your c: on the install process.

---

### Post by Ziox on 2006-09-30
> **Keithod said:**
> Hi Im trying to install ubuntu-linux on my PC but I am coming across a problem...

I have downloaded Ubuntu.
I put it on a CD [the ISO file].
I start my computer with it set to boot first from my CD drive.
But it doesnt load, instead the Windows screen comes up...

I have also tried setting the disc to be of a boot up type but that just brings up the MS-DOS screen upon bootup!

Anyone able to help?

Also, is there anyone who can tell me how to partition my C drive without deleting windows and all my files etc?? Any free software to do it???

Thanks to anyone who can help! :-)

Keith.

first thing first, you need to burn that ISO file to the CD, you can't just drag and drop the ISO to the CD.  To burn an ISO, you need an application like [DeepBurner]("http://www.deepburner.com/?r=download"). And here's the guide on how to burn an ISO using deepburner: [http://www.deepburner.com/help_files/html/deepburner_free/](http://www.deepburner.com/help_files/html/deepburner_free/)

After you are able to boot from that CD, then we can talk about partitioning (which is a piece of cake) :p

---

### Post by Keithod on 2006-09-30
Ah brilliant - yous lads/lasses are great! I will try that and let you know when i get to the point where i need help partioning etc...

Talk to you later, again thanks, great help!

Even Microsoft support doesnt be that clear haha

---

### Post by Keithod on 2006-09-30
Well as yous probably guessed - it worked!!! (insert woo hoo here!) Thank you very very much!

Can you help me now to install it as a partition on my C drive? Please*

I noticed that when I used it from CD it had an option to "install" on the desktop so I presume I will be using that??

Ubuntu = Free = Cool = Reliable, thats 3 things MS isnt!

---

### Post by xpod on 2006-09-30
Might be a good idea to defrag windows a couple o times while you wait on these good folks guiding you along:D

---

### Post by David Corrales on 2006-09-30
Like xpod said, start defragmenting since you'll need to resize your current partition.
Once you've done it, install the system using that installer program you saw on the desktop. When it comes to partitioning, I'd say, start with 10gb for Ubuntu.
Resize your current Windows partition (ntfs or fat32) to allow for 10gb or free space. Out of the 10gb, pick 512 for swap and the rest for an ext3 partition mounted at **/**.

---

### Post by Rui Pais on 2006-09-30
> **Keithod said:**
> Well as yous probably guessed - it worked!!! (insert woo hoo here!) Thank you very very much!
you're welcome :)

> Can you help me now to install it as a partition on my C drive? Please*

I noticed that when I used it from CD it had an option to "install" on the desktop so I presume I will be using that??
Yes, thats right.
But, if you don't mind an advice, try check things around first, using the live CD. 
Get a little familiarized with Linux first (I'm assuming from your question your haven't great experience with it... sorry if not the case) 
Check if your internet works. 
Check some information on net, most different thing from Windows world is permissions and administrative powers. Ubuntu, among other Linuxs, do it a slightly different using the sudo command (or gksudo a graphical interface) to set administrative powers to the 1st user configured on your (future) system. Read something about. Read the manual page on liveCd. 
Try to launch gparted (search menus or from a terminal, everything is a good exercise).
gparted will show how your disk is partitioned. Check interface/buttons/menus to get used and make your life easier on install.

check this [link here]("http://shots.osdir.com/slideshows/slideshow.php?release=659&slide=1") or another [here]("http://easylinux.wordpress.com/2006/04/30/").
it have several screenshots of the installation process, so you can see what will happen.

After that click on install and there you go. Make any question here... someone will always try to help you.

> Ubuntu = Free = Cool = Reliable, thats 3 things MS isnt!
you forget one = Free (one as in free speech and another as in free beer ;))

---

### Post by Apotheosis on 2006-09-30
Aimed at David Corrales ^^

What makes you think he only wants 10g? :S

Not only that, isn't the rule of thumb to have a the swap twice the size of your RAM?

---

### Post by Rui Pais on 2006-09-30
> **Apotheosis said:**
> Aimed at David Corrales ^^

What makes you think he only wants 10g? :S

Not only that, isn't the rule of thumb to have a the swap twice the size of your RAM?

That's a rule considered a little outdated this days (it came from the time when ram was expensive and computers have little). Today most of the time with 256 or 512M swap is hardly used. 

I find 10G a little short too, mine is 12G, i have downloaded deb files and /home on another partitions, and some times space rarefies... 

A good practice too is make an partition for /home.

i find a better place with explained screenshots of the installation with several alternatives here:[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
(thanks to aysiu, for so much detailed and well organized information on install process)

---

### Post by Keithod on 2006-09-30
Thanks again!

I will follow all that info and get back to you about it!

And yup I defo need to install Ubunto, I only started Comp Sci in uni about a week ago and I have to learn to use linux aswell. I know Windows...I only encountered Linux once [first time!] the other day when we doing "grep" commands...very useful for solving crosswords :) 

You're porb saying, hows he going to do Comp Science when he cant figure this out ha well you see I never had to partition a disk before, I wanted to but never found right info on the net to do it...and when I used an iso file before it was from MS to do a memory module test. so please excuse my stupidity! :)

Anyway I will let you know how I get on...

Again, cant thank you enough!

---

### Post by Keithod on 2006-10-01
Woo hoo! and its installed and working...thank you very much to everyone who helped me!!!

Just one last thing I am having a problem setting up my *wirless* network? It doesnt connect to the network... I go to system and then to network and select wireless. I put in my network name and WEP key and press okay but after opening up the web browser it wont load the page?? Anything ive forgooten to done?

---

### Post by David Corrales on 2006-10-01
I recommended 10Gb because linux usually stops growing after a while. Around 5Gb for the core system here.
Since he's starting, he probably wants to install Ubuntu with the least amount of interference possible. Assuming his disk could be a tad old, 10Gb sounds reasonable enough.
About the swap, as Rui Pais mentioned, nowadays you don't need 2xRAM swap space. In my case, I have 1.5gb physical and 550mb swap which gets rarely used above 1Mb.
As a tip, you can run **sudo apt-get clean** to delete all the cached .deb files. After a while, updates and new programs cached tend to pile up and eat up your space.
Nice link with screenies :)

---

### Post by David Corrales on 2006-10-01
> **Keithod said:**
> Woo hoo! and its installed and working...thank you very much to everyone who helped me!!!

Just one last thing I am having a problem setting up my *wirless* network? It doesnt connect to the network... I go to system and then to network and select wireless. I put in my network name and WEP key and press okay but after opening up the web browser it wont load the page?? Anything ive forgooten to done?

Try installing *network-manager-gnome* to handle wireless connections. Also, depending on the brand of your card you might need to use *ndiswrapper*, in order to get your card up and running.
If you want to install them using the command line you can use the following line (after enabling all repositories):
**sudo apt-get install ndiswrapper-utils ndisgtk network-manager-gnome**
You can also use Synaptic to install them if you prefer a graphical interface :)

---

