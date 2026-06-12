---
title: "Should I just stick with Windows? I've had very little success with Ubuntu"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by psam3 on 2008-01-26
About the only thing I managed to do was install the OS onto my hard drive in it's own partition, with no luck on booting it up. It seems like a simple problem but I could be wrong. Whenever I select Ubuntu from the grub menu it just goes to a black screen saying Input Not Supported. Doesn't that mean the resolution isn't supported with my monitor or could it be something else? If so how do I change it without booting into Ubuntu? If no one can help i'm sorry to say that I guess i'm stuck with Windows as I have been searching for about 13 hours for an answer and can't seem to find one. I've even made three threads here about it, only one was even answered. They suggested that I go into the recovery mode, but when I do it just stops when it gets to this
[   34.758156] =======================

Isn't their anyway to fix this????????:confused:

---

### Post by cmnorton on 2008-01-26
Occaisionally, you have to put something down and come back to it. You've made a good start by posting the initial error. People here are helpful, and you're likely to get an answer. 

Can you boot Ubuntu using the live CD? That would give you some information.

Dual-booting is a pain, and if you search these forums, you'll find a lot of info, including in the tutorial area.

---

### Post by Desperate on 2008-01-26
Patience my friend, there will be an answer from someone that has had the same problem, just give them time to find it, it's Saturday, they might not be behind the screen yet.
Try to boot with the live CD in save graphics mode( #2) and see what it needs to recognize your hardware better and do a search for your video card, you might find something.

Good luck and a good weekend

Richard

Edit: :) they're fast here :)

---

### Post by psam3 on 2008-01-26
I can't use the Livecd I had to use the alternate cd to install. I had absolutely no problems installing, just can't get Ubuntu to boot. I'm not sure if it's a problem with my videocard or just the wrong resolution. I have no idea what i'm doing when it comes to Linux. Pleassssssssssssssssssssssssssssssseeeeeeeeeeee help I would really appreciate it.

---

### Post by mortsahl on 2008-01-26
Try this ... boot into windows, set your resolution to 800 x 600, then try booting into Ubuntu again.  If you successfully boot into ubuntu you may have to install drivers for your video card so you can increase the res to what you want.

---

### Post by bwang on 2008-01-26
I have the same video card (GeForce 5200) and Ubuntu works fine so its probably not a display problem

---

### Post by benerivo on 2008-01-26
> **psam3 said:**
> it just goes to a black screenWhen you get to that black screen you mention, does it offer a command prompt for you to type things in to? If so, you can type```
sudo dpkg-reconfigure xserver-xorg
```and try to answer the questions as best as you can, or just go with the default options if you are unsure. Personally i would go with the simplest options on all the questions. If you are on a nvidia card, then one of the first answers is 'nv'. Hope this helps.

---

### Post by hyper_ch on 2008-01-26
you could also try other distros checking if they can better handle your video card.

I'd recommend:

Mepis (also debian based)
Fedora Core
openSuSe

---

### Post by Paul820 on 2008-01-26
> **bwang said:**
> I have the same video card (GeForce 5200) and Ubuntu works fine so its probably not a display problem

Same here, feisty and gutsy have been no problems with display using that card on my desktop.

---

### Post by The Cog on 2008-01-26
If the "Input not supported" message is from your monitor as you suspect, you can try this:
Press Ctrl-Alt-F1. If you get a login prompt that you can see, log in with the username and password you gave the installer, and then use this command:
```
sudo dpkg-reconfigure xserver-xorg
```
Take defaults wherever you're not sure, but make sure you choose the right resolutions and scan rates. Then use this command to restart the GUI:
```
sudo /etc/init.d/gdm restart
```

---

### Post by psam3 on 2008-01-26
> **The Cog said:**
> If the "Input not supported" message is from your monitor as you suspect, you can try this:
Press Ctrl-Alt-F1. If you get a login prompt that you can see, log in with the username and password you gave the installer, and then use this command:
```
sudo dpkg-reconfigure xserver-xorg
```
Take defaults wherever you're not sure, but make sure you choose the right resolutions and scan rates. Then use this command to restart the GUI:
```
sudo /etc/init.d/gdm restart
```

Do you know approximately how long I should wait until I press the key combination? I tried this and nothing happened.

---

### Post by psam3 on 2008-01-26
I'm beginning to think that maybe my computer just isn't compatible with Ubuntu.:cry:

---

### Post by wilsonmuse on 2008-01-26
I've set up 7.10 on a computer and have seen that same screen. Have you ever just let it sit for a while on that screen?

---

### Post by mrphud on 2008-01-26
Hello,

Like was said before "dual booting can be a pain" but probably the hardest thing is to retrain yourself to use another OS. Linux systems handle things differently but Ubuntu's GUI is a nice bridge. Expect the have some frustration but realize that you will be more knowledgable, in general, after you get the hang of things. A big question that I have is did you make a boot partition when you installed so that GRUB (OS selection screen) will come up before any OS is booted? If you don't have the options to choose then you might try reinstalling the partition. If you install manually you should create three partions:

swap           ~twice RAM ex (if your RAM is 1GB use 2 GB for the swap)
/boot      ext3       ~50 MB
/             ext3        (main partition) rest of the space you want to use.


You should also use no less than 10GB for you linux OS. If you have more questions let me know. I also recommend that you become aquainted with your BIOS. So far 3 major hardware conflicts have been solved (after hours of looking and thinking) by checking the BIOS (sound and USB problems in particular). I really do recommend sticking with Ubuntu and I do like it. I do, however, use Windows for my gaming simply because it is more 'reliable' for various reasons. Hope this helps.

Mr Phuuuuuuuuuuud

---

### Post by Aaron_M_E on 2008-01-26
I had a problem like this when I installed Ubuntu on my desktop, after doing the not supported thing for a while it loaded up an interface telling me that my graphics were not configured properly and allowed me to change settings. Eventually I discovered that I needed a different driver (I have an ATI card).

How long are you waiting at the not supported screen?

---

### Post by benerivo on 2008-01-26
> **psam3 said:**
> Do you know approximately how long I should wait until I press the key combination? I tried this and nothing happened.

It should just be about a second. You may be best of trying another distro  such as pclinuxos. As you have the alternate cd, i can suggest this...

Boot the CD and choose 'command line installlation' and install as guided. Be careful to install it in to the right partition if you have also have windows on the hard drive. Then reboot, and then enter your username and password. Then try```
sudo apt-get upgrade
```then```
sudo apt-get install xorg gdm gnome-core
```then```
sudo dpkg-reconfigure xserver-xorg
```then ```
sudo /etc/init.d/gdm start
```

If you do this, you will  have to navigate through a few options screens. Use the cursor arrows to move, space to select / deselect, and return to confirm.

---

### Post by arsenic23 on 2008-01-26
Ok...  well there are a lot of real solutions here, but I think everyone missed on the simplest one.

Do you have another monitor you could try this install with?

More then likely your just outputing video at a refresh rate (or maybe resolution) that your currant monitor doesn't suport.  If you have another monitor, and it does work, then you can just go into 'System > Preferences > Screen Resolution' to set your refresh rate and/or resolution to something your regular monitor suports.

I have a couple LCD screens that do this, so I keep an old CRT monitor around for when I have to reinstall.

---

### Post by stunningman on 2008-01-26
well tell me you installed ubuntu first or windows.if you installed ubuntu first than there could be some problem.always install windows first and than linux.alternately,you can use 'alternate cd'to install ubuntu in text mode.it makes life much easier and hassle free.also live cd takes half an hour to load properly and show you desktop till that time screen remains blank.the reason could be low memory.now there is a trick if you can make a swap partition first in you harddisk.live cd load fast showing desktop.you can install from there in graphical mode.

---

### Post by psam3 on 2008-01-26
> **arsenic23 said:**
> Ok...  well there are a lot of real solutions here, but I think everyone missed on the simplest one.

Do you have another monitor you could try this install with?

More then likely your just outputing video at a refresh rate (or maybe resolution) that your currant monitor doesn't suport.  If you have another monitor, and it does work, then you can just go into 'System > Preferences > Screen Resolution' to set your refresh rate and/or resolution to something your regular monitor suports.

I have a couple LCD screens that do this, so I keep an old CRT monitor around for when I have to reinstall.

This sort of worked. If I use an old crt monitor and the onboard graphics card rather than the Geforce Nvidia I was able to boot into the terminal. I wasn't sure how to change it so I could use the other monitor and graphics card though. Oh well, I guess i'm not getting out of Windows prison yet.

---

### Post by HermanAB on 2008-01-26
Hmm, when you are a new user and you run into serious problems like this where you can't get the GUI up, then it is best to try another distribution.  The main difference between distributions is the initialization code and installation wizards.  Apart from that, Linux is the same everywhere.

So I strongly recommend that you give Fedora, Mandriva, Suse, Mepis, PCLOS, Knoppix or whatnot a try and see how it goes.  Every distro has a large variety of hardware in their test labs, but nobody has everything ever produced on this planet, so they differ in their ability to handle weird stuff.

Cheers,

Herman

---

### Post by AnonCat on 2008-01-26
If you think it's the video card, try renabling your onboard video (and remembering to hook your monitor into it of course) and seeing if you get further into the bootup process.  Sometimes, even though you disabled the onboard video, Ubuntu continues to pick up on it for some reason and you get weird errors like this.  I have a 5500fx in my machine and I had to blacklist some junk in order to get it to stop conflicting with the onboard video even though I disabled it.

---

