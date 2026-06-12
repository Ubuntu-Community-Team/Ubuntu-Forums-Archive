---
title: "Xubuntu won't shut down...."
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by HighlyCalculated on 2008-03-19
When I try to shut down Xubuntu, it will get to the screen with the Xubuntu logo and the progress bar, and then it just seems to stop.  I've let it sit for a couple hours and nothing happened.  It stayed on, the bar never moved, and the working light on my PC never even blinked, or lit up.

Oddly enough, the very first time I shut down it worked fine.  Next time I powered down for the night, I used hibernate and it worked.  However the next time I used hibernate, it went into the screen where it's showing in text form the things it's doing to shut down, but then got to a point where the last words at the end of the text were "shut down" (or something to that effect) and did nothing for twenty mins....since then, I've only tried to use the "Shut Down" button, and got the result mentioned above.

I haven't done anything to my system other then add a couple firefox and thunderbird add-ons, remove abiword and add OpenOffice Spreadsheet.

I also removed the restricted drivers manager, but when I clicked it, it said I didn't have anything that needed restricted drivers.  The problem did exsist before I took it off.

I've also unchecked the "Save session for future logins" check box in the shut down screen.

If the problem can't be solved, how bad is it to be physically turning off my computer at the screen I mentioned it stops at earlier?

---

### Post by linuxtoindia on 2008-03-19
try
sudo su -


and then ''logoff''
in terminal 
after that just shut down!

---

### Post by Jareth on 2008-03-19
Hi,
did this work for you? I have a similar problem with ubuntu feisty and gutsy. Neither will shut down, they just stay on the ubuntu logo.

---

### Post by HighlyCalculated on 2008-03-19
It tells me: comand not found, when I put in "logoff".

Maybe I'm missing something?  I'm very new to the terminal.

---

### Post by BillDozer on 2008-03-19
try:
```
sudo shutdown -h now
```

---

### Post by Jareth on 2008-03-19
Do you mind if I ask what these commands do?
I make my own notes when I find a new command and what it was for.
Thanks!

---

### Post by BillDozer on 2008-03-19
> **Jareth said:**
> Do you mind if I ask what these commands do?
I make my own notes when I find a new command and what it was for.
Thanks!
**sudo**: Call the next command in super user mode.
**shutdown -h now**: Shut the computer down, the -h switch means halt (so that the systems shuts completely down) and now means right now ;-)

You can also change -h with -r then it means restart.

For a complete description try and type:
```
man shutdown
```
**man**: manual (documentation) pages.

---

### Post by Jareth on 2008-03-19
Brilliant!

Thanks so much dozer!

---

### Post by HighlyCalculated on 2008-03-19
I've tried a few different shutdown commands with no luck.

Judging by the sounds my PC makes when shutting down, the HD does shut off (stops spinning at least), but the power source stays on.  The lights on my network card stay on also.

I haven't had any problems resarting so far, so I think it is safe to manually power down at that point....if any knows otherwise, let me know..

When I boot, I get a message that my BIOS fails the cutoff age, and force is required to enable ACPI.  Could this have something to do with it?

---

### Post by BillDozer on 2008-03-19
Yes I think so, try to add noacpi on the bootline in GRUB when you start your PC. And then try to shutdown again. If this helps you could edit the menu.lst in /boot/grub and add the option there.

I think when the PC is shutting down, you can press Ctrl-Alt-F1 and see what it does. As I recall the last line is something like system halted or something like that.

---

### Post by linuxtoindia on 2008-03-19
power off! plug out!
hit a baseball bat on cpu!! kdng! 
dnt do this..


just take a boot cd and repair the  missing files

---

### Post by undertakingyou on 2008-03-19
Maybe I missed this, but what are the specs of the computer in question?  There might be some sort of driver issues or conflicts.

---

### Post by HighlyCalculated on 2008-03-23
Finally got some free time to play with PC.

> **BillDozer said:**
> Yes I think so, try to add noacpi on the bootline in GRUB when you start your PC. And then try to shutdown again. If this helps you could edit the menu.lst in /boot/grub and add the option there.

I think when the PC is shutting down, you can press Ctrl-Alt-F1 and see what it does. As I recall the last line is something like system halted or something like that.

Can someone give me a bit more detail on adding noacpi to the bootline in GRUB?  I've never done anything in/with/at GRUB at all....

The last line when I try to hibernate is "Power Down".  When I try to shut down, It takes me to a screen with the Xubuntu logo, and a status bar, however the status bar never moves, (again, I've let it sit for hours), but my HD does stop spinning, and all the lights on my keyboard turn off.  My power source stays on, and the lights on my network card stay on...

> **undertakingyou said:**
> Maybe I missed this, but what are the specs of the computer in question?  There might be some sort of driver issues or conflicts.

250 mHz processor, 256 mb RAM, ATB Velocity 128 graphics card (uses the nv driver)....if you need more info, just ask specifically for what you need.

---

### Post by plucky on 2008-03-23
> Can someone give me a bit more detail on adding noacpi to the bootline in GRUB?

In Xubuntu ```
sudo nano /boot/grub/menu.lst
``` enter password,then search for line that looks like this > kernel          /vmlinuz-2.6.22-14-generic root=UUID=c65f00cc-bb55-4e82-acea-922fe8e691c6 ro quite splash and add the noacpi like
 > kernel          /vmlinuz-2.6.22-14-generic root=UUID=c65f00cc-bb55-4e82-acea-922fe8e691c6 ro quiet splash **noacpi**

Also search for the line > # defoptions=quiet splash and change to 
> # defoptions=quiet splash noacpi so that then option will be written to the kernel line when there are kernel upgrades.
Then **Ctrl O** letter o not zero to write the file and then **CTRL X** to exit NANO.


[color=red]OK now my 2 cents,[/color]

To fix your problem I would use ```
acpi=off apm=on
``` instead of noacpi and then also edit **/etc/modules** file with ```
sudo nano /etc/modules
``` and enter the line into the file ```
 apm power_off=1
``` and also change the **defoptions** line and add **acpi=off apm=on**

Good Luck

---

