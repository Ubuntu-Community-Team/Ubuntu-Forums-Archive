---
title: "How to dump Dual Boot Screen"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by soho2014 on 2007-05-08
I have windows/ubuntu dual boot set up, and I like ubuntu so much that i'd like to remove the dual boot screen that shows up when I first turn the computer on.

How do i get rid of this screen?:confused:   There is some data on the windows partition that I need right now, so I don't want to forma that partition.

Any help on this problem would be GREATLY APPRECIATED!!!!!!!!!!:popcorn: :) :)

---

### Post by Bartender on 2007-05-08
Whoa there, soho -
That screen you see is coming from a part of your PC that you don't want to go mucking around with until you're sure of what you're doing.
GRUB, the Ubuntu bootloader, has modified the Windows MBR.  If you corrupt MBR you may not be able to get to Windows at all.  

Save the data you need from Windows, then re-install Ubuntu to the entire disc if you're sure you're done with Windows.  Otherwise, I'd strongly suggest getting used to the "Which OS do you want to start?" screen.

---

### Post by ohgod on 2007-05-08
You can edit the grub settings so that the menu never shows up:

Edit the /boot/grub/menu.lst file (sudo gedit /boot/grub/menu.lst).
-Look for the 'hiddenmenu' setting and make sure it's not commented out.

You can also change the timeout value to 0 so that you don't have to wait before the default boot option is selected:
-Look for the 'timeout' setting and change it to 0.

Ex:
```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		0

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

```

---

### Post by mikewhatever on 2007-05-08
If that's GRUB menu you are talking about, then type
> gksudo gedit /boot/grub/menu.lst

Find this line > #hidemenu
and change it to > hidemenu
save and exit.
Now, you'll only see the timer at boot. If you ever need that menu again, hit Esc during the count down.

---

### Post by DarthWHO on 2007-05-08
> **ohgod said:**
> 

-Look for the 'timeout' setting and change it to 0.



Quick question on this...If you change the timeout to 0 and do a hidemenu, can you still hit ESC to bring up the menu?

I guess my concern with setting the timeout to 0 is that you are leaving yourself either A) no opportunity or B) a really short opportunity to bring up the menu if required for troubleshooting (Recovery Mode).

---

### Post by Terl on 2007-05-08
> **DarthWHO said:**
> Quick question on this...If you change the timeout to 0 and do a hidemenu, can you still hit ESC to bring up the menu?

I guess my concern with setting the timeout to 0 is that you are leaving yourself either A) no opportunity or B) a really short opportunity to bring up the menu if required for troubleshooting (Recovery Mode).

I think hitting a key will show the menu but with the timer set to zero I am not sure you'd have time.  This is why I would just set Ubuntu to default and set the timer for, say 5.  This way it will just boot to ubuntu but still leave options just in case you ever do need to select recovery mode, for example.

---

### Post by DarthWHO on 2007-05-08
All-in-all soho2014, I think the key here is to realize that the grub boot loader wasn't just put there for you to dual-boot to Windows. grub allows you to manage how Linux starts up as well. Another option for you is to completely remove the Windows reference from menu.lst (usually towards the bottom) reduce the timer to say 3 seconds, make sure the bootup you want is first in the list and go with that.

---

### Post by soho2014 on 2007-05-08
Thanks everyone for your help.  I think that I just need to set timer to zero, since the one that I want by default is ubuntu.  But thinking about it again, there is a second sort of safe mode for ubuntu, so maybe I should leave timer on?

---

### Post by orb9220 on 2007-05-08
I just put the timer to 2 secs. Which flysby fast but still gives you access to menu when you need it.

---

### Post by earobinson on 2007-05-08
> **soho2014 said:**
> Thanks everyone for your help.  I think that I just need to set timer to zero, since the one that I want by default is ubuntu.  But thinking about it again, there is a second sort of safe mode for ubuntu, so maybe I should leave timer on?
Yes you should leave the timer on, all sorts of cool things can be done from that boot menu if you get into trouble.

2 - 3 seconds is great. It really dosent hurt your boot time that much compaird to all the advantages you get.

---

