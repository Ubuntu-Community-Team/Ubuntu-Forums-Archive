---
title: "Ubuntu 7.10 installation problem."
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by davischen on 2008-02-15
Hi, I have just downloaded the Ubuntu 7.10 Desktop CD version, and tried to install it on my computer.
But, After I selected "Start or install Ubuntu" it starts to load Ubuntu. after the loading bar goes to full, the screen flashes and i get such output
*Starting deferred execution scheduler atd                                                    [ OK ]
*Starting periodic command scheduler crond                                                  [ OK  ]
*Checking battery state.......                                                                         [ OK ]
*Running local boot scripts (/etc/rc.local)                                                       [ OK ]
"

after about 6 flashes, It outputs "The display server has been shut down about 6 times in the last 90 seconds.  It is likely that something bad is going on.  Waiting for 2 minutes before trying again on display :0."

And then  it just keep doing the retry.

The samething happened for "Start Ubuntu in safe graphics mode".
My graphic driver is ATI X1250, so i downloaded the "ati-driver-installer-8-02-x86.x86_64.run" and burned it on to a disc.
Then i selected "Install with driver update CD" and followed the instructions, but i still get the same result.

Anything I can do to solve that problem? Thanks.

---

### Post by Bubba64 on 2008-02-15
what is your distro from to gutsy.

---

### Post by emarkd on 2008-02-15
This is pretty common with some video hardware, including ATI.  Your best bet may be to install using the Alternate CD.  It's just an installer, no live cd, and it's text-based so it'll work on pretty much anything.  Then you can get your card up and going using the restricted drivers manager after it's installed.  If you want to go this route, you can get the CD from [http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)

---

### Post by davischen on 2008-02-15
Hi,
For the first reply, I downloaded from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

For the second one, thank you, I am downloading that. 

So if that works, and then I can still convert it to a graphic interface?

---

### Post by jr_herman on 2008-02-16
Hello Everybody,

WARNING: I AM A COMPLETE LINUX/(7.10) NEWBIE.

I hope I can double up on this thread. I've been searching this forums for a while and can not find the solution to whats happening with my machine.

Machine Specs:
AMD Athlon 64 Processor 3500+
2.21 GHz, 2.00 GB of RAM
ATI Radeon x700 PRO-256PCIE

Background: 
I DL'd 7.10 iso. I performed all of the pre-burn verification checks. I burned the iso as an image to the cd. The CD works okay so far. So when I reboot my system it will boot from the CD first. So Far So Good.

Problem:
No matter what option I choose. Start or Install, Safe mode, Check CD for defects, I get a black screen:confused:. It doesnt move flicker anything, My lcd monitor appears to be in sleep mode (power light is orange. 
--->In other forums I saw instructions to press CTRL+ALT+F1. Nothing happened.](*,).

Please help!

---

### Post by perce on 2008-02-16
> **davischen said:**
> 

So if that works, and then I can still convert it to a graphic interface?

It does a complete installation, only during the installation the interface will be text based, but still very easy to use.

 Warning: I've never installed 7.10 from the the alternate CD, but only 7.4. Here I'm assuming they behave in the same way.

---

### Post by davischen on 2008-02-17
Hi, I have used the alternate CD to install Ubuntu and it works fine now, thank you.

But now there is another problem, when I try to go to my orginal Windows XP, the computer reboots automatically.  However, I can still get into Safe Mode with no trouble.

So what should I do to fix it? Thanks.

---

