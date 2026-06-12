---
title: "Another live cd problem"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by robholt on 2007-03-13
Hi,
First post here, hoping to get some answers so I can seriously consider switching OSs from xp (before Gates decides to yank support for it to force me into Vista).

Problem: burned the live cd for Ubuntu 6.10 - it works on my Acer laptop (except for the wireless, which I understand is a no go with Broadband wireless) but it won't work on the desktop. Meaning: I'm getting the black screen after the boot screen when the OS loads from the cd. It doesn't crash, because I hear the music perfectly, but there is no screen. I tried loading the "safe graphics" mode but it still goes black after the loading bar completes it's task.

My system specs:  Intel e6600 C2D on a Gigabyte ds3 motherboard (intel 965 chipset), 2 gigs of ddr2 667 ram, 250 sata hd, audigy2 sound card, ati 1900xt video card, internet through belkin router and a 20.1 wide screen benQ lcd. 

I know there is a problem with ati x series, as I've read plenty about them. How do I make it work for the live cd? I don't want to install Unbuntu on a dual boot unless I can tell that it will work with my hardware. I don't want to put it on my laptop because I need my wifi connection for the internet.  Oh, I tried this workaround:  [http://ubuntuforums.org/showthread.php?t=379807]("http://ubuntuforums.org/showthread.php?t=379807") but all I got to was an empty box with editing options - there wasn't anything listed.

Do I have to install it before I can get it to work?

---

### Post by dstew on 2007-03-13
Here is one thought:

[http://www.ubuntuforums.org/showthread.php?t=375527](http://www.ubuntuforums.org/showthread.php?t=375527)

---

### Post by robholt on 2007-03-13
Hey, thanks for the reply.... 
I tried that solution but I still got the same blank screen (not sure I typed ide=nodma in the right place).
I kinda think its my ati x1900xt that is causing the problem as the system doesn't really freeze. I hear the opening music through my speakers and the cd is still be accessed, so it is loading the OS, but with no image.

---

### Post by mikewhatever on 2007-03-13
I'd suggest trying Alt+Ctrl+F2 to get you to console, then > sudo nano /etc/X11/xorg.conf
check what driver is loaded in the device section, try a different one, ati or vesa, save, exit and type startx.

---

### Post by robholt on 2007-03-13
Thanks for the suggestion but, when I hit ctrl+alt+f2 after the OS loads (I'm listening to the opening music) I get a garbled screen of greeen and purple checkered boards. 
I tried doing the Sudo nano command after doing the break=bottom thing under f6 but it told me there was no such directory. 

Is it beginning to look like that there is no way to run a live cd with an ati x1900xt video card?

---

### Post by robholt on 2007-03-14
Wednesday morning bump.

Okay, from reading some of these posts, it would seem that I have a problematic video card - ati 1900xt, and maybe the motherboard is a problem - gigabyte 965p - ds3. I tend to think it's the former as I do get into the desktop (I hear the intro music) but, with no video. I doubt the fact that I have a wide screeen lcd with a native resolution of 1680 x 1050 has anything to do with it....

Any more suggestions on how to get the live cd to work?

 I failed to mention that I tried SimplyMepis rc1 also and it won't even load into desktop. It goes so far and then starts to post that it can't find something in the /etc/x11/ section - something with the number 5 in it. It will keep repeating this message as a scroll on down the screen into ad infintum.

---

### Post by robholt on 2007-03-14
another bump.

Hope 3 hours isn't impolite to bump a post. I guess I need to come to a determination if this rig is going to work or not.
Thanks in advance.

---

### Post by dstew on 2007-03-14
My only thoughts now are try a different live CD, like Dapper 6.06. I do not have any reason to believe it would work, thought.

You could also just install an ubuntu distribution using an alternate install CD, and then try to get the graphics card to work after that. You would be able to install drivers.

---

### Post by ravis_31 on 2007-03-14
having a similar problem,read this [post]("http://ubuntuforums.org/showthread.php?t=382140")
i have a atix700 and i faced the same problem,try the alternate cd(link posted in the other thread)it started up for me but had to abort due to config issues.

travis

---

### Post by dstew on 2007-03-14
What config issues led you to abort the installation? Was it the keyboard thing?

---

### Post by shultzjr on 2007-03-14
To all the people having video problems, the server version of Ubuntu does not load the graphics interface.  After loading the server version, then load the graphics interfaces from the command line separately making sure you configure for your viideo card.  That method should work.

later.....

---

### Post by robholt on 2007-03-14
okay, I guess what I surmise from these posts is that I will need to use the alternate cd and do an install on my hard drive in order to get the ati card to keep from going to a black screen.
I guess I can do this but I'm worried about encountering problems with installing on a separate partition on my hard drive and then having issues with the motherboard or with the boot loader, and then having to re-install the Windows OS again.

The reason I'm interested in trying Linux is that I was getting tired of situations where something happens to a piece of hardware on my rig (had to replace the mb in the last 6 months, had a bad flash prior to that) and i had to reload windows.  I end up having to talk to some person in India who interrogates me as to how many computers I have loaded my xp on before they give me another license number to reactivate it. I really want to own my computer and the OS on it, and not feel like I'm "renting" from the richest man in America.

---

### Post by ravis_31 on 2007-03-14
this [link]("http://users.bigpond.net.au/hermanzone/p3.htm") might get you through the installation process

travis

---

### Post by robholt on 2007-03-14
Thanks, just what I need. It shoulld help a lot!

---

