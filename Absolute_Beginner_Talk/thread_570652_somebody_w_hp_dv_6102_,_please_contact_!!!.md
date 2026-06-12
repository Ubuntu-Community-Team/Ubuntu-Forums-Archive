---
title: "somebody w/ hp dv 6102 , please contact !!!"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by doron387 on 2007-10-08
I am terribly sorry for not beung polite according to the forum's rules, but i have been spending the last week almost w/no sleeping as my kubuntu installation on my hp dv 6102 wouldn't boot.
i read a lot of threads and articles, but not a clue.
i am a newbi and just wish to know if there is another person who uses k/ubuntu 7.04 on an hp dv 6102, i would like to ask  a question that might solve my problem.
please, forum admin. if you heard about such a person please contact us.
and wish to say sorry again and thnx.
doron
:confused:

---

### Post by molly_001 on 2007-10-08
Please describe in some detail the repeatable problems you are seeing.
What do you see on the screen if it will not boot?
What actions did you take before trying to install?
etc.
Thanks!

---

### Post by doron387 on 2007-10-08
:confused:
my machine is : laptop hp pavilion dv 6102 ea
+mobile amd sempron 3400
i386 family, 1.8 MHz
nvidia geforce 6150 go, driver : nv4_mini.sys
resolution 1280x800x32
512 ram
hd sata 70 Gb

the istallation steps were :
1. totally recovering of the computer (after bad installation) - the comuter worked fine afterwards w/wnxp.
1.5 defraged the windows hd.
2. resized the win NTFS partition (made it small in 10 Gb) by GParted.
3. ran the live cd session, everything was as usual (i did press F4->chose 1024x768x32->everything worked well)
4. installed kubuntu using the option : "guided - use largest free consistent space in the disk"
5. installation passed perfect untill the shut aown sequence which never in the previous sessions reached the end perfectly - i mean that after ejecting the cd, closing the cd tray and pressing enter it always freezed, and this time again so i had to forced shutdown.

when i ran live cd sessions a few times before the installation, i discoverd that if i just pressed start/install kubuntu (the first menu option) the bar showed, then blank, then another bar, then blank screen and from here it didn't comtinue...(same screen like now, after the installation)

but

if i pressed F4, changed the resolution settings to 1024x768x32 it showed the bar, then blank, then bar, sounded beep when the second bar reached almost its end, then blank, then x appeared, then blue kubuntu screen etc... everything worked well.

now, after grub menu, if i choose first option (start kubuntu...) there are few lines too fast to catch, than the progress bar, then it the 75% of it, screen goes obscure (kind of greenish-black), nothing moves, no lights from the keyboard, no keyboards combinations works. totally freeze.

tried acpi apci off on etc etc...i don't have a clue what they do and hope i didn't ruin anything during these trial and error (for the last two days forum members try to help but this is like a shot in the dark)

as far as i understand, if before all i had to do was change vga to 1024x768x32 then this is what should be done now, but unfortunately this option does not appear on the grubmenu and i don't have a clue how it should be done.

wish 4 help !!! (it seems that only one who uses the same machine w/ the same software or an linuxq/ubuntu expert might have the soultion)

---

### Post by molly_001 on 2007-10-08
Boot into Ubuntu.  When the screen appears to go black or go blank, then hit 
CTRL + ALT + F1.

You will be given a root server terminal, type there:
[SIZE=-1]**sudo** dpkg-**reconfigure** xserver-xorg

Go through the options and you can change it.  
[/SIZE]

---

### Post by doron387 on 2007-10-08
in the last times that i tried ctr + alt + F1 it didn't do a thing, 
if i start in recovery mode and in the end of all the code lines i write it, is it the same ?

---

### Post by molly_001 on 2007-10-08
I've installed *buntu on 30+ machines, it still sounds like an xserver-xorg configuration error to me.

However, since you have a good understanding of partitions, why not use the Alternate Install CD (instead of the Live CD)?  The AI CD will show you step by step on each installation progress, so that you can identify (in text) where the install problem is occuring if there is an installation problem.

---

### Post by doron387 on 2007-10-08
well, i wouldn't say that i have good partitioning understanding, actually though i wanted to do the partitions my self the automatic way was the only way that workd. so i prefer not to do so.

but

i am just coming back from the terrifying experience of "comunicating"with the xserver configuration program, after i have put all inside i tried startx and it gave me some errors report.
mainly about :
1. FATAL ERROR :no screen found
2. no matching device section for instance (BusID PCI:0:10:13) found.

the truth is that were some lines that i might fordgot but these looked like the crucial ones.\

now, i agree with you that it is probably the xserver configuration that should be done but my question is :
is there a known guide (i am starting to look for it right away) for each computer model for this configuration routiine ? as the problem is that there were some questions that i did not have a clue what it ment so i pressed ENTER instead of writing nonsence. (e.g. what is pci:0:5:0 that he offered and that i pressed obbeyingly ENTER ?)
if not, should i wait for a hp dv 6102 like mine for answers or might i find all the info on the web ?

thnx
waiting 4 rply
doron

---

### Post by doron387 on 2007-10-08
please read the last message and another question :
assuming that i just messed up the xserver configuration that came with the installation, is there a way to put it back where it started few minutes ago ? (i am now in windows and will have to start all the booting from the beggining to do it)

---

### Post by annda on 2007-10-08
hi!

i understand you have messed up your Xorg configuration. can you still boot into recovery mode? if so, after booting add the appropriate resolution to the kernel parameters:

```
nano /boot/grub/menu.lst
```

in the line where the latest kernel is listed add "vga=792" for the 1024x768 resolution.

example:
> kernel		/boot/vmlinuz-2.6.22-12-generic vga=792

if your xorg.conf is damaged and won't let you boot, can you post its contents here? (recovery mode, and the file is located at /etc/X11/xorg.conf)

PS. when you boot into recovery mode, you can check if you you have automatic backups of the old xorg.conf

```
ls -la /etc/X11
```

files called xorg.confSOMETHING are backups and the one with the oldest timestamp/date will have your initial configuration. 

```
cp /etc/X11/xorg.confSOMETHING /etc/X11/xorg.conf
```

to restore the working configuration. it will overwrite the current file with the older config.

post back with questions.

---

### Post by doron387 on 2007-10-08
wow, thnx for the well explanation.

1. i can boot into recovery and i first found the xorg.confSOMETHING, then i copied it.
2. then i ran nano /boot....    in the end of the line was written 'ro'(what does it mean ?)
3. i added vga=792, confirmed the change and exit.
4. i am just a newbi so i imagine that then i had to click 'startx'which is what i did, but the screen went to the same like before.
was what you offering me to do was compliant with my idea about the F4 during live sessions ?
if the answer is yes then it means that i must configure my xserver from the ""bottom to the sealing" which is something that i don't know.

sorry for not sending the code/script as i can not copy paste, i am writing from winxp and booting again to try youre good folks advices.
i am awake, waiting for another hint.
(btw, sorry for my english, i am not eng spoken naturally - i speak hebrew much bette)r

---

### Post by molly_001 on 2007-10-08
Don't worry, I am recently of Petakh Tikva, we will forge our way through this problem together from Sheinkin & Allenby Streets to Broadway.

The proper configuration of xorg.conf doesn't depend on the model number, but instead on the type of graphics adapter in the machine and the way that the motherboard talks to that adapter.

Often, you just have to make a guess as to what is most successful while setting up xserver-xorg.  I have found the most often the following will work:
     i810
     check to make sure video card bus is PCI:1:0:0 (if not, then very unusual)
     select (asterick) only with 1024x768 and Lower
     "Simple" selection for monitor type (not Medium, not Advanced)
     16-bit color   (not 24)

The above almost always gets me to a viewable 1024x768 screen.

---

### Post by doron387 on 2007-10-09
shalom,
ok, i think that we are talking at leat at the same direction.....
well, 

1. do you have a  hp dv 6102 or you just urderstand linux/ubuntu very well ?
2. i don't understand what is 'i810' , i don't remember this question in the xorgconf but it might be just my memory, so please explain.
3. pcibus was in my case 0:5:0, what does it mean and should i change it to 1:0:0 (which means...?)
4. what do you mean by "select (asterick) only with 1024x768 and Lower'' - what is an  'asterick' ?
5. ok, i'll choose 'simple' monitor and not 'medium'as i have done mistakely- but will short explanation be possible please  ?
6. ok, i'll choose '16'instead of '24 bit' - but will short explanation be possible  ?
7. about guessing - as i don't have a clue about these definitions, it is not wise at all to guess, as you see, i have chosen 'normal'and '24 bit' because i was thinking that my machine is a normal one and that its screen should be with the best 'bit' number (another thing that i don't understand...)
btw, if you would call 02-6728532 (doron) and we'll have a short talk about what happend from the biggining of my experience with ubuntu i think that  it will be much faster to solve it, (i am eager to see this blue screen on my machine coming stright of my hd and not from a live cd) and i promise to make a [solved] thread to help others when it's done !
waiting 4 reply, thnx.

---

### Post by molly_001 on 2007-10-09
Shalom,

Funny note:  I just now Googled only this:  dv6102 ,
and the first google hit was your doron ubuntuforums inquiry from today, 10-09-2007.
Amazing!!  Also tells me that 6102 model was exclusive Israel/MidEast product.

All comments below are for using sudo dpkg-reconfigure xserver-xorg

  i810 is the adapter interface, it is on the same selection screen as 'nv' and 'nvidia' and 'ati' and 'vesa' ... there are about 30 choices, and i810 is one choice.

  pci bus is the numbered bus on which your graphics adapter is sitting.  The graphics is almost always 1:0:0 .  Should you change it?  No, I would not do so, yet.


  for asterick ... looks like this --> *

   on the screen for selecting resolution, 
you want asterick ( * ) only next to 1024x768 and lower, such as 800 x 600

 please choose 'simple' for monitor selection.  Then simply choose appropriate size, for instance choose 19-20 inch if you have 19-inch monitor.

  definitely choose 16-bit for color (and not 24) because the basic support in 32-bit machines is for 16-bit color  (still gives you millions of shades)  ... 24 often will not work when configuring/using X Window manager


We can work via Skype this evening (I am -8 hours to Israel)

---

### Post by molly_001 on 2007-10-09
Don't worry, you are not alone.  I have installed Ubuntu/Kubuntu and even other Linux distributions (such as OpenSuse) on many different machines, and easily 50% of the time there is some frustration.  The first of these frustrations is almost always the X Manager Windows (xserver-xorg).  Your success with installing Linux on that machine will be in direct proportion to how much effort and time you are willing to put into the endeavour.

However, your best approach is to "take a step back" and repeat the process with someone like me who has done it dozens of times.  I will help you if you are willing to do that attempt with me on a foundation of knowledge and experience.  Very important is that you always have a pencil and paper to record some errors when and if you see them.

Are you willing to download and burn to CD, the Alternate Install CD for Ubuntu(Kubuntu) 7.04 ?  This is the path by which you will have success.

---

