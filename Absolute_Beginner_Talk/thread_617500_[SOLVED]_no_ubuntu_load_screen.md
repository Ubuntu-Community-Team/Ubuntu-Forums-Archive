---
title: "[SOLVED] no ubuntu load screen"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by LowSky on 2007-11-19
OK here an odd issue that I can't find help on (google has failed me)

My computer and monitor turn on fine, goes into grub just fine as I can see everything and choose my OS, but when it starts to load ubuntu my screen looses its signal from my computer and doent come back up until ubuntu starts loading X/Gnome.

I'm cant seem to think what the issue is, is it my xorg.conf or grub, or something else? Could it be my video drive, but I'm running everything else ok including Compiz?

Here are my specs

Ubuntu 64 7.10
AMD Athlon64 3700+
2Gb SDRAM
Nvidia 8600gt

---

### Post by LowSky on 2007-11-19
bump...

---

### Post by blithen on 2007-11-19
Why is it such a big deal as long it runs when you go into X/GNOME then what does it matter?

---

### Post by question_chick on 2007-11-19
do you have a widescreen display by any chance?

It has something to do with the resolution of the splash screen. 

what video card do you have and do you have all the relevant drivers for it?

I do have more details but they re at home on my computer, will hunt them out and try to post them tonight.

---

### Post by LowSky on 2007-11-19
I would like to know if my computer is actually booting or hung up for 2-3 minutes. I cant even see what its starting in safe mode while it boots.

Everytihng is working fine now but if anything goes wrong it nice to know something something should be working

---

### Post by LowSky on 2007-11-19
> **question_chick said:**
> do you have a widescreen display by any chance?

It has something to do with the resolution of the splash screen. 

what video card do you have and do you have all the relevant drivers for it?

I do have more details but they re at home on my computer, will hunt them out and try to post them tonight.
thanks

I am using a 19" widesceen LCD with 1400x900 resolution and a Nvidia 8600gt with the nvidia-glx-new drivers

---

### Post by blithen on 2007-11-19
> **LowSky said:**
> I would like to know if my computer is actually booting or hung up for 2-3 minutes. I cant even see what its starting in safe mode while it boots.

Everytihng is working fine now but if anything goes wrong it nice to know something something should be working

Ah okay good point. Though I have no idea how to help. Do you have a widescreen?

---

### Post by question_chick on 2007-11-19
ok, so that's all good.

you can edit the resolution in menu.lst but I can't remeber the exact way to edit it, maybe someone else knows?

---

### Post by question_chick on 2007-11-19
ok, this might help, it's a solution to another problem but the vga part is the resolution for the splash screen

> 
Does the black Ubuntu loading splash screen work when you do that?

If not, here is another (slightly longer) fix that was posted elsewhere to fix it for reals. The problem with the slow boot is that the settings in Usplash can sometimes get messed up on install and hang up the boot. Removing some of the lines in menu.lst disables Usplash and fixes the problem. If you like the verbose boot up, then leave it. If you'd like the pretty Ubuntu boot up sequence, try this.

1) Put everything back in /boot/grub/menu.lst that you took out ( "ro quiet splash" in the kernel line and "quiet" at the end)

2) At the very end of the kernel line after "splash" , add "vga=791" This is the weird part for me, because I'm not exactly sure why the number is 791. Make sure this goes on the same line, though.

3) Save that file, close it, and open up /etc/usplash.conf

4) Change the screen resolution to the resolution you are actually using. Save it and close it.

5) Grub won't know anything about this until you rebuild the boot, so do the following commands.

uname -r
This lists your current kernel version.

sudo update-initramfs -u -k <insert results from uname -r here>

This rebuilds the image that Grub uses to start the system.

Voila, you have fixed the boot speed issue and gotten the splash screen back. Reboot and enjoy the fruits of your labor. Your mileage may vary, but it worked for me on the first try and for quite a few other people throughout the forum. This only works if Usplash is what was broken, which sounds right for all of you. Also, you can always hit CTRL-F1 when the splash is running to get back to your verbose mode.


---

### Post by LowSky on 2007-11-19
i'll try it, but does it matter that I use DVI and not VGA?

---

### Post by question_chick on 2007-11-19
That could be a ver good point, i'm honestly not sure.

---

### Post by Bigbird999 on 2007-11-19
Search for slow boot  black screen  no splash screen there are a bunch of threads on how to edit the startup vga resolution.

BB

---

### Post by LowSky on 2007-11-20
OK I tried this, with the supplied VGA number and another I found for my monitors resolution and both did not work...

here's what I tried
```
sudo gedit /boot/grub/menu.lst 
```

At the very end of the kernel line after "splash" , added "vga=791" (i used a different code as well just to try but no luck)

Saved that file, closed it, and opened up  ```
sudo gedit /etc/usplash.conf 
```  
Changed the screen resolution to the resolution I am using.  Didn't  work, tonight I might resize to smaller number to try again)

```
sudo update-initramfs -u -k <insert results from uname -r here> 
```

I even reinstalled my video driver using Envy, but still nothing, I think I may try to copy and paste /boot/grub/menu.lst  from another computer i'm using but leave certain settings alone.

---

### Post by Bigbird999 on 2007-11-20
You last line of code is very picky.  If you read the thread there is one post that talks about tick marks like this `(upper left key under esc) around the uname -r results if you use quote marks like this '(left of enter) it won't work or if you miss one ` it won't work  I can't remember exactly but it should be something like `2.6.22-14-generic` .  Took me days to find that gem.  

BB

---

### Post by xdwmx on 2007-11-20
I have no boot screen either on 32/64bit Ubuntu 7.10.

There was a boot screen running the Live CD, but after the installation there was no boot screen.

ATI Mobility Radeon X1300

---

### Post by l33t_3lv3n_g33k on 2007-11-20
> **LowSky said:**
> I would like to know if my computer is actually booting or hung up for 2-3 minutes. I cant even see what its starting in safe mode while it boots.
 
Everytihng is working fine now but if anything goes wrong it nice to know something something should be working
 
I have the same problem.  Everything is booting fine if the system comes up.  You're not "hung up for 2-3 minutes", the computer just isn't displaying the shiny splash screen.  You can actually turn off the splash screen and you'll see the normal boot processes (not as pretty, but it should lay your suspicions to rest if you're worried that something is going wrong.)
 
Remove the "splash" argument from your /boot/grub/menu.lst lines.

---

### Post by Stunt Double on 2007-11-20
I'm running 7.10 and had the same problem. The solution was to use Synaptic Package Manager to install startupmanager. It's put in System-->Administration-->Start Up Manager. Under the BOOT OPTIONS tab, I changed the Color Depth from 8 bits to 16 bits. That's all it took. Now I have a splash screen when it starts and stops. And it loads in 1/4 the time.
I had tried changing most of the settings but ultimately, the change to 16 bits was all that was required to resolve the problem on two separate computers.

---

### Post by MyR on 2007-11-20
startupmanager makes editing /boot/grub/menu.lst much more user friendly :D

on my parents' system (dell dimension 2400) i had to change the resolution to 640x480 with 8bit color to get the boot splash to display. i'd been looking for a solution to this for months!

awesome, thanks!

---

### Post by gupta_sumesh63 on 2007-11-20
It does matter.
In /boot/grub/menu.lst there is an entry like defoptions=vga=791 or 771 or some number.
Just copy that and paste it below the block of defoptions.
say like this:
/boot/grub/menu.lst
#...
#....
#defoptions=vga=791 (copy this line only)
#defoptions=vga=791 follow /../hda5
(and paste it here without any hash mark as prefix)

Save the menu.lst and reboot.
Your problem will be solved.

---

### Post by MyR on 2007-11-20
you missed page two buddy ;]

---

### Post by gupta_sumesh63 on 2007-11-21
Ya I did miss out the page 2. Its an oversight. I'll have to get my right eye checked by an eye specialist I think. Thanks for informing me. No pun intended. Its a fact and thanks is genuine.:lolflag:

---

### Post by darvasi on 2008-02-04
Hi all,

I'd like to add that I had the same problem.
Than from Synaptic Package Manager I installed startupmanager.
But in my situation I had to set the colours from 8bits to 16 bits and
also had to set the resolution to 800x600.
This is solved the "no load screen issue".
I've got HP Pavilion dv5000 with Ati Radeon XPRESS 200M VGA.

:lolflag:

I have been looking for this info for long too. Thanks mates!!!

---

### Post by staticvoid on 2008-02-04
just to mention,

hit  **ALT  F1** to see the text load  :)

i had this problem and did the VGA fix, and it worked. if all else fails try doing a verbose boot, even though it might be ugly.. :)

SV

---

### Post by LowSky on 2008-02-04
Wow I'm amazed this thread came back from the dead... marking it solved

---

