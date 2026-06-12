---
title: "Want to install ubuntu studio"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by johnnyphive on 2007-05-13
I currently am running a dual boot with XP.  I have attached an image containing my partion layout.  Could somebody point me in the right direction in order to install studio?  If possible, i'd like to keep my default feisty intact in case for some reason i don't like studio.  If that is not possible, what is the best way for me to backup my current config of feisty, so if i want to go back to it, I don't have to start from complete scratch.

[IMG]http://pic60.picturetrail.com/VOL1741/8908562/16438267/252338678.jpg[/IMG]

---

### Post by Happy_Man on 2007-05-13
Resize /home by maybe 10 GB, make a new ext3 partition, use that for UbuntuStudio. of course, isn't there a way to install it from a working feisty install? Somebody tell this guy how to do that, too...

---

### Post by ep2011 on 2007-05-13
To "Upgrade" from feisty just run the 2 commands:

```
sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update

```

Then install the following packages with your favorite installer (apt-get, synaptic, aptitude, etc):

# ubuntustudio-desktop
# ubuntustudio-audio
# ubuntustudio-audio-plugins
# ubuntustudio-graphics
# ubuntustudio-video
# ubuntustudio-artwork
# ubuntustudio-gdm-theme
# ubuntustudio-icon-theme
# ubuntustudio-look
# ubuntustudio-session-splashes
# ubuntustudio-sounds
# ubuntustudio-screensaver
# ubuntustudio-theme
# ubuntustudio-wallpapers
# usplash-theme-ubuntustudio
# wired

---

### Post by johnnyphive on 2007-05-13
Will that give me the same effect as doing a clean studio install?

If i don't like it, how hard is it to uninstall?

---

### Post by happy-and-lost on 2007-05-13
Turn hda3 into a logical partition and cut it in half (or quarters!)

I'm dual-booting Ubuntu Studio and Kubuntu on a 10GB logical partition right now, works a charm :)

---

### Post by johnnyphive on 2007-05-13
> **happy-and-lost said:**
> Turn hda3 into a logical partition and cut it in half (or quarters!)

I'm dual-booting Ubuntu Studio and Kubuntu on a 10GB logical partition right now, works a charm :)

Anything i need to do to "prep" hda3 before changing to logical and adding a partition?  Do i run the risk of hosing my current installing by doing this?  After the install, will i have another option in grub?

Sorry for all the questions, but i'm somewhat new to linux (but not computers)

---

### Post by happy-and-lost on 2007-05-13
Well... yeah, it'll have to reformat, losing your existing install. But once it's done, it's done and you can play around with Linux distros to your heart's content.

---

### Post by johnnyphive on 2007-05-13
> **happy-and-lost said:**
> Well... yeah, it'll have to reformat, losing your existing install. But once it's done, it's done and you can play around with Linux distros to your heart's content.


Anything i can do to backup my current config (window decor, wallpaper, firefox favs, install apps / packages) so i don't have to do it all from scratch when i get back up and running?

---

### Post by happy-and-lost on 2007-05-13
All of your application data is stored in your /home partition, which includes everything you said except installed apps. Reinstalling apps is a snap with apt when you get going again though ;)

---

### Post by johnnyphive on 2007-05-13
Even my current desktop layout, window decor, etc?

If so, that kicks so much a$$.  Loving linux more and more

---

### Post by ep2011 on 2007-05-13
> **johnnyphive said:**
> Will that give me the same effect as doing a clean studio install?

If i don't like it, how hard is it to uninstall?

sudo aptitude remove "packages you installed" and just change back the theme Using System -> Preferences -> Theme

> **johnnyphive said:**
> Even my current desktop layout, window decor, etc?

If so, that kicks so much a$$.  Loving linux more and more

If you installed your themes to .themes in your home directory, then yes, if not, you will need to reinstall them

---

### Post by johnnyphive on 2007-05-13
Again, I apologize for all the questions, but like i said, i'm learning.

Here's what i plan to do.

Reboot my PC with the Feisty install disc.

Reformat my / partition into 2 smaller logical partitions

Install feisty on one of those partitions

Reboot pc with studio disc and install to the 2nd new partition

This should give me 3 OS on my machine (XP which will stay intact, Feisty, and Studio)

My /home partition will not be touched in the reinstall process, so in theory, everything should stay the same when i reinstall.  Can i share this /home directory between the to Linux OSes?

---

### Post by Shibby73 on 2007-05-13
I can't wait to get home and attempt to install UbuntuStudio!

Couple of issues I think I need help with first though.

1) I don't have a DVD burner

2) I have WINXP running well and kinda need to keep it intact

3) I have an old and completely messed up install of Ubuntu on a partition that doesn't start-up, well it tries to but I get the blue and red screen saying things are all messed up and no GUI.

How do I install Ubuntu Studio in place of this older Ubuntu that doesn't work?  I have tried and failed with overwriting it with the live CD and fixing the old install, and I don't know even if I could get my hands on an UbuntuStudio DVD don't know that it will work
Can I erase just the Ubuntu partition so that is fresh and still dual boot successfully?

Any help is appreciated.

-Steve
[email]smorrea_nospam@stansgnosticus.net[/email]

---

### Post by johnnyphive on 2007-05-13
> **johnnyphive said:**
> Again, I apologize for all the questions, but like i said, i'm learning.

Here's what i plan to do.

Reboot my PC with the Feisty install disc.

Reformat my / partition into 2 smaller logical partitions

Install feisty on one of those partitions

Reboot pc with studio disc and install to the 2nd new partition

This should give me 3 OS on my machine (XP which will stay intact, Feisty, and Studio)

My /home partition will not be touched in the reinstall process, so in theory, everything should stay the same when i reinstall.  Can i share this /home directory between the to Linux OSes?

Sorry, should have asked if these were the right steps to take, rather than say thats what i was doing.

Is the above correct?

---

### Post by johnnyphive on 2007-05-14
For anybody else that comes across this thread, i bit the bullet and did the above mentioned, and guess what, all my settings were till intact.

Hope this helps anybody else that had my same questions.

---

### Post by Zero Prime on 2007-05-16
> **johnnyphive said:**
> For anybody else that comes across this thread, i bit the bullet and did the above mentioned, and guess what, all my settings were till intact.

Hope this helps anybody else that had my same questions.

And that my friend is the answer I've been looking for.

---

### Post by happy-and-lost on 2007-05-16
> **johnnyphive said:**
> For anybody else that comes across this thread, i bit the bullet and did the above mentioned, and guess what, all my settings were till intact.

Hope this helps anybody else that had my same questions.

Just in case anyone gets the wrong end of the stick regarding my suggestion, it's not the only way to install Ubuntu Studio, it's just a useful way of testing distributions without causing any harm to your working daily one :)

---

### Post by Vandorius on 2007-05-31
> **ep2011 said:**
> To "Upgrade" from feisty just run the 2 commands:

```
sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update

```

Then install the following packages with your favorite installer (apt-get, synaptic, aptitude, etc):

# ubuntustudio-desktop
# ubuntustudio-audio
# ubuntustudio-audio-plugins
# ubuntustudio-graphics
# ubuntustudio-video
# ubuntustudio-artwork
# ubuntustudio-gdm-theme
# ubuntustudio-icon-theme
# ubuntustudio-look
# ubuntustudio-session-splashes
# ubuntustudio-sounds
# ubuntustudio-screensaver
# ubuntustudio-theme
# ubuntustudio-wallpapers
# usplash-theme-ubuntustudio
# wired

Im quite a noob when it comes to repairing something in Linux. I wanted to try Ubuntu Studio the way above. It installed and everithng looked great. But i noticed comp is running a bit slower 3D runs slover and i cant run games anymore they just freeze. 

So i manually deleted the Ubuntustudio repository and went for feisty theme. But now it still isnt ok.

Is there anyone who can tell me what must i do to get my Feisty back without a lot of mess or reinstall?

---

### Post by gary0 on 2007-05-31
I back up all on to cd using aptoncd. When done reinstalling Ubuntu, pop the apt cd in the drive, add to repositories, and bam! You're back to where you were with your software. It's all there again. Magic.

I'm loving linux more and more. What would take me a couple of days to get windows back to my normal install setup, takes about an hour on Ubuntu. Love it.

Gary.

---

### Post by Vandorius on 2007-05-31
> **gary0 said:**
> I back up all on to cd using aptoncd. When done reinstalling Ubuntu, pop the apt cd in the drive, add to repositories, and bam! You're back to where you were with your software. It's all there again. Magic.

I'm loving linux more and more. What would take me a couple of days to get windows back to my normal install setup, takes about an hour on Ubuntu. Love it.

Gary.

Thanks for the ansver. But like i said im a noob and i wuld like to know where can i get aptoncd? Is that a software? and how do i do it when i found it? I really dont wanna mess things up right now.

Thanks for reply again.

---

### Post by Happy_Man on 2007-05-31
```
sudo apt-get install aptoncd
```

---

### Post by Cosme on 2007-06-01
For this kind of things I use VirtualBox (an open source virtualization solution). I test all I want and wen I am sure I do the partitioning. ;)

---

### Post by KillerBob-it on 2007-06-02
> **ep2011 said:**
> To "Upgrade" from feisty just run the 2 commands:

```
sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update

```

Then install the following packages with your favorite installer (apt-get, synaptic, aptitude, etc):

# ubuntustudio-desktop
# ubuntustudio-audio
# ubuntustudio-audio-plugins
# ubuntustudio-graphics
# ubuntustudio-video
# ubuntustudio-artwork
# ubuntustudio-gdm-theme
# ubuntustudio-icon-theme
# ubuntustudio-look
# ubuntustudio-session-splashes
# ubuntustudio-sounds
# ubuntustudio-screensaver
# ubuntustudio-theme
# ubuntustudio-wallpapers
# usplash-theme-ubuntustudio
# wired

Does this install the kernel low-latency as well?

---

### Post by Happy_Man on 2007-06-02
No, I don't think it does.

---

### Post by MetalMusicAddict on 2007-06-02
ubuntustudio-audio grabs the -lowlatency kernel. But only grab -audio, -video, -grapgics and -audio-plugins if you need it all.

Also you can just grab ubuntustudio-desktop and it grabs all the art. so if you just wanted the base system and audio packages you would do: **sudo apt-get install ubuntustudio-desktop ubuntustudio-audio**
[B][COLOR="Red"]
WARNING:[/COLOR][/B] ubuntustudio-desktop is set to conflict with ubuntu-desktop. This was needed because our system sounds package cant be installed alongside Ubuntu's.

---

### Post by KillerBob-it on 2007-06-02
Thank you. So I think I will install Ubuntustudio in a separate partition because I need a low latency kernel for real time audio applications.
How much disk space does it require?

---

