---
title: "[SOLVED] On the dreaded vista... Need some advice"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by nathan1936 on 2007-12-21
Hey! Ok, this is my first post. I am a COMPLETE NOOB when it comes to ubuntu
[oh great, right?]
I have been on windows since I was a little kid, BUT I want to try it. 
So heres what I need.

1. Can someone show me how to get started? I want wireless internet, mp3 player, mozilla, and a basic text typer.

2. and I wanna know about playing windows games... I play starcraft, and java games such as runescape. Can I continue on ubuntu? What about flash?

2. How do the drivers work on ubuntu? can I use the windows ones? I have a wireless card in my laptop and I need to know if it will work. Its a 3com wireless a/b/g card.

3. How does wireless connectivity work?

4. Is there a good, noob friendly version, WITH some bells and whistles? I want it to look nice, I dont have 3d support on my internal VGA video card, but I still want something that looks nice. [im on Vista now...]

So, now specs:
I have a compaq evo n600c, 1.2ghz processor, 1gb ram, 30 gb hd.
I read that I may need a firmware flash on my mobo BIOS? Please explain...

All the help will be greatly appreciated, so thanks in advance. The sooner I find out about ubuntu, the sonner i will be up and running

Vista doesnt support my internal speakers very well and im tired of xp so im willing to try something better.
So im waiting :popcorn:


Thanks again! and happy holidays everyone

---

### Post by shae on 2007-12-21
1) Firefox is the default internet browser, gedit is roughly equivalent to notepad, and openoffice.org writer is used like word.  Now your wireless internet could be set up automatically needing you only to enter the encryption passkey.  A good mediaplayer is installed by default that somewhat reminds me of iTunes without the store.  To play MP3s you need to install codecs.  Simply install the package "ubuntu-restricted-extras" in synaptic and it should take care of java and codecs.  Usually it would take care of flash too but there is a post that explains how to fix that clearly.  The first thing you should do is boot to the live CD and try out your wireless and any other hardware.

2) Runescape should work as normal from the browser and older games such as starcraft, warcraft, diablo, should run through wine pretty well.  There are posts about installing these games here and at the wine application database.

3) Once set up it works similar to windows.  You might have to set up ndiswraper if there are no linux-native drivers for your wireless card.

4) I would start off with ubuntu simply because it has more polish. 

I doubt you need to flash your BIOS.  About the only thing you will have to do is tell BIOS to check if the CD in the drive is bootable.

More importantly: BACKUP BACKUP BACKUP before you try anything.

---

### Post by p_quarles on 2007-12-21
1. All of those things are available for Linux.

2a. I believe that Starcraft will work with a program called Wine, which allows you to run Windows applications. Java games should work fine. Flash is easy to install.

2b. Drivers for many hardware components are included in the kernel itself. Linux is a monolithic kernel, whereas Windows uses a microkernel. Basically, this means that separate drivers are often not necessary in Linux, with some significant exceptions. According to [this]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCards3com"), 3Com wireless cards are well-supported by the Linux kernel. 

3.Once you've got your wireless card working, pretty much the same as in Windows.

4. Ubuntu's a good choice. You might also take a look at other user-friendly distros like Mandriva and OpenSuSE. 

As for your specs, yes, that's more than enough for any Linux distro. I doubt you'll need to flash your BIOS, so don't worry about that until you've actually run into problems.

---

### Post by nathan1936 on 2007-12-21
wow thanks for the quick reply! 
But yea,
what version of ubuntu should I get? also what is the live cd?
I want to install ubuntu to my hd, not run from a cd... Is the cd like a testing/debugging version? 
again, I want it to be noob friendly... so explain
Thanks again

---

### Post by p_quarles on 2007-12-21
The live CD allows you to try it out without installing, but it also gives you the option of installing it to the hard drive. Since you're brand new to this, I'd recommend just going with the standard Ubuntu 7.10 live CD. This will allow you to test hardware compatability before installing, and is very easy to follow during the installation process itself.

---

### Post by Skidpad on 2007-12-21
Welcome.

A LiveCd is the entire OS burned as an .iso image file onto a cd.  It allows you to run the OS and try it out, without actually installing anything.  It runs within your ram, and is fully functional.  I know, its a strange concept to folks like myself who came here from a Windows background.  I was blown away by it, tried it out off and on for a week or so, and then installed it.  That was a year ago.  Me likes.  :)

You can get the newest version of Ubuntu (Gutsy Gibbon, also known as 7.10) [Here]("http://www.ubuntu.com/getubuntu/download")

---

### Post by nathan1936 on 2007-12-21
Hey! are there any good torrent programs for ubuntu?
Like I really enjoy Utorrent, but idk if it is ubuntu compatible

---

### Post by barbedsaber on 2007-12-21
just keep in mind tht when you run it from the live cd, Ubuntu will run really really really slowly. This is no representation of ubuntu's speed, this is becuase pretty much every hard drive even the really slow ones, will work faster than even the fastest cd drives. so if you get a live cd and it takes 4 minutes to boot, don't just think linux is slow, because it sure as hell isn't.

---

### Post by barbedsaber on 2007-12-21
> **nathan1936 said:**
> Hey! are there any good torrent programs for ubuntu?
Like I really enjoy Utorrent, but idk if it is ubuntu compatible

frost wire is what I use, it uses the same network as limewire.

---

### Post by p_quarles on 2007-12-21
> **nathan1936 said:**
> Hey! are there any good torrent programs for ubuntu?
Like I really enjoy Utorrent, but idk if it is ubuntu compatible
Azureus and Ktorrent are both available from Add/Remove programs. Another favorite is Deluge, which you can find via Google (the developer is an active participant in these forums, btw).

---

### Post by nathan1936 on 2007-12-22
Sweet Ill make sure to try that out

---

### Post by mike555 on 2007-12-22
---   just a note , when you decide to install be careful, pick the manual partition option and be sure not to wipe out your Windows install, (unless you want to ) ....

---

### Post by Sef on 2007-12-22
Before installing, read up about Ubuntu on [Psychocat's site]("http://www.psychocats.net/ubuntu/index.php").

---

