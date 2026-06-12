---
title: "kubuntu or just ubuntu ?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by jnorthr on 2007-06-21
Hello world -
how do i choose which of these two versions of ubuntu to use ? I have a 256MB ram and 20GB hard drive. Does it make any difference ?
Can I also just say a big 'thank you' to each and every one of you who spend so much of your valuable time helping the newbies - many thanx jim

---

### Post by diatribe on 2007-06-21
256mb of ram is low, I would go with either xubuntu or ubuntu; kde is kind of bloated imo

---

### Post by buuntuu! on 2007-06-21
it's exactly the min. requirement of ubuntu so xubuntu would seem the logical choice if you want to enjoy your ride....

---

### Post by jnorthr on 2007-06-21
Have i read this correctly - xubuntu is not part of the official ubuntu project. Do i sacrifice anything by using xubuntu ?

---

### Post by diatribe on 2007-06-21
xubuntu IS part of the official project, and it just gives you a different ui.  it is less resource heavy, and you do not sacrifice anything by using it

E: attached xfce screenshot; xfce has panels like gnome I just removed them ;p

---

### Post by phr0ze on 2007-06-21
You could always install ubuntu and add the xubuntu manager after so you can choose when you log in.

---

### Post by allix on 2007-06-21
> **jnorthr said:**
> Have i read this correctly - xubuntu is not part of the official ubuntu project. Do i sacrifice anything by using xubuntu ?

Xubuntu is supported by canonical. Same as Ubuntu.

[http://www.ubuntu.com/products/whatisubuntu/derivatives](http://www.ubuntu.com/products/whatisubuntu/derivatives)

---

### Post by LaRoza on 2007-06-21
As a side note, no matter which *buntu you install, you can always add the desktop environments, so whatever you choose is not written in stone. Your RAM is low, so follow the above poster's post.

---

### Post by buuntuu! on 2007-06-21
as the hd is small size matters... having 2 window managers will take its toll and the standard apps installed with ubuntu aren't exactly lightweight either (eg. open office). a clean install would be best imo.

---

### Post by Xoanan on 2007-06-21
I have Xubuntu myself;  it uses the XFCE desktop environment. I loaded it onto a system w/ 128 MB of RAM. Its running fine for me. 

I couldn't load Ubuntu due to the RAM requirements.

---

### Post by LaRoza on 2007-06-21
If you want a distro that works well with low RAM, you could look at Zenwalk.

---

### Post by jnorthr on 2007-06-21
Ok, well i'll take a stab at xbuntu and in an hour or so i'll burn a cd from the .iso image, then be back.
thanx

---

### Post by jnorthr on 2007-06-21
just 1 more question -
it looks like a separate partition for /home is a good idea. Can i make it a FAT32 partition rather than ext2 or ext3 - just so i can move all my java source between evironments ?

---

### Post by Kubunteando on 2007-06-21
256MB is enough to run Kubuntu, that is the minimum Recommended memoery. Of course, if you open 10 applications simultaneously is will get a bit slow. But it is a better option to Xubuntu. I have run Kubuntu Feisty with 128MB and it was using a lot of SWAP memory what made it slow. But 256MB is enough.

The applications is Xubuntu a too simple, and you will end up installing Kubuntu or Gnome applications. But if you use just Kubuntu you will get the benefit of resource saving because they use the same basic libraries, so when you open various applications simultaneously from Kubuntu you will actually save memory.

So I would say go for Kubuntu 7.04, you will a happy Kubuntu user.

If you use Firefox, that one is quite memory hungry, there are several tutorials on the Internet to reduce the memory consumption.

---

### Post by diatribe on 2007-06-21
> **Kubunteando said:**
> 256MB is enough to run Kubuntu, that is the minimum Recommended memoery. Of course, if you open 10 applications simultaneously is will get a bit slow. But it is a better option to Xubuntu. I have run Kubuntu Feisty with 128MB and it was using a lot of SWAP memory what made it slow. But 256MB is enough.

The applications is Xubuntu a too simple, and you will end up installing Kubuntu or Gnome applications. But if you use just Kubuntu you will get the benefit of resource saving because they use the same basic libraries, so when you open various applications simultaneously from Kubuntu you will actually save memory.

So I would say go for Kubuntu 7.04, you will a happy Kubuntu user.

If you use Firefox, that one is quite memory hungry, there are several tutorials on the Internet to reduce the memory consumption.

If he has any programs that use gnome dependencies, the dependencies will be installed; he does not need the ENTIRE UI.  

also I think /home has to be ext3 but I am not sure

E:
You can use FAT32 as an additional data partition, but you cannot mount it as /home

/home is a special folder that has a lot of permissions, and FAT32 doesn't support user permissions.

---

### Post by dptxp on 2007-06-21
Make a SWAP partition of 1 to 2 GB first at the end of the drive using GParted (download it, make live CD and boot with it). Else you may not be able to even run the live CD. Some RAM goes to video too.

This is important. Xubuntu may run, Kubuntu and Gnome did not run on my desktop.
Had to make SWAP first. Then Installed Ubuntu.

---

### Post by diatribe on 2007-06-21
With 256 the livecd should run, I have heard of them running on as low as 192

---

### Post by dptxp on 2007-06-21
You may lose a lot of time. If Live runs, Install can be a big problem. Partitioning uses RAM.

With Xubuntu you should not have any problem.

---

### Post by stevecaldwell on 2007-06-21
> **jnorthr said:**
> Hello world -
how do i choose which of these two versions of ubuntu to use ? I have a 256MB ram and 20GB hard drive. Does it make any difference ?
Can I also just say a big 'thank you' to each and every one of you who spend so much of your valuable time helping the newbies - many thanx jim

Hello,

I've set up a used computer for my teen son (Compaq Deskpro EN Pentium III, 800 MHz, 256 Meg RAM, 20 Gig HD) using Ubuntu (Feisty 7.04).

I've haven't benchmarked it, but the used Ubuntu computer performance feels comparible to the performance I get from a Windows XP machine (Dell Pentium 4, 2.8 GHz, 512 Meg RAM, 320 Gig HD) for routine tasks (web surfing, email, word processing, listening to MP3 audio, etc).

Good luck,
Steve

---

### Post by jnorthr on 2007-06-21
I did try the live CD before and ran the install up to the partition setp 4 of 7 without problems - just chickened out before doing the full thing.

---

### Post by vexorian on 2007-06-21
IF you really got a hard time deciding ,you can download the 3 flavors and try them in live-cd mode before making a decition, with 256IMHO you can run the 3 of them fine after doing some tweaks to Ubuntu or Kubuntu, I even could run windows XP on my 256MB computer and THAT's bloated.

Of course Xubuntu is probably going to be the fastest alternative in this case.

---

### Post by Xoanan on 2007-06-21
I didn't chicken out; but then again, what was on that machine before was Windows ME which I had every intention of leaving behind. LOL!

---

### Post by Webby_s on 2007-06-21
This is what i am thinking of trying on an old Gateway that had WinME. And then I upgraded to XP (for my parents) Now I may try Xubuntu because I tried Ubuntu and on booting from the Live CD it keeps coming back with "not enough memory "Not enough memory". So I will try X.

Any thoughts?  I don't know exactly how much ram this said Gateway has but I thing it may be around 128mb :( I know. Why I want to do this is so I can learn Ubuntu and then build my own rig very soon!

---

### Post by ryanVickers on 2007-06-21
> Can i make it a FAT32 partition rather than ext2 or ext3 - just so i can move all my java source between evironments ?
You could, but I wouldn't recommend it - windows filesystems, especially the FAT series, are very prone to corruption.  I suppose you still could, but the limitations are high risk of failure (keep backups frequently!), and no simgle file can be over 4Gb (fat***32***).

---

### Post by Xoanan on 2007-06-21
128 megs is exactly what I have on mine.  Try Xubuntu.  With Ubuntu, you have to have at least 256 megs of RAM.  Oh yes, I would recommend the alternate install CD though. You have to have more RAM for the Live CD

On my machine, I started the pc up and pressed the DEL key.  This gave me my system info.  It also allowed me to change the BIOS to boot from CD

---

### Post by jnorthr on 2007-06-21
Can i just clarify this - once either/any version is installed, which version takes the smallest digital footprint - xbuntu or kbuntu ? I feel that a smaller footprint may imply better performance and on 256MB performance may become an issue. Of course i hope to blitz the windows98/se soon any way, if i can get to developing java on ubuntu.

---

### Post by Xoanan on 2007-06-21
Xubuntu requires less CPU usage.  I have had no Java issues with it myself

---

### Post by Xoanan on 2007-06-21
Here is a pic of my Xubuntu desktop, if that gives you an idea of its capabilities
[IMG]http://ubuntuforums.org/g/images/160785/small/1_6a00cd973389c34cd500d09e793208be2b-200pi.png[/IMG]

---

### Post by ryanVickers on 2007-06-21
Yes, once something is installed, you can add another.  For instance, I had ubuntu and added KDE making it ubuntu and kubuntu.  The command for adding kde is:
```
sudo apt-get install kubuntu-desktop
```

I imagine that you could do the same for adding ubuntu or xubuntu to either one aswell, just a different letter!

---

### Post by vexorian on 2007-06-21
You can make an small FAt32 partition to share files between windows and ubuntu, this partition shouldn't be the main partition on neither windows or Ubuntu though since it is a very bad filesystem actually...

---

### Post by dptxp on 2007-06-22
Go for FAT32 if you love SCANDISK :).

You can make Windows read EXT3.

I suggest you to go for regular Ubuntu (Gnome) after making a SWAP with GParted.
If you find it slow, then you can add xfce-desktop to it and use any at any time.
Gnome is the easiest to navigate and perhaps most stable. It is default Ubuntu.

---

### Post by Webby_s on 2007-06-22
> **Xoanan said:**
> 128 megs is exactly what I have on mine.  Try Xubuntu.  With Ubuntu, you have to have at least 256 megs of RAM.  Oh yes, I would recommend the alternate install CD though. You have to have more RAM for the Live CD

On my machine, I started the pc up and pressed the DEL key.  This gave me my system info.  It also allowed me to change the BIOS to boot from CD

Thanks for the info!  I was about to load the regular live CD but I will now download the alternate CD Thanks:D

---

