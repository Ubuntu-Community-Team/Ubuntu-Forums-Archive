---
title: "A couple different issues - 7.1/GeForce 3 issues, and xorg.conf will not save changes"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by RevGored on 2008-02-04
Hey there guys, just installed 7.1 about a couple weeks ago, and I only get intermittent time with the machine.

I've got a couple glaring issues that I can't seem to get around here, and I'm just trying a shot in the dark here.

1)  I'm running on an OLD machine here - Athlon 1,1, 256meg, GeForce 3 Ultra 64meg.  System runs a might slow, but it still runs.  However, I cannot get the video card to take - my monitor is an old LCD (NEC Multisync 1525M), and the res defaults to 800X600 on desktop, and will not change.  I tried Envy, and it will not jive with 7.1, for some reason.  Now, I've managed to get my machine to recognize the card, and reset the desktop res to 1024X768 BUT, upon a restart, the desktop goes back to 800X600, and will not change.  

2)  Same setup as above, but, now, my xorg.conf will randomly just 'forget' the settings that I edit into it - for example, I am trying to use a 5 button mouse, so I remove the current mouse operators in the .conf, and replace it as such - 

Section "InputDevice"
       Identifier "Configured Mouse"
       Driver "mouse"
       Option "CorePointer"
      Option "Device" "/dev/input/mice"
      Option "Protocol" "ExplorerPS/2"
      Option "Buttons" "7"
      Option "ButtonMapping" "1 2 3 6 7"
      Option "ZAxisMapping" "4 5"
EndSection

 - Here's the kicker though - when I do a reboot, the .conf sometimes just forgets I ever did that.  Like, the old settings are just there, and the settings for the new mouse are completely removed,

Has anyone experienced anything like these issues, and have any advice for a new user?  I'm really trying to get into it here, but Google hasn't really turned up much as far as solutions for these two problems I've been getting stonewalled with lately.

Thanks in advance!

---

### Post by spiderbatdad on 2008-02-04
i believe this may have to do with irqpolling during startup. I am not an expert.  You may need to edit the kernel line in /boot /grub/menu.lst by removing ro --quiet splash, and replacing with noapic nolapic noirqpoll vga=771
good luck.

---

