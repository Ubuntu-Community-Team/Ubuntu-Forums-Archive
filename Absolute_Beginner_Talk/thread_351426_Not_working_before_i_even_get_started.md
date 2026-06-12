---
title: "Not working before i even get started"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by -Ghost9- on 2007-02-01
I was attempting to use the live CDs to mess around a bit before installing, but I've run into issues. I tried running ubuntu and kubuntu 6.10, but they all failed to load. I see the loading bar in the middle going and filling up, but it eventually reaches a point where everything stops,  I see these blue and green lines across the screen, and the cd stops running with the screen just frozen there. I also tried doing the graphic safe mode but got the same result.

So since I read how 6.10 is somewhat of a testbed, i decided I'd go back and try dapper. Well i do the normal run and everything seems to go fine until it tells me it can't load my video platform. So i take a long sigh, and try running the disc in the graphic safe mode. This time it works and appears to run, but now I am concerned. I've read that ati doesn't have good linux support and my vid card is an ati x850xt. Does this mean I'm looking at a lot of problems if I attempt to go through with an install?

My hardware setup:
ATI RADEON X850 XT 256MB 16X PCI EXPRESS
(939-pin) AMD ATHLON64 FX 55 CPU w/ Hyper Transport Technology
(939-pin Socket) ASUS A8V-E Deluxe VIA K8T890 Mainboard
2048 MB (1GBx2) PC3200 400MHz Dual Channel DDR MEMORY Corsair XMS High Performance Memory w/ Heat Spreader
Western Digital Raptor 74GB 10,000RPM Serial ATA 150 8MB Cache WD740GD
ULTRA X-Connect 500W ATX PS w/2 80mm Fans
Memorex 52x CDRW/DVDrom

---

### Post by Darklighter137 on 2007-02-01
Hi!  My graphics card is also in the ATI RADEON Express line, and it works very well for me.  Did you burn your own CD's?  If so, please try buring the latest Ubuntu release (6.10) on a low burn speed (no more than 4x).  The last few times I tried Ubuntu, my graphics were messed up.  Just today I burned a fresh CD (with the same ISO I used before) and the graphics worked flawlessly.

Maybe you will not have similiar success, but it worked for me. ^_^

---

### Post by -Ghost9- on 2007-02-01
i did burn my own cd and i did burn it at max speed. I'll try slowing the burn speed and see if that works. thanks!

---

### Post by Darklighter137 on 2007-02-01
Max speed is sure to cause nothing but errors.  It should always be <= x4 speed.  It took about 25 minutes at x4 on my drive.  If you wish to be extra cautious, you might turn it down even lower.

Do not dispair, it will work (unless your card is somehow radically different from mine, but I doubt it)! I've gone through CD's that wouldn't boot, and several that refused to see my monitor and graphics card settings correctly.  This latest burn does everything right. ^_^

---

### Post by -Ghost9- on 2007-02-02
i burned the 6.10 version at 4x, and that disc worked even less than the first time. The 52x disc atleast started to work, the 4x disc wouldn't even load. the green letters came up saying loading, but then it just froze. nothing happened. disc would read every 40 seconds or so. One time I got an I/O error. so i guess i'll be trying the dapper version and hope for the best.

---

### Post by -Ghost9- on 2007-02-02
I decided to bring my discs into work and see if they would function on another computer. They seemed to function just fine on my work computer, but I noticed some significant differences. 

At home at the loading screen the graphics are all messed up and grainy(reminds me of how windows looks in safe mode). The loading text at home is also different; it's green and there's two sets of it scrolling across the top of the screen. 

Is this a video problem with my system? What can I do, as I can't even get to an install screen, except for the 6.06 version in graphic safe mode....

---

### Post by lamego on 2007-02-02
Download and use the alternate CD, the problem with the LiveCD with some video cards it is not able to setup the graphical mode.
The Alternate CD uses a text installed, its easy to use, and after installing the system you can setup/install the proper graphical driver.

---

### Post by jd65pl on 2007-02-02
> try buring the latest Ubuntu release (6.10)

Note that whilst edgy maybe the latest release in terms of time it can prove to be unstable due to its nature of using more "cutting edge" software. For a more supported and proven system use dapper.

---

### Post by -Ghost9- on 2007-02-02
ok. so i took the advice of some people and installed 6.10 using the alternate CD. well it still doesn't work. ubuntu starts loading and then it get these blue and green lines and nothing happens. I like the whole dual boot setup though. that's pretty cool. 

Any suggestions? 

And another question. I'm wondering if I should try installing 6.06 since that livecd worked in the graphic safe mode. But now how do I uninstall 6.10?

Also, the partition automatically did half my drive, if I want that back for use with windows, do I have to reformat my entire drive?

---

### Post by pegazuz on 2007-02-02
> **-Ghost9- said:**
> ok. so i took the advice of some people and installed 6.10 using the alternate CD. well it still doesn't work. ubuntu starts loading and then it get these blue and green lines and nothing happens. I like the whole dual boot setup though. that's pretty cool. 

Any suggestions? 

And another question. I'm wondering if I should try installing 6.06 since that livecd worked in the graphic safe mode. But now how do I uninstall 6.10?

Also, the partition automatically did half my drive, if I want that back for use with windows, do I have to reformat my entire drive?

I had tried earlier to install Ubuntu 6.10 cause it booted up fine as a live CD but for reasons i don't understand it wouldn't install. I then tried Mepis and it installed fine but wouldn't boot up from the external hard drive.  I also tried several other vesions of Linux Live CDs which wouldn't boot up at all. I then tried Kubuntu 6.06 and it installed fine and more important booted up my computer.  I also tried Puppy which is a real small easy to install Linux that I then installed on a small USB flash drive which I can also use to boot up Linux.

  I use the Kubuntu 6.06 on an external USB hard drive and it is very similar to Ubuntu but I like the KDE interface better than GNOME.  I went with a an external HD and USB Flash Drive cause I wanted to try them without any risk of wrecking my Windows Multimedia OS till I am ready to give it up.  Generally the install features on the Live CD's will either reformat the hard drive for or use the space you leave blank when you delete a partition.  If you leave it and don't reformat you may encounter space problems unless you have a large hard drive.

---

### Post by -Ghost9- on 2007-02-02
i went through the 6.06 live cd in graphic safe mode and was going to install but the only partition options it gave me was to reformat the entire drive, or manually go through and do it. so I looked at manually doing it, but I don't really know what i'm doing with that. There were 3 partitions. One was the ntfs partition(50G), and then there was ext (18.5G), and then an "extended" 895.5 or something(MB). I'm not sure what to do. I guess i'll try reading up on it to figure it out unless someone can break it down for me real easy.

---

### Post by -Ghost9- on 2007-02-02
well i managed to go through the manual partitioning of the 6.06 version. It worked! ubuntu 6.06 seems to be working, but the 6.10 version is not. The video will only go to 1024x768, which I'm assuming has something to do with not having the right video drivers. I need ot search for ati drivers. also something odd in grub now though.

When the boot menu comes up, it has 5 options for ubuntu instead of the first three that i first saw. Now there's:

Ubuntu, kernel 2.6.15.27-27-386
Ubuntu, kernel 2.6.15.27-27-386 (recovery mode)
Ubuntu, kernel 2.6.15.27-26-386
Ubuntu, kernel 2.6.15.27-26-386 (recovery mode)
Ubuntu, memtest86+

and then Windows XP

Now either of those Ubuntu choices seem to do the same thing, but it's weird that there are so many options isn't there?

---

### Post by -Ghost9- on 2007-02-02
tried updating the video. :( now xserver won't start and I can't seem to get back into visual mode.

---

### Post by pegazuz on 2007-02-03
> **-Ghost9- said:**
> well i managed to go through the manual partitioning of the 6.06 version. It worked! ubuntu 6.06 seems to be working, but the 6.10 version is not. The video will only go to 1024x768, which I'm assuming has something to do with not having the right video drivers. I need ot search for ati drivers. also something odd in grub now though.


As a beginner I was advised to stick with 6.06 till I learn enough to fix things.  I think it is harder to get set up in the newer versions since they have more problems and require more skill to fix things.  I have also read that the newer version Edgy won't work well with my wireless internet connection so I am concentrating on getting one version to run well and feel I am half way there.  The advantage of live Cd's is they allow you to see if it will work with your system without a lot of upgrading and fixing.  If 6.06 is working why not try to get everything working there first?

---

