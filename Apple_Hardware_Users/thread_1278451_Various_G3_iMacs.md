---
title: "Various G3 iMacs"
date: 2009-09-29
forum: Apple Hardware Users
---

### Post by HaaiianHippie on 2009-09-29
Aloha all!

I supervise an Apple lab at a small private university.  Over the years, I've accumulated no small number of computers whose only sin is not being new.  

My current project is to try and find homes for about a dozen G3 iMacs.  They span a few years of productions, and include processor speeds of 333, 350, 400 and 600 MHz.  HD sizes range from 6 to 38 GB.

My first approach was to load them all with OS 10.3.9.  I've had some issues with the older machines, though... before I can install OS X of any flavor, I need to run firmware updates.  However, all of those machines had OS 9.1 installed before I came around, and to do the firmware update, I need to backgrade them to OS 8.  Which I don't own.

So, as an alternative, I was contemplating putting some flavor of Linux on them all.  I have Ubuntu on an old PC laptop and I rather like it, so that was my first choice.  I located and downloaded 9.04 for PowerPC yesterday.

But before I launch down this path, I wonder... am I doing the right thing?  Will I have an easier or harder time finding a productive home for this older technology with Ubuntu?

Mahalo!

---

### Post by rjcalifornia on 2009-09-29
Well, hello there! 

Ubuntu is the right technology for those old apple computers.

I recommend installing to the 333, 350, 400 Mhz Machines Xubuntu. This one is "less heavy" on those machines.

For the 600 Mhz machines, try Ubuntu or Kubuntu.

oh yeah, what is the amount of RAM that each machine has?

---

### Post by HaaiianHippie on 2009-09-30
The oldest machine currently has only 32 MB RAM, but I have chips on hand to upgrade it.  I've just not had the time to undertake that fairly respectable construction project.

The others range from a low of 256 MB to a high of 640MB and include some unusual increments (320, 384, 512) that resulted from adding RAM in a "whatever is on hand" approach a few years ago.

---

### Post by B_Free on 2009-09-30
Hello
You probably should go through some pages of these posts. You will find constant problems with the monitor sizes, sound, etc. Any variety of Ubuntu will not Live install on an iMac G3. You will have to be proficient in the use of the terminal and UNIX commands. This is nothing like installing Mac OSs. Ubuntu gives me hope to continue using my Macs (I have many). It is not easy. Installing on an Intel machine is a breeze. Not a PPC. I do have another discussion at [http://ubuntuforums.org/showthread.php?t=1242108&page=4](http://ubuntuforums.org/showthread.php?t=1242108&page=4). Check out more of the postings to get an idea of what is involved.

---

### Post by rjcalifornia on 2009-10-01
well, if the 600 Mhz has 512-640 of RAM, you can try Kubuntu. I have a guide somewhere around here which will help you in the install process. It covers a lot of stuffs, even the screen resolution problem.

Also, for those ones, you can try Ubuntu. It is great, not my favorite but it's a Great operating systems. There a guide from someone else around here on how to install ubuntu. Better than mine, with more feedback.

For the 300/400 Mhz I strongly recommend installing either Xubuntu or Debian Lenny. Even if those have 512 of RAM, another os will be kinda slow. For taking advantage of the hardware, I recommend Xubuntu. Lightweight and covers your needs. 

If you need help installing any of these, let us know :D

---

### Post by oswaldkelso on 2009-10-01
Due to your low ram you really need to in stall ubuntu alternate and build a system. If Ubuntu has lxde add that for a full light desktop.  [http://lxde.org/](http://lxde.org/)  

If you want the easy option the debian lenny xfce and lxde CD covers all bases. You can run it on 128mb but it would be painful. I'm writing this on a 333mhz 256mb imac with lxde and it's very usable. It's even more so with blackbox and rox-filer but a bit more work. 

[http://cdimage.debian.org/debian-cd/5.0.3/powerpc/iso-cd/debian-503-powerpc-xfce+lxde-CD-1.iso](http://cdimage.debian.org/debian-cd/5.0.3/powerpc/iso-cd/debian-503-powerpc-xfce+lxde-CD-1.iso)

---

### Post by rjcalifornia on 2009-10-01
> **oswaldkelso said:**
> 
If you want the easy option the debian lenny xfce and lxde CD covers all bases. You can run it on 128mb but it would be painful. I'm writing this on a 333mhz 256mb imac with lxde and it's very usable. It's even more so with blackbox and rox-filer but a bit more work. 

[http://cdimage.debian.org/debian-cd/5.0.3/powerpc/iso-cd/debian-503-powerpc-xfce+lxde-CD-1.iso](http://cdimage.debian.org/debian-cd/5.0.3/powerpc/iso-cd/debian-503-powerpc-xfce+lxde-CD-1.iso)

How come that you didn't post this before? I think I'm gonna install this on my old faithful ibook G3....

I'll download this tonight... Thanks!

---

### Post by imacQ on 2009-10-06
Okay, I'm late to the party; however...

FYI you don't need to downgrade to OS 8 to run the firmware upgrades. The iMac G3 firmware upgrade is run from OS 9.1 or 9.2. See this: [http://support.apple.com/kb/HT3036](http://support.apple.com/kb/HT3036). If you want to stick with OS X on the slot loaders, get one install just right, and then on the firewire iMacs use Carbon Copy Cloner to copy bootable clone to the others. Only the 350 and the lowly tray loader 333 have no firewire. If you've got a G4 with a DVD drive, you can install Tiger via firewire and target mode. Tiger runs well with 512 ram.

---

