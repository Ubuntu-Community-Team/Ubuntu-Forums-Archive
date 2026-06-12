---
title: "Fresh Install = Blinking Cursor"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by en3rgy on 2007-03-16
I admit I am new to Linux but have been working with PC's since DOS 3. 

Recently I have become uncomfortable with what MS has been pushing on the public and decided to try Linux. UBUNTU was what I chose thanks to the article "30 days with UBUNTU" over at [H] forums. 

I have successfully installed UBUNTU (I think) and I get to the point where I eject the cd and fully reboot. I get past the POST and then I am staring at a blinking cursor. It just sits there... blinking. I let it blink last night for over 2 hours thinking it was doing "something". Well, I am rather tenacious and am unwilling to give up as this is a new challenge for me. With that said, I was wondering if anyone has anything constructive information that will help me here. I did re-download UBUNTU 6.10 and burned another cd and reinstalled... but still have the same issue.

My hardware specs;
MAIN BOARD       ASUS P4P800E Deluxe
CPU                    Intel P4 3.2
MEMORY            (2) 1 gig Corsair CMX1024-3200PT
DVD/CD              Plextor DVD burner (IDE)
HDD                   Western Digital 150 Raptor (SATA) Hard Drive
VIDEO CARD       EVGA nVidia 6800 Ultra Video Card
MONITORS         (2) Dell 2407FPS monitors
KEYBOARD         MS 4000 Ergo
MOUSE              Logitech MX 518

Thank you in advance for any logical help you can offer.

---

### Post by jbayone on 2007-03-16
it may be your xorg, you can try rebooting in recovery mode, then sudo dpkg-reconfigure xserver-xorg and go through the steps there, since it's a fresh install, you can choose the nv driver or even the vesa driver (don't kill me if i'm wrong) then type sudo \etc\init.d\gdm start

---

### Post by Kateikyoushi on 2007-03-16
You get past the post but not yet to the grub menu ? Then it is a problem with grub.

---

### Post by en3rgy on 2007-03-16
> **jbayone said:**
> it may be your xorg, you can try rebooting in recovery mode, then sudo dpkg-reconfigure xserver-xorg and go through the steps there, since it's a fresh install, you can choose the nv driver or even the vesa driver (don't kill me if i'm wrong) then type sudo \etc\init.d\gdm start
I have done a Google search trying to find the definition of the term "xorg" and am not coming up with much. So I am going to guess that "xorg" is like a config.sys file in DOS. 

Step 2: Reboot in recovery mode.
I can not access a command line so I am once again guessing that you are suggesting that I reboot with the cd and choose the "safe mode" option. Then, once at the desktop, go to Applications -> Accessories -> Terminal then type "sudo dpkg-reconfigure xserver-xorg" - and follow the steps therein. Then at some point I will be asked which video driver to go with "nv and/or vesa" and type "sudo \etc\init.d\gdm start". Obviously without the quotes 

Summization: The problem then is ultimately with the nVidia video card's driver not being recognized or properly installed each time I tried to install UBUNTU. Does that sound correct? With UBUNTU I feel like I am in a dark forrest with a small flashlight. :) :) :)

---

### Post by en3rgy on 2007-03-16
> **Kateikyoushi said:**
> You get past the post but not yet to the grub menu ? Then it is a problem with grub.
The grub menu is in Windows terms the os choice/multi boot load menu... correct? 
[IMG]http://nobumasa-web.hp.infoseek.co.jp/multi_boot/grub_menu.gif[/IMG]
This is just a pic I found doing a Google image search for the term "Grub Menu"

---

### Post by Kateikyoushi on 2007-03-16
Yes this is grub, but from your previous post I assume you do not get this far.

---

### Post by en3rgy on 2007-03-16
> **Kateikyoushi said:**
> Yes this is grub, but from your previous post I assume you do not get this far.
Rgr that. All I get after my POST is a blank screen with a horizontal blinking cursor. I press alpha keys on my keyboard to see if my pc/os is responding but the cursor statically blinks into oblivion. Of course, I also checked my caps lock key to see if my hardware was still working and my kb caps lock light responds so that's working at least. #-o

---

### Post by en3rgy on 2007-03-16
I also wish to add that the primary boot hard drive is brand new and has never been formatted prior to this UBUNTU install.

---

### Post by Fataltragedy2 on 2007-03-16
> **en3rgy said:**
> I also wish to add that the primary boot hard drive is brand new and has never been formatted prior to this UBUNTU install.

What kind of cursor is it? The generic windows one or the short stubby ubuntu one?

---

### Post by PhillyB on 2007-03-16
Well I have the same exact problem.  Total Newb.

P4P800 mobo
3.4p4
1gb rams
160gb WD IDE
36gb Raptor sata - really wanting to install to this drive
5200 Agp
650w seasonic
Dvd-rom IDE 


I am trying to do a LAMP server install, tried that first, got a no-boot style bios message.  Tried the normal install to hard drive, same thing.  Killed all the partitions including the 160gb and tried again to install to the sata drive, this time blinking cursor.  Bios then cursor.  Going to try to install to IDE now I guess.  I really need the speed of that Raptor.

---

### Post by en3rgy on 2007-03-16
> **Fataltragedy2 said:**
> What kind of cursor is it? The generic windows one or the short stubby ubuntu one?
I have to go with the first choice here. It's a black screen, no gui, with a white horizontal cursor blinking.

---

### Post by PhillyB on 2007-03-16
Alrighty!  Removed the power from the IDE drive, did LAMP again, boom its doing something!!  Not sure what exactly.

---

### Post by en3rgy on 2007-03-17
Can someone tell me how to make sure grub was installed properly? Or is there a way to check this? A friend of mine suggested that there may be a master boot record issue as a result of grub not installing correctly. 

Thanks for your help.

---

### Post by en3rgy on 2007-03-17
Ok, so this is where I am now and it's really blowing my mind. Now, when I go to reinstall UBUNTU again, during the beginning stages of the INSTALL cd boot up to desktop the top of my screen looks like it's "choppy"... like swatches of horizontal lines blinking and what not (reminds me of a monitor that is not attached securely to a video card). Then, I get to the "desktop" where I select INSTALL and everything looks great. In fact, now my screen maxes out at 1024 x 768 whereas yesterday it went to 1280 x 1024 (Dell 2407FPS monitor). 

I know my video card is 100% functional as I have swapped primary drives back to an XP install and everything looks just perfect. 

Anyone have any ideas on this by chance?

---

### Post by freebird54 on 2007-03-17
I am not an nVidoia guy - but the place to start is by editing your /etc/X11/xorg.conf file - which pretty covers all your X-windows setup.  Open a terminal (Applications->Accessories->Terminal) and type or paste this into it and hit <enter>.

```
gksudo gedit /etc/X11/xorg.conf
```

the section of the file that looks like this:

```

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Radeon 9550"
        Monitor    "Samsung_900iFT"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
```


is the one you need to alter to show the resolutions you wish to use (that your system CAN use ) .  You might want to specify the Sync and Refresh setting while you're in there too - in this section:

```
Section "Monitor"
        Identifier   "Samsung_900iFT"
        HorizSync    30.0 - 70.0
        VertRefresh  50.0 - 85.0
        Option      "DPMS"
EndSection
```

using the values appropriate for your system of course!

Sorry if I'm too detailed - but I haven't really met you yet :)  Good luck and enjoy.

---

### Post by h0ax on 2007-03-17
The problem here is not nvidia - He is not booting the OS

I had this problem a while ago, and I think I may have resurrected it tonight, ugh.

Anyway - it is indeed a problem with GRUB at the hardware level.

What I did to fix it -> 
Instead of having the jumper on the hdd:
I can't remember which one it was but either:
PRIMARY (MASTER) --> I put it on CABLE SELECT(CS)
CABLE SELECT(CS) --> put it on PRIMARY (MASTER)

Guys - if has barely got past POST - this has nothing to do with xorg or nvidia...

---

### Post by freebird54 on 2007-03-18
Probably not - but it sounded as if the Live CD ran, and the install worked.  I can see how a mismatch on the drives could appear at that time too, though I would have expected the install to fail as well...

As long as someone gets him going again!

---

### Post by en3rgy on 2007-03-20
I wish to say thank you to everyone who took the time to respond to my problem. h)ax was correct, I removed all hdd's except for the install hdd and rebooted into a fully functional os! 

Now begins my learning curve and I am very excited about it! Thus far I am very confused as to how to fix a few minor display issues but Ill spend some time here and about the 'net and Im sure Ill find what I need.

Thanks again to everyone, sometimes being a small fish (me) in a big lake sucks but this is one fish that swims fast! :guitar: :guitar: :guitar:

---

