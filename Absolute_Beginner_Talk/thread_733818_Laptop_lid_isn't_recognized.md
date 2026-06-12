---
title: "Laptop lid isn't recognized"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Drittponken on 2008-03-24
Hi, i installed Ubuntu Gutsy gibbon on my HP compaq nc6000 laptop recently.

But i have one problem, Ubuntu doesn't seem to "recognize" (in lack of a better word) that i close the lid to my computer. So it still runs like nothin happens, that disturbs me because i rather have Ubuntu turn off my screen or something. 


So, is there any solution?

---

### Post by (((X))) on 2008-03-24
This is because you must configure it first.
There is an applet, called energy star or battery monitor not sure, there you can configure how your laptop will act if you close the lid, it has several options like hibernate, lock screen..

---

### Post by Drittponken on 2008-03-24
Well, in gnome's "power manager" it's set to blank the screen. And i remember that it did work when using the live-cd, if i'm not misstaken. 

But now, nothing happens.

---

### Post by sillyxone on 2008-03-24
it could be that same bug that existed a while ago:

[https://bugs.launchpad.net/ubuntu/+s...rt/+bug/163265](https://bugs.launchpad.net/ubuntu/+s...rt/+bug/163265)

check /etc/acpi/events/lidbtn to see if the typo is still there, if yes, it will ignore lid event, and can be fixed by changing the line:

event=button[ /]lid

to:
event=button[/]lid"

---

### Post by Drittponken on 2008-03-24
> **sillyxone said:**
> it could be that same bug that existed a while ago:

[https://bugs.launchpad.net/ubuntu/+s...rt/+bug/163265](https://bugs.launchpad.net/ubuntu/+s...rt/+bug/163265)

check /etc/acpi/events/lidbtn to see if the typo is still there, if yes, it will ignore lid event, and can be fixed by changing the line:

event=button[ /]lid

to:
event=button[/]lid"

I tried that and the typo was there.

So i changed it as you suggested and then i restarted X. (ctrl+alt+backspace)
Unfortunatly it didn't work. What can i try more?

---

### Post by sillyxone on 2008-03-24
I don't remember exactly how to reload acpi daemon so please restart your computer and try again.

you can also use acpi_listen to make sure that the lid event is registered

---

### Post by Drittponken on 2008-03-24
I've tried to reboot the computer, but no success.

When i use acpi_listen the lit event is registered. But it takes some time for it to be registered. Id dosen't show up for some seconds and if feels like i must release the button for it to register it.

```

michel@michel-laptop:~$ acpi_listen
button/power PWRF 00000080 00000001
thermal_zone TZ1 00000081 00000000
thermal_zone TZ1 00000081 00000000
button/lid C139 00000080 0000001a
button/power PWRF 00000080 00000002
button/power PWRF 00000080 00000003
button/lid C139 00000080 0000001b
button/lid C139 00000080 0000001c
button/power PWRF 00000080 00000004

```

I have to release the buton and make another event before the lid button is registered :S

---

### Post by sillyxone on 2008-03-24
yeah, my Dell D620 sometimes ignore lid event as well. I usually debug it by editing /etc/acpi/lid.sh, add something like "echo debug_1 >> /tmp/lid_debug.log" at various places in the script to see where it got stopped (just keep increasing the number every time you add a new line). Run the script directly (without using the lid) so you can see what happens.

most of the time it couldn't get pass the line: 
if [ `CheckPolicy` = 0 ]; then exit; fi
mostly because it passes the job to power manager and PM just does nothing.

if you just want it to always turn off backlight when lid closes, you can add xset command at top of lid.sh (search for it, I don't remember the exact detail how to use it).

---

### Post by Drittponken on 2008-03-24
I will look into that. I found a related bug that seems to be exactly what i experience.

[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/89860](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/89860)

i also tried what this guy wrote, and it worked (we have the same computer) så i guess i'll have to wait for an complete fix. 

[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/89860/comments/20](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/89860/comments/20)



but your suggestion about adding the "xset" command, does it just turn off the light or can i get it too blank the screen as it should?

i would like it to suspend.

---

### Post by sillyxone on 2008-03-24
sad, it's not consistent on my laptop neither, so usually I hit the suspend button before closing the lid (in your case that would be Fn-F5). Sometimes, the sleep button doesn't do anything that I have to click on power icon (top right) and select suspend from there.

If the sleep button works consistently, you can tinker with lid.sh, comment out the line with "CheckPolicy" so that it won't pass the job to power manager, and then in the if branch where the lid state is closed, edit to call sleepbtn.sh instead.

---

