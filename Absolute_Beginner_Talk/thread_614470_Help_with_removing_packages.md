---
title: "Help with removing packages"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by G2GTech on 2007-11-16
Hello all,

I've recently converted from Windoze 2k Pro after being sick of the Microsloth forced upgrade tactics (amongst others).  I really like what I've seen so far of Gutsy, but I'm having a problem installing it.

The installation gets up to 89% and says "Checking for packages to remove..." and locks up.  Did I do or am I doing something wrong?  Keep in mind that this is my first foray into the wide world of Linux.

Here are the specs of my system:
Epox EP-8KDA3+ motherboard
AMD64 3200+ processor
2GB DDR400 RAM
80GB SATA Hard drive (partitioned to 20GB main, 1GB swap, and the rest storage space)
Sapphire Radeon X1650 256MB DDR2 AGP Video Card

---

### Post by Inxsible on 2007-11-16
to state the obvious, have you give it enough time to complete?

Since you are in the midst of installation, i would highly recommend having a separate home partition. it will save you a lot of grief later on.

you can also have a look at this link for the installation procedure and make sure you are doing everything right

[www.psychocats.net/ubuntu/installing](www.psychocats.net/ubuntu/installing)

---

### Post by G2GTech on 2007-11-16
Thanks for the link.  I checked the site, and it looks like I'm just a bit before the last screenshot.

The computer has been cranking for over two hours now, with no further progress.  To make my partition purposes clearer, here are the partitions I'm using:
20GB boot partition (ext3, mountpoint of /target)
1GB swap partition (SWAP)
54.5GB files partition (ext3, mountpoint of /target/user)

Any help would be greatly appreciated.

---

### Post by Inxsible on 2007-11-16
> **G2GTech said:**
> Thanks for the link.  I checked the site, and it looks like I'm just a bit before the last screenshot.

The computer has been cranking for over two hours now, with no further progress.  To make my partition purposes clearer, here are the partitions I'm using:
20GB boot partition (ext3, mountpoint of /target)
1GB swap partition (SWAP)
54.5GB files partition (ext3, mountpoint of /target/user)

Any help would be greatly appreciated.so you have no partition mounted at / and /home ?

you cannot install ubuntu without at least having a / (root) partition
Change the /target to / and make it about 10GB. Make another partition mounted on /home about 15-20 gb,  1 gb swap and the remaining you can mount at /target/user (or whatever you like at that time)

---

### Post by G2GTech on 2007-11-16
Hello all,

I've run the ram tester for 48 cycles, and I was about to start pulling hairs due to the time it was taking.  It ran for 19 hours, and I did find out that I only have 1GB RAM.  Could this be the problem?

The root folder is called "/", but when viewed in the Ubuntu Live User environment it appears as "/target".  After running the memtest86+, I tried again to install (this time without internet access to remove that possible problem location), and it's still hanging at "Checking for packages to remove..." at the 89% mark.

The computer is not locked up, as I can still move my mouse and activate other programs in the live environment.  I really want Ubuntu on my system, but desperation is setting in and I'm about ready to go back to the dreaded Windoze 2k environment, which ran without a problem.

Any suggestions?

---

### Post by kevink10 on 2008-01-27
Did you ever get around this problem?  I am having a similar problem.  My computer gets stuck at the 89% point and never wants to finish.  Let me know if you have any ideas.

---

### Post by teratakis on 2008-03-17
> **kevink10 said:**
> Did you ever get around this problem?  I am having a similar problem.  My computer gets stuck at the 89% point and never wants to finish.  Let me know if you have any ideas.
I have the **same problem** with a** Intel 86x64 platform**, regardless of the language :
[LIST]
[*]"Checking for packages to remove" 89%
[*]"Vérification des paquets logiciels à supprimer" 89%
[/LIST]
(However the Ubuntu i86 CD installs well on i86 platforms.)

---

### Post by teratakis on 2008-03-18
[COLOR="Blue"]**[SIZE="4"]Solution[/SIZE]** ( workaround ) **[SIZE="3"]allowing the installation to complete[/SIZE]**.[/COLOR]
**Abstract **: kill «unnecessary» processes.
**Method**.
1.** [COLOR="Blue"]launch a command window[/COLOR]**, this way :
[LIST]
[*] if Ubuntu in French :   Applications ... Accessoires ... Terminal
[*] if Kubuntu in English :   K-Menu ... System ... Konsole - Terminal Program
[/LIST]

2. [COLOR="Blue"]**Demonstrate the installation program takes 100% of CPU**[/COLOR]
[FONT="Courier New"]ubuntu@ubuntu:~$** [COLOR="Blue"]top[/COLOR]**
PID  USER ........... %CPU .... COMMAND
**9562** root ........... ** [COLOR="Red"]100[/COLOR]** .... **ubiquity**[/FONT]
Stop this display with Ctr-C, or open another terminal window.

3. [COLOR="Blue"]**Find the cascade of processes**[/COLOR]
[FONT="Courier New"]ubuntu@ubuntu:~$ [FONT="Fixedsys"][COLOR="Blue"]ps -edf | sort -n | grep ubiq[/COLOR][/FONT]
root      **9562  **9554 0 13:52 ?  00:16:16 /usr/bin/python /usr/lib/ubiquity/bin/ubiquity kde_ui
root     16425  9562 0 13:57 ?  00:00:00 /usr/bin/perrl -w ...
root     16427  9562 0 13:57 ?  00:00:00 log-output -t ubiquity ...
.../...
root     [COLOR="Red"]17270 [/COLOR]17269 0 14:08 ?  00:00:00 [COLOR="Red"]/bin/sh /usr/share/ubiquity /check-kernels[/COLOR]
root     [COLOR="Red"]17290 [/COLOR]17270 0 14:08 ?  00:00:00 [COLOR="Red"]/bin/sh /usr/share/ubiquity /check-kernels[/COLOR]
root     [COLOR="Red"]17291 [/COLOR]17290 0 14:08 ?  00:00:00 [COLOR="Red"]/bin/sh /usr/share/ubiquity /check-kernels[/COLOR]
[/FONT]

4. [COLOR="Blue"]**Kill «unnecessary» processes**[/COLOR]
The processes [FONT="Courier New"] [COLOR="Red"]/bin/sh /usr/share/ubiquity /check-kernels[/COLOR] [/FONT]can be killed.
Just send them the CONT signal, until you see the installation resume.
[COLOR="Blue"][FONT="Fixedsys"]sudo kill -18 17291
sudo kill -18 17290[/FONT][/COLOR]

---

### Post by Crazy_Ivan on 2008-05-24
I also THOUGHT the install (Kubuntu i386 DVD) was locked up (@ 95% in my case) as there was no HDD or DVD LED activity but it just took a while (30 minutes w/ P4 1.6GHz/400MHz FSB, 1GB Rambus). There WAS numerous packages to remove (mostly language stuff) so just be patient...it's processing.

---

