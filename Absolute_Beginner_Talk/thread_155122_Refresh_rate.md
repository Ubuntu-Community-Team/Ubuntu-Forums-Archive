---
title: "Refresh rate"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by Griffer on 2006-04-04
Okay i have installed ubuntu on my old b/w powermac g3, but sadly i only have a really old tft monitor at the moment, which only allows i think it's 60 or 70 hz aignal. I get to the load screen, and then the system changes refresh rate and my screen goes black.

Is there anyway to change the refresh-rate before the system boots?

---

### Post by IYY on 2006-04-04
Make sure your /etc/X11/xorg.conf file is configured properly, with appropriate horizontal and vertical frequencies.

---

### Post by Randomskk on 2006-04-04
If you login in "single user mode" from the GRUB menu (the bootloader), you will be logged in as root.
Now, type:
nano /etc/X11/xorg.conf

The file's kinda big, but look through to where the refresh rate is set (can't remember exactly where right now) and change it, then I think the command to save is F2, hit y then enter, then reboot.

Good luck!

---

### Post by Griffer on 2006-04-04
Wow that was fast :).

I don't really know how to enter single user mode. When the bootloader starts i get the option to boot into linux, and boot on cd...

---

### Post by Randomskk on 2006-04-04
Choose to boot linux, and you should see a screen something like "press esc to load the menu" or something (I've only seen it once, and then briefly) - you need to get to a menu that has a few different Ubuntu options, and one of them is Recovery Mode, choose this (if there are multiple ones, choose the Recovery Mode nearest the top)


edit: I've just seen that you're on a Mac, so I'm not sure if you installed the GRUB bootloader?
I don't know how the Mac version installs, but I'd assume there's a similar method to enter single user mode. While booting, look for any text prompting you to press a button to get a menu.

---

### Post by Griffer on 2006-04-04
Hmm i only get a "welcome to yaboot version 1.3" message.
And if i press enter ubuntu boots, if i type "help" it describes how you choose another boot disc. But maybe some other command could get me into single user mode

---

### Post by IYY on 2006-04-04
How about you try rebooting normally, and when system gets to the login screen, press Ctrl+Alt+Backspace. This should switch to terminal-mode where you can login and make changed to /etc/X11/xorg.conf using the nano editor.

---

### Post by Griffer on 2006-04-05
Hmm i tried pressing ctrl+alt+backspace, and nothing happens, my screen still tells me that the input signal is out of range...

---

