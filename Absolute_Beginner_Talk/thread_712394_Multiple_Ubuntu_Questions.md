---
title: "Multiple Ubuntu Questions"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by M4v3r1kk on 2008-03-01
So a friend recently showed me Linux BERYL which wowed me. So now I am in the process of figuring out whether I get BERYL or not but first I have a couple of questions.

[LIST]
[*]Do I **have** to overwrite my current version of Windows (Vista) if I want to install Ubuntu?
[*]Can I install Ubuntu on an external hard drive?
[*]What do I need to do to get BERYL?
[*]And finally, why can I not run a demo of Ubuntu when I reboot my computer?
[/LIST]

edit: As far as I know I need Ubuntu to use BERYL. This is why I'm asking so many questions about Ubuntu.

---

### Post by amazingtaters on 2008-03-01
1. No, you do not need to overwrite your Windows installation.
2. You can install Ubuntu to an external HDD
3. [http://ubuntu-tutorials.com/category/compizberyl/](http://ubuntu-tutorials.com/category/compizberyl/)
4. You should be able to run the LiveCD, but you need to make sure that your primary boot device is set to your optical drive and not your hdd.

---

### Post by ugm6hr on 2008-03-01
> **M4v3r1kk said:**
> 
[LIST]
[*]Do I **have** to overwrite my current version of Windows (Vista) if I want to install Ubuntu?
[*]Can I install Ubuntu on an external hard drive?
[*]What do I need to do to get BERYL?
[*]And finally, why can I not run a demo of Ubuntu when I reboot my computer?
[/LIST]

edit: As far as I know I need Ubuntu to use BERYL. This is why I'm asking so many questions about Ubuntu.

1. Vista and Ubuntu can co-exist in a "dual-boot" (ask again or search for advice on how to do this)
2. Ubuntu can be installed on an external HD.  The process for doing so is straightforward, but you do need to take care not to overwrite the Vista bootloader when installing Ubuntu that way (again - ask first)
3. Compiz Fusion is default on Ubuntu 7.10.  I am not a big fan of Desktop Effects, but I believe Beryl has now merged with Compiz to become Compiz Fusion
4. The Ubuntu LiveCD can be used as a "demo" - but be aware it will be horribly slow compared to a HD installation.
5. Beryl (or Compiz Fusion) will run with any Linux which uses Gnome, KDE or XFCE (which are different Desktop Environments).  Ubuntu is a good example of Linux with Gnome.

---

### Post by M4v3r1kk on 2008-03-01
[list]
[1]So how do I install the demo to try it out?
[2]Also how can I make Vista start from the demo? (Do I need to access BIOS? If so how?)
[/list]

Thanks a lot for helping me.

edit: Never mind that. Please disregard it. My new question is when I decide to install Ubuntu on an external Hard Drive what will I need to do? Do I need dual-boot hardware or what?

---

### Post by Midwest-Linux on 2008-03-01
You can, or should be able to install Ubuntu on another partition on your hard drive. My personal recommendation would be to install another hard drive on your computer. Then disconnect the vista hard drive and install Ubuntu on the new hard drive. Simply switch out hard drives. I do that on one of my computers where I have Linux Mint 4.0 on one hard drive and Windows XP on the hard drive. While it may seem to be more of a pain, I think everything runs better that way.

 I do have dual boot on my Windows 2000 computer with Ubuntu 7.04 as a dual boot. It works good. when installing Ubuntu, I always prefer the alternate CD/text installer. Its more straight forward and there is no guess work. Use the guided partitioner always when doing a dual boot so not to erase the current OS by mistake.

 The live CD can and should be able to run just fine on your computer without installing anything so you can test out the distro before deciding to install it. The live CD SHOULD be able to run on your computer, unless Vista has some "feature" preventing it. The CD ( I believe) should boot right up if you put the disc in. Otherwise put the disc in the computer, shut off the computer and restart it and then it should boot up from the disc and run it from the disc...IIRC I don't use Live discs however, except for Puppy Linux.

But again, at least for me I recommend the alternate text CD for permanent installations...thats just my opinion...others might tell you different.

 Ubuntu is a great OS, but I personally prefer Linux Mint 4.0 over the other distros. Others might chime in with something different. Beryl should be right on there on Linux Mint. Though I have not used it...yet.

---

### Post by M4v3r1kk on 2008-03-01
So I have tried out Ubuntu and I have a couple of more questions.

1. Can I totally customize it **without** BERYL?
2. How do I get BERYL?

note: I'm running a laptop (hence why I want a Hard Drive even if I wouldn't install Ubuntu).

edit: Keep forgetting things. What do I need to dual-boot? Any good sites with lots of information?

---

### Post by ugm6hr on 2008-03-01
> **M4v3r1kk said:**
> So I have tried out Ubuntu and I have a couple of more questions.

1. Can I totally customize it **without** BERYL?
2. How do I get BERYL?

note: I'm running a laptop (hence why I want a Hard Drive even if I wouldn't install Ubuntu).

edit: Keep forgetting things. What do I need to dual-boot? Any good sites with lots of information?

1. Yes
2. Please read my previous reply (Ref: [http://www.beryl-project.org/](http://www.beryl-project.org/))
3. Dual-boot sites: [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu) [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by northern lights on 2008-03-01
> **M4v3r1kk said:**
> 1. Can I totally customize it **without** BERYL?
Yes. Run ```
sudo apt-get compizconfig-settings-manager
```
Then, navigate to "System > Preferences > Advanced Desktop Effects Settings"

> **M4v3r1kk said:**
> 2. How do I get BERYL?
Don't. The Beryl project is no longer continued, and all features of the "latest" Beryl have been fused with compiz.

P.S. If you want to work in Ubuntu for real, might not wanna go to hyper with those FX...

---

### Post by M4v3r1kk on 2008-03-01
> sudo apt-get compizconfig-settings-manager
Where would I run the above code?

Also is Compiz Fusion available in the Advanced Desktop Effect Settings?

---

### Post by Miller12 on 2008-03-01
The code is run in the Terminal
Applications > Accessories > Terminal


 or use search (the one at the top) in Synaptic
System > Administration > Synaptic Package Manager

*Also is Compiz Fusion available in the Advanced Desktop Effect Settings?*
Yes click on the bottom one

---

### Post by M4v3r1kk on 2008-03-01
Alright so I've chosen to use Ubuntu but now I'm stuck on installation.

[list]
[*] What is a good size for a partition?
[*] I want to use an external 500GB Hard Drive with no information from my Laptop drives but I also want to import settings from Vista, how do I do that during partition?
[*] Do I really need to use the switch option with a 500GB Hard Drive? [/list]

Thanks again for all the answers.

---

### Post by Midwest-Linux on 2008-03-01
I found this pictorial of how to do a dual boot with Vista and Ubuntu.

[http://vista.blorge.com/2008/02/22/how-to-dual-boot-vista-with-ubuntu/](http://vista.blorge.com/2008/02/22/how-to-dual-boot-vista-with-ubuntu/)

---

### Post by M4v3r1kk on 2008-03-01
Alright important question. Will Ubuntu install where I put the partition or what mount point I select?

---

### Post by owbizi on 2008-03-01
You can separate folders on Ubuntu, to keep things more organizated.

/ is where system files will be, in general;
/home is where Ubuntu will store personal data, and, if you want, documents, pictures and so on.

You can put / as primary partition and /home as logical. Just don't forget the swap one too.

---

### Post by M4v3r1kk on 2008-03-01
Both / and /home are ext3 right? Oh and if I decide to use my remaining hard drive space as SWAP can I still actually save data on it?

---

### Post by owbizi on 2008-03-01
Well, I think the best is to format these two as ext3 (it's like Ubuntu's first choice), but it's up to you to decide. :)

And **no**, you can't save any data on the swap partition. By the way, it does not takes much space: max 1gb (or 2, if you don't have much ram), and rarely Ubuntu will use it all. As for / partition, I think 10gb, max 20~30gb will do fine!

---

### Post by northern lights on 2008-03-02
> **Miller12 said:**
> *Also is Compiz Fusion available in the Advanced Desktop Effect Settings?*
Yes click on the bottom one
:confused:

Compiz-fusion is Gutsy's default desktop effects manager. "Advanced Desktop Effects" is no more but a menu entry in "System > Preferences" that opens ccsm. In order to fully customize compiz-fusion, ccsm is the only neccessity not installed by default...

---

### Post by Miller12 on 2008-03-02
> **northern lights said:**
> :confused:

Compiz-fusion is Gutsy's default desktop effects manager. "Advanced Desktop Effects" is no more but a menu entry in "System > Preferences" that opens ccsm. In order to fully customize compiz-fusion, ccsm is the only neccessity not installed by default...


I'm still a noob. I thought you had to turn it on, 'Advanced Desktop Effects', but it may have been after I got the settings manager and followed a tutorial that I got things working.

---

