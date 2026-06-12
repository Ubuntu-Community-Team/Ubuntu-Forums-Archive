---
title: "unplug laptop annoyance"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by Corona on 2006-09-22
First of all -- let me say -- Ubuntu rocks. I havent booted into windows into months.

I do however have an annoyance, everytime I unplug my laptop the screen goes black and I have to enter my password. I know this is a security feature but I dont need it.

Is there anyway to disable this??

---

### Post by Metacarpal on 2006-09-22
I'm running Ubuntu on a laptop and don't have this happen...

Try right-clicking on the battery icon in your panel and choosing "Perferences" - that lets you configure the power management behavior when plugged in and when running on battery.  Might be able to stop it there.

Otherwise, I'm going to guess this is either a BIOS setting on your computer, or some sort of hardware/ACPI conflict.  I'm hoping the power management settings fixes it for you.

---

### Post by Corona on 2006-09-23
There is no option under power mgmt and I am sure that its ubuntu doing it.

Anyone else have a clue?

---

### Post by neogeek on 2006-09-23
what do u mean by unplug? do u shut down first?

---

### Post by Mimsy on 2006-09-23
I'm going to guess that the OP removes the AC powercord from the laptop without shutting it down, fuly expecting it t ocontinue to run off the battery, without blinking. that's what laptops do.

Except not that one, apparently. Mine only runs for an hour. I remain convinced that Ubuntu has communication difficulties with laptops.

/Mimsy

---

### Post by Corona on 2006-09-23
Let me clarify.

My laptop is powered on and is plugged into the wall, now I want to take my laptop somewhere else, so I unplug the power cable from the back. 

When I unplug the power cable from the back, the screen slowly fades to black, but it does not shutdown or log out. It only locks the computer.

Now to get back to my desktop, I move the mouse and up pops a 'enter password' dialog box. I enter the password and continue.

I would like to know how to disable this feature, I do not want the laptop to be locked when I unplug from the wall.

I have looked under power mgmt, login, and sessions and did not see any way to disable this.

Does anyone know how to disable this security feature?

---

### Post by batigolix on 2006-09-25
bump.

anyone knows howto disable this feature?

---

### Post by Metacarpal on 2006-09-25
I don't think this is a standard security feature.  Have you added any additional software that might have this function?

If not, then it's either something peculiar to your BIOS power management, or else it's a bug.  If you can't find anything in your BIOS settings, I'd recommend [reporting it as a bug]("https://launchpad.net/distros/ubuntu/+filebug/+login").

---

### Post by daranz on 2006-09-27
The whole fade-to-black then lock is a standard feature, except with my laptop, it happens when the lid button is pressed (ie, I close the lid), instead of the AC being plugged in. My guess is that it's some weird ACPI setting that makes it do it. While I'm not too familiar with the ACPI configuration scheme, but this is my /etc/acpi/events/ac, which is the config file responsible for events on plugging in the AC:

```
# /etc/acpi/events/ac
# Called when the user connects ac power to us
#

event=ac_adapter
action=/etc/acpi/power.sh

```

(you can check it by typing in gedit /etc/acpi/events/ac. Unless you type in sudo gedit /etc/acpi/events/ac, you won't be able to save it, though)


Of course, if the power.sh script is different on your machine, it won't help much. But, if for some reason the ac event calls the lid script, or some such, you could try changing the action to what's above. Back up anything you mess with if you're unsure.

---

### Post by PilotJLR on 2006-11-15
yopnono's post on the below link worked for me:
[http://ubuntuforums.org/showthread.php?t=242216](http://ubuntuforums.org/showthread.php?t=242216)

---

