---
title: "Planning to switch"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by faustianoverdrive on 2007-12-05
So, I'm in the process of building a new box- should get the last part friday. 

I've decided this would be the time to experiment with linux- I've got no real experience. I've taken two Comp Sci classes, and become convinced that I would need to move to Linux sometime. At this point I played with the livecd for a couple of distros, but never got more then a couple hours (For the past couple years I've been using just a laptop- so, I could niether write to the hd or access my wireless with livecds... so It was a more frustrating then educating experience)

Well, I know this machine can't be a dedicated ubuntu box. The box is also going to be wireless, so I'm guessing a livecd would still not be able to access the internet.  And while i've read, once upon a time, a site for setting up a virtual machine with ubuntu to play with, I can't find it again. (I also know nothing about virtual machines, but I believe I read somewhere that the motherboard I got does not support amd's hardware virtulization, or something to that effect. I don't know if that means it'd still be possible to have a virtual machine or not.) 

I'm guessing that means I'm going to be stuck dual-booting. Now, as for partition planning, I've got an older 20 gig drive that I was thinking of setting up the OSes on, and then using the new 500 gig as shared data- guess that means fat32 formatting. 

Now, being a complete newb, I'm probably going to need some help with even the most basic choices. 

At first, I'm not sure if I should go with Kubuntu or Ubuntu. I've read enough to know that the difference is merely KDE vs Gnome, but with no real linux experience, I'm not sure which I would prefer. What's the practical differences between the two?

---

### Post by skyjacker on 2007-12-05
> **faustianoverdrive said:**
> So, I'm in the process of building a new box- should get the last part friday. 

I've decided this would be the time to experiment with linux- I've got no real experience. I've taken two Comp Sci classes, and become convinced that I would need to move to Linux sometime. At this point I played with the livecd for a couple of distros, but never got more then a couple hours (For the past couple years I've been using just a laptop- so, I could niether write to the hd or access my wireless with livecds... so It was a more frustrating then educating experience)

Well, I know this machine can't be a dedicated ubuntu box. The box is also going to be wireless, so I'm guessing a livecd would still not be able to access the internet.  And while i've read, once upon a time, a site for setting up a virtual machine with ubuntu to play with, I can't find it again. (I also know nothing about virtual machines, but I believe I read somewhere that the motherboard I got does not support amd's hardware virtulization, or something to that effect. I don't know if that means it'd still be possible to have a virtual machine or not.) 

I'm guessing that means I'm going to be stuck dual-booting. Now, as for partition planning, I've got an older 20 gig drive that I was thinking of setting up the OSes on, and then using the new 500 gig as shared data- guess that means fat32 formatting. 

Now, being a complete newb, I'm probably going to need some help with even the most basic choices. 

At first, I'm not sure if I should go with Kubuntu or Ubuntu. I've read enough to know that the difference is merely KDE vs Gnome, but with no real linux experience, I'm not sure which I would prefer. What's the practical differences between the two?In my experience Kubuntu is that it is easier to customize and doesn't require as much interaction with the terminal as Gnome. It is similar to a Windows feel, but without the bloat and slowness. You just have to try them both and see which one you prefer. You can have them both at the same time and pick which one to use at the log in screen. Good Luck!!

---

### Post by n00buntu_tim on 2007-12-05
Do it - I just installed ubuntu on an old pc, and am genuinely excited about computing for the first time in a while.  So much stuff you thought should be possible under other OSs is possible under ubuntu.

My advice (such as it is at this stage) woulld be not to bother with a dual boot unless you really need it - that way you will be forced to solve the problems and will gain confidence faster.

I'd stick with Gnome for now - if only because by being the default there are more people using it, and hence more support - especially for us newbies.  You can always install KDE instead / as well.  Plus, software specifically written for one desktop environment will usually work on another (e.g. Kile).

Happy ubunting.

---

### Post by Therion on 2007-12-05
I've had mixed success with getting internet connectivity with LiveCD's; it seems like it's kind of a crap shoot, really.  I've never had a problem getting my wireless network up and running under a full-install of Ubuntu.

As for dual-booting, you make it sound like a bad thing; I can assure you it's not.  I've been dual-booting Ubuntu/WinXP for some time now, and frankly, I think it's the best of both worlds.  I've not needed to boot into XP in months, nor have I, but it's not hurting anything being there and I like having options.  Every day that goes by, however, brings me closer to wiping the XP partition and taking the Big Leap.  But, and more to the point, IMO, dual-booting pretty much rocks!  Don't think of it as being "stuck"; it's both easy and convenient in my experience.  

Can't really help you with the KDE vs. Gnome thing, I think it boils down to personal preference more than functionality, but again, I don't really know.  I've only used Gnome but I'm very happy with it.

As for your dual hard-drive setup, while *I* would consider a 20GB drive to be the absolute bare minimum for booting two OS'es it's going to be sufficient to the task.  Also, you are not limited to using FAT32, my secondary drive is NTFS formatted and I have zero problems mounting/using that drive in both Ubuntu and XP.  There may be some compelling reasons to use another FS other than NTFS, but I don't know what they are and NTFS is working just fine for me.

Other than that, I too would say "Go for it!".  It was love at first boot for me and Ubuntu.  XP is hanging around on my drive, it's true... But its days are numbered.

---

### Post by faustianoverdrive on 2007-12-05
Unfortunately, I still need windows. I'm still in school, and several courses do lab-sim cd things. stuff I would absolutely have to do,  and couldn't be sure would run through wine. 


Now, I do like my GUI- while I know a spiffy desktop isn't necessary, I'd like to have something easily customized and a bit more useable- If I'm going to switch, I'd like a desktop that could compete with Aero or so. 

So, I'm guessing I'll go with Kubuntu.

The computer I'm building does support 64 bit. However, glancing through the forums, it looks like 64 bit operating systems are a bit harder, and not perfectly compatible with 32 bit software. That means I should probably stick with 32 bit, at least until i'm very comfortable with ubuntu? ( I do do a fair bit of ripping and burning, so I would appreciate the speed increase, but I guess it's not really a requirement.)

As to the formating, I wasn't sure that ubuntu could read/write NTFS. Thought I saw something somewhere saying it could read it, but... I've had a hard time finding the websites I saw in my previous ubuntu material search.

---

### Post by LowSky on 2007-12-05
use gnome as its the refernece point for most info off this site, and It is much easier on new users

other than that Ubuntu 7.10 can natively read NTFS which is better then FAT32, so if you already have it set up with NTFS, leave it the way it was.

as for the virtualization, AMD stuff works fine, but I suggest using duel boot because I think you will want your USB and Graphics to work the way they are supposed to.

as for aero effects, gnome is more stable while running compiz. Compiz puts Areo to shame!!!

---

### Post by Therion on 2007-12-05
> **faustianoverdrive said:**
> ...  If I'm going to switch, I'd like a desktop that could compete with Aero or so. 

I just read this and felt compelled to respond.

HAHAHAHAHAHAHA!!!  Compete with Aero?  My friend, [Compiz Fuzion]("http://i240.photobucket.com/albums/ff243/aaapha/53efe8e8.jpg") *crushes* Aero, steals its lunch money and then taunts it for weeks with prank phone calls.

---

### Post by faustianoverdrive on 2007-12-05
After two more posts, I'll go with Gnome (and I didn't realize exactly how compiz fuzion worked... for some reason I thought it was part of Gnome or someting along those lines. I've got a lot to learn, it looks like). After a bit of playing around, I'll give KDE a test drive or so. Considering my gf is also going to be using this, it'd be nice if I could get something that felt familiar to windows users (I know she could just boot into xp, but that would quickly become a hassle. Hoping to win her over to ubuntu too. )

---

### Post by vikram on 2007-12-05
> **faustianoverdrive said:**
> After two more posts, I'll go with Gnome (and I didn't realize exactly how compiz fuzion worked... for some reason I thought it was part of Gnome or someting along those lines. I've got a lot to learn, it looks like). After a bit of playing around, I'll give KDE a test drive or so. Considering my gf is also going to be using this, it'd be nice if I could get something that felt familiar to windows users (I know she could just boot into xp, but that would quickly become a hassle. Hoping to win her over to ubuntu too. )


your 500 G partition doesnt have to be FAT 32 to be shared between linux and windows. FAT32 gives a filze size limitation of around 4GB so DVD ISOs are a problem you can partition it as ext3 and use a windows ext driver (I used it extensively to access linux folders from XP )  see [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

you can also format it as NTFS and get rw support through the ntfs-3g driver. I would recommend the first option as I have noticed some wierd things when mounting fat systems esp with small and cap letters etc. 

Both KDE and GNOME are great DEs and have loyal and sometimes fanatic followers. Since they are free try both out along with window managers like Xfce, enlightment and see what works for you. I started with GNOME too but soon startedd using KDE because I found it to be be familiar since I was used to windows and more customizable. Maybe it was because I was a newbie and didnt know all the options I had to use the command line way more often in GNOME than in KDE. Not that this is a bad thing - I love the CLI and use it quite often (long time solaris user) its just that when starting to get familiar with a new OS I preffred to use the GUI to get started and got used to the CLI at my own space.

---

### Post by faustianoverdrive on 2007-12-05
Is there any hassle or issuses using a windows ext driver? Once it's installed, can i just kind of forget about it, or am i going to have to add extra steps to saving/running stuff while in xp?

And I know tis is going to be a headache, but i'm going to need to get that wireless working asap. 

my card- [http://www.newegg.com/Product/Product.asp?Item=N82E16833124115](http://www.newegg.com/Product/Product.asp?Item=N82E16833124115) 
I only bought it after I saw it listed somewhere as a card that had worked on ubuntu.. Just hope it doesn't mean i'm going to have to spend a lot of time banging heads with it before it works. 

Anyone know where I could get set up intructions for it, or at least the most newb friendly wifi setup help?

---

### Post by vikram on 2007-12-05
> **faustianoverdrive said:**
> Is there any hassle or issuses using a windows ext driver? Once it's installed, can i just kind of forget about it, or am i going to have to add extra steps to saving/running stuff while in xp?

And I know tis is going to be a headache, but i'm going to need to get that wireless working asap. 

my card- [http://www.newegg.com/Product/Product.asp?Item=N82E16833124115](http://www.newegg.com/Product/Product.asp?Item=N82E16833124115) 
I only bought it after I saw it listed somewhere as a card that had worked on ubuntu.. Just hope it doesn't mean i'm going to have to spend a lot of time banging heads with it before it works. 

Anyone know where I could get set up intructions for it, or at least the most newb friendly wifi setup help?

Once you use the ext2 driver (it works with ext3 too ) you assign it a drive letter in windows and its the same as any other for all purposes. appears in explorer, can open save using MS Office etc.

Not sure about the wifi, if Ubuntu doesnt automatically detect it you can use ndiswrapper with instructions in the community doc. your milage will vary as it depends on the wireless card.

---

