---
title: "Ubuntu 7.1 AMD64bit edition Install Problem: Busybox &amp; debian initramfs error"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by WhtCyphR on 2007-10-25
Ok, I'm an absolute newbie to Linux, so I always document my process in detail to hopefully get a good response to my issues on anything i'm doing.

1.) What I'm trying to do:
    1.1.) I'm currently running Vista Business and I'm trying to setup a dual-boot option for Ubuntu V7.1. and Vista. I'm trying to setup a Dev enviornment so I can
           begin to learn Ruby, ROR, Mongrel, and others on the linux/Ubuntu Platform.

2.) My Process thus Far:
   2.1.) Ok, I've Partitioned my drive accordingly:
           C:/ is currently operating with vista (20Gig)
           D:/ is currently unallocated space (15Gig)
           G:/ is my data partition to where I always install my vista applications (currently active and allocated as a separate partition= 65Gig)
           E:/ is my CD/DVD optical drive

   2.2.) I have downloaded the ubuntu-7.10-desktop-amd64.iso and extracted the containing files & Folders to a DVD
   2.3.) After Burning, I rebooted. Nothing different, and obviously no boot.mbr to reference.
   2.4.) I then looked at the files on the dvd and notice the "wubi-cdboot.exe" and run it, then reboot
   2.5.) Now I am able to choose to boot to either Vista or Ubuntu. (great, but not for long), I choose ubuntu
   2.6.) it runs a set of commands and then the Ubuntu Splash Loader screen comes up with the Orange loader bar
   2.7.) Now just when everything is looking good, It sends me to a command screen with the following:
                2.7.a) Busybox V.1.1.3 (Debian 1:1.1.3 - 5ubuntu7) Built-in shell (ash)
                         Enter 'help' for a list of built-in commands
                         (initramfs)
                2.7.b) at this point i'm confused becuase the install tutorial shows that I should be seeing a screen full of options that include "install"
                         so i press enter and recieve the following: "invalid command: bin/sh"
                2.7.c) I type help, realize i'm unfamiliar with the commands and type "reboot"

  2.8.) Decide to check out as many forums on Installing and Dual-booting and try a few things suggested such from the threads: [http://ubuntuforums.org/showthread.php?t=421588&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty%3B+job%20+control+turned+off](http://ubuntuforums.org/showthread.php?t=421588&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty%3B+job%20+control+turned+off))
[http://ubuntuforums.org/archive/index.php/t-442015.html](http://ubuntuforums.org/archive/index.php/t-442015.html)
[http://forums.debian.net/viewtopic.php?p=108981&sid=f86a4236249f683bedcded364b0b9938](http://forums.debian.net/viewtopic.php?p=108981&sid=f86a4236249f683bedcded364b0b9938)
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[http://ubuntuforums.org/archive/index.php/t-511972.html](http://ubuntuforums.org/archive/index.php/t-511972.html)
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

  2.9.) I'm now writing this post!

3.) My Problem:
  3.1.) if it isn't obvious by now, I can't get anywhere on install! I can't seem to find the information needed to get a work-around or solution.

4.) My Other Questions:
  4.1) Am I using the correct verision of Ubuntu for my system? (b/c i've tried the i386 version as well with the same results)
  4.2) Do i have to burn the iso a certain way other than just the standard way of extracting the contents and burning?
  4.3) Should I be modifying anything in Vista? or on the Ubuntu Disk?
  4.4) Am I just A Hopeless retard newbie trying to hard?! :) jk, we all know this answer.
  4.5) Can anyone please offer any experience and insight into my problem please? it would be greatly appreciated if you have the time.

5.) My Hardware:
      Gateway Laptop: Model MX7515
                                HDD: 100Gig: HTS541010G9AT00
                                CPU: Mobile AMD Athlon 64 Processor 4000+ 2.60Ghz
                                RAM: 1.534 Gig
                                Video: ATI Mobility Radeon X600: 256mb shared
                                DVD/CD: HL-DT-ST_DVD-RW_GWA-4082N

I hope this is enough information, if there is anything else I'm missing, please just ask, and I'll be more than happy to give my experience with this installation.

Thank you for reading this post and offering your thoughts.

---

### Post by speed145a on 2007-10-25
it sounds like you might be burning the iso incorrectly.

what tool are you using to burn?

if the tool is going to do the job correctly, I don't think there should be any "extraction" process.

the terminology is usually something like "burn image to disc"  
tools like Nero, UltraISO, and similar usually have a term like this or something like "make a bootable disc"

if you get the ISO burned correctly, it should bring up a splash screen when you insert the disc on windows, and if you reboot it should give you a ubuntu install screen.  this is assuming that you have your cdrom as the first boot device.

let me know if this help or if you need more

---

### Post by DennisMonague on 2007-10-25
I get the exact same thing.  I've run the tests as well and made sure that my burn was good.  I used NTI to create my boot disc. I have no idea what the commands mean after I type "help"

My computer is an acer aspire 5040 laptop.  AMD Turion 64, ATI Radeon Extress 200M, 2-512 Ram, 60 GB hard drive.  I have partitioned my drive as follows: 
C: Windows and all it's components 25 gb (ntfs)
D: Unformatted space 25 gb
E: Tranfer 8 gb (fat32)

I've used windows all my life and finally am fed up with their resource hungry, constantly updating, security fragile, weak, unstable system.  So when it comes to new I'm about as new as possible.

---

### Post by speed145a on 2007-10-26
congrats on taking the leap on dumping windows, it is a sometimes slow, but always satisfying endeavour.

help me out here... have you made sure that the cdrom is the first boot device?  
and when you insert the newly burned iso while in windows, does the ubuntu splash screen pop up?

---

### Post by WhtCyphR on 2007-10-26
yes, The CD drive is the first bootable device. In addition to your reply, when i mentioned the "extraction"  my proccess is as followes.

I'm am using PowerISO to view .ISO - 
I then simply open the .ISO in the app and then copy all the files within to my cd/dvd drive and then write to disk.

when i put the burned cd in the drive (without running the "wubi-cdboot.exe") it boots straight to vista. although if i run the "wubi-cdboot.exe" and restart I am then prompted with the option to choose Vista or Ubuntu. when I choose Ubuntu, the proccess described in my original post begins.

---

### Post by DennisMonague on 2007-10-26
Me too.  I opened into bios (f2) and set my cdrom as the first boot.  Mine does go to the first splash screen.  Now at this point if I hit "enter" I get:
hdc: error code: 0x70 ....
Buffer I/O error on device hdc, logical block 20XX
SQUASHFS error: unable to read page:
(it goes on and on and on but that's sort of the gist of it)
If I use the F6 key and add "acpi=off noapci" I get through to the second load screen and it seems to load.  It then kicks into a black screen that says:
Busy Box ...........
(initramfs)
(there is no errors noted at this point so I'm assuming that this is some sort of command line.  It also advises me to type help to get a list of commands)
Now at this point I started to do much reading and found a forum that sounded similar to my problem.  They used the "modprobe piix, exit" command.  I tried that and it seemed to get me past this point to the actual load screen.  My screen turned brown and the mouse pointer looked like a loading icon.  The screen flashed a bunch of times then i get this note that says something like "tried 6 times to load screen failed will try again in 5 minutes"  It then freezes (I left it for 2 hours and nothing changed).

---

### Post by anrichp on 2007-10-28
hey ppl 

i have exactly the same problem , i can only assume that the installation can not accure because i cant find the partition the wubi software was installed on

hope someone can help us 

thnx!!

---

### Post by nikef on 2007-10-28
Hi all,i have the same problem,but i update from fiesty fawn 7.04 :confused:

i can still get into gutsy by,clicking escape  @ boot and choose a different kernal

to the op,sorry i can not help you

---

### Post by WhtCyphR on 2007-10-28
Alright, I was able to get ubuntu to install. figuring out that it was a "burning" issue. (thanks for the tip speed145a, much appreciated). 

I ended up downloading UltraISO and opening the ISO and just selecting "Burn" which i found out will put a boot loader into the burn process automatically unless you de-select this option. Once I burned it and rebooted, i was able to see the "Start or Install" options. when you select this, ubuntu will load the drivers to run directly from the CD only. when the desktop loads there is a icon that says "install" and this will run you through the standard process of choosing the partition you with to install to. One thing I noticed (and hopefully i did this correctly) was that when i went to choose my partition to install onto, I just allocated all the space available on that partition. When i went to go to the next step it said that I have to identify a "Swap Space" for the memory. Ubuntu recommended a minimum of 256mb (which you have to identify as another partition then label it as "Swap" and not primary or boot) so I have the mentality of Well bigger is better and allocated a swap space partition of 1024mb (1gb). Followed through the rest of the prompts and rebooted to see the GRUB boot loader option screen with Ubuntu and vista then continued to boot into Ubuntu. It takes a little while to boot into Ubuntu like 5 mins (at least in my case. not sure if this is normal) and now it works just fine.

Although, I am having issues finding my wireless network. But I'm sure I'll be able to figure that out soon enough. Also, I noticed that Ubuntu offers some cool "Desktop Effects", but evidently my graphics card and hardware is not supported so I am unable to use this feature. This doesn't really bother me, but it would have been nice to see what the effects looked like.

Other than that, I'm good to go, and realized that it certainly was my initial "burn process" that was bringing me to my initial errors written in the original posts.

I hope this works for the other users that have mentioned the same issues.

Thanks for everyones help, and now its time to move onto learning all about Linux & Ubuntu!!!

---

