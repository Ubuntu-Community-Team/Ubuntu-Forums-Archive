---
title: "Installing Ubuntu on a Dell Dimension 2400"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by gconeen on 2007-03-17
Hi, I just started using linux, and I wanted to install it on my family's crappy dell to try to spiff it up. As the topic says, it's a Dell Dimension 2400. I've installed Ubuntu on 2 machines without a problem so far very easily, but I really have no idea what I'm doing with this Dell. Any help would be appreciated, thanks.

---

### Post by Josey on 2007-03-17
What is the problem exactly?  Is it not booting off the cd?

---

### Post by gconeen on 2007-03-17
Well, I'll boot from the CD and I'll get the initial menu, and choose to start up Ubuntu, and then it'll just sit at a black screen with a mouse cursor in the middle forever.

---

### Post by oilchangeguy on 2007-03-17
please advise the specs of your machine. and the version of ubuntu you're trying to load.

---

### Post by Josey on 2007-03-17
That is known to happen for a long time depending on how fast the machine is.  How long have you left it sit at that screen?

---

### Post by gconeen on 2007-03-17
The Dell has a Pentium4 2.6GHz processor, 256MB RAM, Intel i845e/g/pe/ge chipset, and 128MHz FSB. And I'm installing the latest version of Ubuntu Desktop 6.10.

---

### Post by gconeen on 2007-03-17
> **Josey said:**
> That is known to happen for a long time depending on how fast the machine is.  How long have you left it sit at that screen?

It's been stuck for around 45 minutes.

---

### Post by oilchangeguy on 2007-03-17
not sure why it's not working. the 256mb of ram is probably the min for it to load. but it should still load. also you'd be doing the computer a favor if you can add more ram. given your cpu's specs the motherboard probably supports 1gb, 512x2, of ram. and is this the same disc you've used to load ubuntu on other computers?

---

### Post by gconeen on 2007-03-17
Hmmm, dang. Do you think Kubuntu or any any other distro (something my parents can just use for web browsing, and checking email) would work?

---

### Post by oilchangeguy on 2007-03-17
kubuntu is the same as 6.10, just uses kde, instead of gnome. use xubuntu.

---

### Post by gconeen on 2007-03-17
ok, thanks for all you're help. hope I don't have to come back with more problems.

---

### Post by drushr on 2007-04-10
I had the same problem on my Dell Dimension 2400 when I was booting from the live CD.  I installed more memory and the problem went away.  I only had 128mb of memory and I went to 1GB.

---

### Post by Sunflower1970 on 2007-04-10
If you haven't tried it yet, try the alternate CD. My laptop, when I got it, originally had 256 MBRAM and took forever to do anything with the liveCD install. I switched to the alternate and it installed just fine. (Bout a month later I upgraded the RAM to 1GB)

---

### Post by KClaisse on 2007-05-22
I am interested in how successful you were with that machine. I too have a 2400 and it is currently running FC6 (with gnome). It has had many problems so I am hoping that Ubuntu will work better with it. Any information you have would be great.

-Kyle

---

### Post by Terl on 2007-05-22
I had the same machine.  I was only able to get it loaded when I upped the RAM.  That 256 you have is being used by the onboard graphics also so it is not really 256.  I kicked mine to 512 and things were much better.  I would advise to at least double the ram or move to Xubuntu as it has a lighter weight desktop.

---

### Post by KClaisse on 2007-05-22
We have 512 in the machine right now, so thats a plus. How is the compatibility with the hardware? Will I have to find drivers and install them, or will Ubuntu find them right away?

---

### Post by Terl on 2007-05-22
> **KClaisse said:**
> We have 512 in the machine right now, so thats a plus. How is the compatibility with the hardware? Will I have to find drivers and install them, or will Ubuntu find them right away?

What do you have for internet?  I was using cable modem and Roadrunner and had no issues at all.  If you are on dialup it will depend on the modem.

The on board intel graphics should work well as it is supported under linux.  Everything else was just fine.  On my 2400 I have actually had FreeBSD, Slackware, SuSe (7.2 version), Debian, Ubuntu, Vector, and Zenwalk.  Only Gentoo had issues and it was resolved.  (Yep, I've been trying a few :) )

The nice thing is you will have a good idea how it will go when you try the live cd.  Just remember the live cd is slower than an actual install will run.

---

### Post by KClaisse on 2007-05-22
Thanks for the info! Looks like i'll be installing Xubuntu today. And I think my connection will be fine:

[img]http://www.speedtest.net/result/129427342.png[/img]

:D

---

### Post by Terl on 2007-05-22
It sure will!  Have fun!  Let us know how it fares.

---

### Post by ashishagrawal on 2007-08-30
so there is no way that ubuntu can be run on these kinds of pc's smoothly but people on this forum say that they can run it pretty smoothly with same configuration. i also want to run ubuntu instead of kbuntu or xubuntu.

really will appreciate the help regarding the configuration and install for the dell dimension 2400 series pc with 25mg ram, 80 gb hard drive and 2.4 Ghz celeron processor.

---

### Post by TeaSwigger on 2007-08-30
Hello,

I've installed on an old Dell Dimension 2350, the preceeding and inferior model to the 2400. It has 256mb memory with shared (built in) graphics, a lousy 1.6ghz Celeron processor that's absolutely owned by my older 933mhz PIII Dell 4100 (that's why I usually call it a Celery Processor) and one 30gb hard drive. So I'm here to report the lessons of the experiences to any interested in installing on such a unit:

- You can do it and it's absolutely worth it. Definitely preferable to trying to keep running Windows XP on it.

- You must use the Alternate CD, not the Live CD. Fear not: installing is still a snap.

- You may be well advised to disable the usplash. That's the logo with the loading bar that's (supposed to be) on screen while the system is booting up. This usplash may not work. You will know if you should do this when you try to boot: you get a blank screen and it may "hang" for a while or "stick" in a few spots. I haven't found a working fix if there is one yet. So for now here is what you can do to prevent this from being a problem and hanging up the boot:

*a) If it does boot, but the usplash didn't show up and/or it hangs during boot:*

Once booted, edit the file /boot/grub/menu.lst. What to do: you must disable the usplash in the "bootloader" (GRUB). This will mean that you will see text scrolling by on the screen as it boots instead of the fancy logo, but this is not a problem; the PC will now boot quickly and reliably this way. This is done by adding "nosplash" to the end of the kernel line. To illustrate, here is the relevant part from my /boot/grub/menu.lst:

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=76e09fab-480a-4964-9c26-8037e6369271 ro nosplash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault
```

Note the location of the word 'nosplash'.

How to do this:
There are three ways to do this. You can use a GUI kindly provided here, which lets you edit GRUB:
[http://ubuntuforums.org/showthread.php?t=228104](http://ubuntuforums.org/showthread.php?t=228104)

Or to use a GUI text editor open a terminal (or konsole if you are using kubuntu) and enter:
ubuntu:
```
gksu gedit /boot/grub/menu.lst
```
kubuntu:
```
kdesu kwrite /boot/grub/menu.lst
```
xubuntu:
```
gksu mousepad /boot/grub/menu.lst
```

Or to edit it right in the terminal, open a terminal (or konsole if you are using kubuntu) and enter:
```
sudo nano /boot/grub/menu.lst
```

Either route, add in the word **nosplash** at the end of the line as shown above, and only do that; please don't touch anything else in that file unless you know what you're doing.

*b) If it does not boot, instead hanging up indefinitely with a blank screen:*

Start or restart the PC however you have to. When first starting the PC you should briefly see a screen where you can select which version or system to start (which kernel, recovery mode, and windows if you are using a dual-boot with windows). If it goes to quick I think you can press the up or down arrow to catch it. Pick the recovery mode option and enter. This will start booting with a big long list of text scrolling on the screen, eventually stopping at a command prompt (something like root@mypcname:$ ). Now you can set it to disable usplash. Enter:

```
nano /boot/grub/menu.lst
```

Okeydoke, find the listing for the main linux kernel's regular boot. At the end of the kernel line, type in nosplash. Again, To illustrate, here is the relevant part from my /boot/grub/menu.lst:

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=76e09fab-480a-4964-9c26-8037e6369271 ro nosplash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault
```

Note the location of the word 'nosplash'. Save and when you return to the prompt, type reboot and press enter. Done. Now it'll boot quickly and reliably.

- Xubuntu is suggested over Kubuntu, and Kubuntu is suggested over ubuntu (Gnome), Best choice I've found is to install xubuntu and use Fluxbox as a window manager instead of Xfce, or perhaps IceWM. If you find those too strange and just not your style, then Xfce will do well enough. You might do well to install Fluxbox and/or IceWM; this way you can choose Xfce, Fluxbox or IceWM at logon so you can have it whatever way works for you for whatever you want to use the PC for that time. A nice flexible setup :) Ubuntu will run, it'll just be slower than the other options.

- You may have to instruct the PC to boot from the CD in order to install anything. To do this, press F2 right after starting the PC and seeing the Dell insignia. This will bring up a blue screen with various menus. Using the arrow tabs, work your way to the page that lists the boot order and, ta-da, change the list so the CDROM is first. Then save changes and exit (press F10). Restart with the ubuntu CD in the CD drive and you should be good to go.

Hope this is helpful to someone :)

---

### Post by ubun2dragon on 2007-08-31
I installed Feisty on a Dell 2400 2.4 celeron with 384mb ram with the video card sharing memory, several months ago, and had similar issues where the install would hang.  There were a few settings in the BIOS controlling the video card which I played around with, and I finally got it to work.  If I remember right, I reduced the video card memory to max 64mb, and once I did that Feisty installed without any other problems.

Ran fine under those configurations, but I only used it for surfing the net.  You may need to put in another 128mb ram, and if you have to do that, you'd be better off putting in 256mb, so you don't have to worry about the shared memory at all.

---

### Post by Clear_air on 2007-10-05
Yesterday I tried to install Ubuntu Fiesty Fawn on my old Dell Dimension 4100 with Windows ME. I had exactly the same experience as ubunt2dragon. I could install AbiWord, Mozilla Firefox and Mozilla e-mail but not Ubuntu.  After initially hopeful signs it would revert to a blank screen with immobile cursor. I left it installing overnight but it still showed a blank screen in the morning.The CD was that supplied by Canonical. 

I formatted the c: drive to delete all programmes and files, but the result was the same.

I downloaded [ubuntu-6.06.1-desktop-i386.iso] to a fresh CD and got pretty much identical results (I performed all the recommended checks on the download and the integrity of the disk).

The Dimension 4100 has the Pentium III processor and the Intel 815E system chip set, 256Mb RAM and 1GHz (I believe) clock speed.

Totally new to Linux so would be grateful if any advice is in plain text!:)

---

### Post by mvanwey on 2007-10-15
I'm also a noob. My wife has the same unit running XP. I can't wait to get Ubuntu on it!

I did Ubuntu 6.06 LTS on a Dell Optiplex 110. P3 667Mhz, 256 MB Ram.   I had to do the "alternate" install.  Would not play extra web content.  15+ seconds to load Open Office doc's.  Forget about video or games.  E-bayed a 1Ghz CPU & 512MB (2x256) RAM & a used 20 Gig Drive & used CD burner.  I'm only in for $45 even after shipping. Plays video, rips/burns CD's, USB thumb drive support, Web/Flash/Java is fine,  my kid plays educational games  on-line.  This is great!

Yours should really scream once it works. Try installing from the "alternate" CD, using the text based install.  Don't worry,  it's not terminal, It's still point & click, just very basic graphics.

---

### Post by imjscn on 2008-06-23
I'm planing to install a dualboot WinXP+Xubuntun on my Dimention2400 (originally 256 RAM, upgraded to 512, 80G). I read from another thread saying sometimes a slow down is due to out dated drivers. I checked on Dell's website, there's only one Urgent item(SmarktKey for USB booting) to update. There are lots of other recommended items, I don't know which one I need. I wish to know some suggestions on what are the drivers we'd better update? 
I see this thread is quite old, hope you guys are still around.
Thanks!

---

