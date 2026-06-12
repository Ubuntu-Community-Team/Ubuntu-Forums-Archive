---
title: "Ubuntu doesn't work"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by waste301 on 2007-12-09
I've been trying to get ubuntu to boot, and my PC locks up no matter what I try.  Help please, I am about to give up.  It won't boot from the disk or any other way, it just locks up with a cursor blinking.

---

### Post by Hobo Joe on 2007-12-09
Could you give a little more detail on what is happening? When does it do this? Have you checked your CD etc.

---

### Post by waste301 on 2007-12-09
> **Hobo Joe said:**
> Could you give a little more detail on what is happening? When does it do this? Have you checked your CD etc.

When I boot to that drive, it locks up.  It goes to a cursor blinking in the upper left corner.  When I try to install, it does the same thing.  The only way I can get an OS up, is to boot into windows.

---

### Post by Dapilot1 on 2007-12-09
Yeah that happened to me too. Sadly the way I got around it was by removing the video card, a GeForce 2 MX200, and using the on-board graphics. I don't know why the card didn't work for me, but it has worked fine for some.

---

### Post by CDL-WarChilde on 2007-12-09
What hardware are you using?  Motherboard, video card, processor, etc...

With Ubuntu 7.10 I would be surprised if it was a driver issue.

---

### Post by waste301 on 2007-12-09
Is there a way to post all my devices?  Its a dell I ordered, not a PC I built.

Ubuntu worked fine for a while.  Now it will not load. I installed using the alternative text CD, since the live CD was causing problems.

I've had no problems for a month or so.  Now, when the GRUB OS loader appears, if I select any ubuntu OS, repair or otherwise, it simply locks up, whether I use the CD or not.  

I don't even know how to uninstall ubuntu and reinstall on that drive.

---

### Post by waste301 on 2007-12-10
Hello?

---

### Post by tyggna1 on 2007-12-10
I've had similar problems on my wife's computer--only the alt CD would work.  If you can get that to work, poke around the alt CD for the recovery environment, and run an lspci.  That'll give you an idea of all the hardware on your computer (in a very technical readout).  More valuable to me would be the answer to this:
How much RAM is in your computer?

---

### Post by GSF1200S on 2007-12-10
> **waste301 said:**
> Hello?

Ive never tried this, but what about a repair install from the Alt CD? You said you cannot load "even from the cd..." Does this mean you cant even get to load an alternate CD to where you can select anything, or does it mean if you select the "exit and boot" command it fails to load Ubuntu?

**EDIT** As said above, and im not sure, but it may be a recovery console. At least from there you could post the contents of your bootloader, and we can go from there.

---

### Post by waste301 on 2007-12-10
I boot the alt CD, and get the menu.  Whatever I select though, tries to run and it either goes to a blinking cursor in the corner of my screen, of runs a list of commands, and then locks up in the middle.

At this point, I'd be satisfied with removing ubuntu, but I don't even know how to do that.

---

### Post by tyggna1 on 2007-12-10
press ctrl alt f1 while it's loading to get to a command line.  from there, you can run any command you want.
fdisk (remove)
aptitude (see if anything is broken in Ubuntu)
dpkg-reconfigure (fix certain packages)

---

### Post by GSF1200S on 2007-12-10
> **waste301 said:**
> I boot the alt CD, and get the menu.  Whatever I select though, tries to run and it either goes to a blinking cursor in the corner of my screen, of runs a list of commands, and then locks up in the middle.

At this point, I'd be satisfied with removing ubuntu, but I don't even know how to do that.

You could use another Linux's liveCD, well say OpenSuSe or Fedora and use the partitioning agent to wipe the partition and reformat in NTFS...  This seems like a hardware problem.. Try another distro and see if it happens to go any farther. If not, you can get a partitioning agent and install it in Windows, and do the formatting from there.

---

### Post by iatpia5 on 2007-12-10
I just spent  some time writing a thread and by the time I was done, this one had appeared on top of mine and wate301 seems to have a problem similar to mine. The diffirence with me is that I never managed to install in the first place, just got that blinking cursor in the top left corner after selecting install or run live cd. As I mentionned in my thread, I got the same thing with a kubuntu live cd I downloaded also from softpedia and a xubuntu 7.04 live cd I got from a magazine. The ubuntu live cd did install flawlessy however as a virtual machine on vmware in windows vista. I have a laptop with intel core 2 duo t7250 2gig ram intel graphics mobile intel(R) 965 Express chipset family (I don't know what any of this is BTW).

I probably shouldn't be mentioning this in waste301's thread but if anyone has an idea what this is please let us know. Thanks so much.

---

### Post by GSF1200S on 2007-12-10
> **iatpia5 said:**
> I just spent  some time writing a thread and by the time I was done, this one had appeared on top of mine and wate301 seems to have a problem similar to mine. The diffirence with me is that I never managed to install in the first place, just got that blinking cursor in the top left corner after selecting install or run live cd. As I mentionned in my thread, I got the same thing with a kubuntu live cd I downloaded also from softpedia and a xubuntu 7.04 live cd I got from a magazine. The ubuntu live cd did install flawlessy however as a virtual machine on vmware in windows vista. I have a laptop with intel core 2 duo t7250 2gig ram intel graphics mobile intel(R) 965 Express chipset family (I don't know what any of this is BTW).

I probably shouldn't be mentioning this in waste301's thread but if anyone has an idea what this is please let us know. Thanks so much.

Try another distro's LiveCD and see if you have the same problem. What makes Wate301s so odd is that it just stopped working...

---

### Post by iatpia5 on 2007-12-10
U mean something other than ubuntu, kubuntu xubuntu etc. Like fedora? Or does that refer to getting ubuntu from a different place? BTW thanks for the speedy reply.

---

### Post by iatpia5 on 2007-12-10
OK so I tried the alternate cd and I got the exact same thing: ubuntu screen came up, chose install in text mode and I got the eternal black screen with the blinking cursor on the top left corner. The new thing is that after I shut off the computer and rebooted I got this message :"BOOTMGR is missing Press Ctrl+Alt+Delete to restart" . When I do I get the same exact message. So I cn't even get to vista now! I will have to boot from cd and restore it I guess. Any other suggestions are welcome still but I think I might give up soon! Thanks for all the help everyone!

PS I copied this message from my original post just to follow up in here also.

Update: this is hilarious: I tried the fix boot problem from the boot cd of vista and it gave me the the classic windows message:" Windows can not fix the problem. Sending more information to microsoft may help find a solution. Would you like to send this information to microsoft?" (translated from greek)
I don't even have an operating system up, never mind an internet connection and they give me this! Reminds me why I want to get rid of windows in the first place.

---

