---
title: "A sad 7.10 start"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by Shevilie on 2007-10-17
I wanted to try to install 7.10 on my "old" computer... 
It contains 3ghz, a Radeon 9600 graficcard and a MSI motherboard....

First i tried with the desktop cd... I get to press Start and Install, but that's as far I get and the screen goes black. 

then I tried the alternate cd - it did the same thing, so I changed the vga to 640x400 (because I had an idea that that was the problem) - then I got to the actual installing interface. 

The installation went fine, but the first time I started the computer, I see the Ubuntu Loading Bar...

Then I see the login screen. I enter my user and password...

 Then the brown background and the mouse appears... and that's it...

Anybody know how I can turn debugging on, so I can see, when it stops loading? Or does anybody have an idea what actually could be the problem?

(The screen is a 15" TFT screen that can handle 1024* whatever)

I appreciate your help.

---

### Post by jordanmthomas on 2007-10-17
When you're booting up hit ESC at the grub menu and press e on your ubuntu install
Then, press e on the line that begins with 'kernel'  and delete the word 'quiet' (and also splash if it's there) from it.  Hit enter and then 'b' to boot.

You should be able to see what's going on when you boot then.

---

### Post by Shevilie on 2007-10-17
I forgot to say that I reach the login.. I enter my user and password.. Then I get the background and the cursor...

---

### Post by jrasmussen0 on 2007-10-17
I had the same problem and it seemed to have more to do with having XGL installed previously.

Try running 'mkdir ~/.config/xserver-xgl; touch ~/.config/xserver-xgl/disable' and then restart X '/etc/init.d/gdm restart'

---

### Post by Shevilie on 2007-10-17
Well the problem is that I never get longer than typing my password and user... So when should i do this ???

---

### Post by scapalexis888 on 2007-10-17
Maybe wait till GG is officially released?

---

### Post by GaryLittlemore on 2007-10-17
I have this problem with 7.10RC but my black screen is before the login screen.

---

### Post by techno-mole on 2007-10-17
i would say wait until 7.10 is officially released (even though i didnt)
Ive been running the rc for a couple of days, and i have had some issues, but all of them small, and they will probably be sorted once my system is updated to the official version.
but so far its kicking a##@ compiz is running like a dream (after installing the settings manager, which doesnt get installed by default) eveything else is fine, some small sound issues (report already filed) and a small issue with changing cursors (another report filed) with 7.04 i could never get bluetooth working, the system would see the adapter was connected but it would never pair up with my phone, tried it with 7.10 worked first time and all i had to do was set up a couple of things.
ive been running virtual box for a while as some of the courses im doing the software they use is designed for windows, so ive got virtual box set up and it runs really well, im using my larger external drive as a network drive so i can move files from virtual system to ubuntu and back, ive done it this way because i have 2 hard drives one runs ubuntu and one runs xp (for games) and sometimes i have to move files about.

read/write for external ntfs drives was enabled by default, basically i cant really fault it, yes there are some small issues (small for me anyway) but arent there always with most pieces of software ?
how many people have to update various applications/games and operating systems regardless of which operating system they are using ?
its to be expected, but from my point of view this version seems alot more stable than 7.04 even this early on, so hopefully it will continue to be stable.

cheers

my system specs are - 

amd 3400 + cpu @ 2.4 ghz (over clocked in bios)
nvidia ge force 7600 gs 256mb agp graphics card.
1.24 gb of ddr 3400 ram (1 x 1 gb stick ocz ram + 1 x 256 mb stick ebuyer 3400 ram)
sound blaster 24 bit sound card.
2 x 80 gb sata drives (one with ubuntu on and one with xp on)
system is on a home network (wired through 4 port router) and networks fine with the other 2 pc's (both are running xp, but will soon be running a dual boot set up)
1 x 250 gb external hard drive + 1 x 20 gb external drive.

---

### Post by jrasmussen0 on 2007-10-17
In order to touch the file you will need to press ctrl-alt-F1 to get to a command prompt or you could try to start Ubuntu in the safe mode.

---

### Post by XVII on 2007-10-17
I would suggest to wait for the official release, try again, remember to burn slowly, and remember that there is no longer a splash screen.

---

