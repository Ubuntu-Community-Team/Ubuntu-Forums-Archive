---
title: "How to open/edit an internal/external application??"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by davidwfox on 2007-06-19
I recently wanted to edit my Grub bootloader, to get rid of surplass menu entries (as a result of the recent kernel update/upgrade). I joined an existing thread wherein the thread originator had been advised to edit his bootloader using:
gksudo gedit /boot/grub/menu.lst

So, I did the same thing and in reporting the results of this I was advised by another respondent:
(Try to avoid opening external applications from the terminal requiring superuser privileges with just 'sudo'. Better to use 'Run Application' gui.).

Rather than pursue the topic in someone else's thread, I've opened this one.

I want to progress my understanding of Linux / Ubuntu and in order to do this I need to understand what I'm doing and why. So:
1,  How do I determine what is an external application and what isn't? If it isn't external, what is it - internal?
2.  What command do I use to open an external app and why?
3.  What command do I use to open a non-external app and why?
4.  Where (in U 7.04) do I find the "Run Application" GUI?

---

### Post by dreadlord_chris on 2007-06-19
> **davidwfox said:**
> I recently wanted to edit my Grub bootloader, to get rid of surplass menu entries (as a result of the recent kernel update/upgrade). I joined an existing thread wherein the thread originator had been advised to edit his bootloader using:
gksudo gedit /boot/grub/menu.lst

So, I did the same thing and in reporting the results of this I was advised by another respondent:
(Try to avoid opening external applications from the terminal requiring superuser privileges with just 'sudo'. Better to use 'Run Application' gui.).

Rather than pursue the topic in someone else's thread, I've opened this one.

I want to progress my understanding of Linux / Ubuntu and in order to do this I need to understand what I'm doing and why. So:
1,  How do I determine what is an external application and what isn't? If it isn't external, what is it - internal?
2.  What command do I use to open an external app and why?
3.  What command do I use to open a non-external app and why?
4.  Where (in U 7.04) do I find the "Run Application" GUI?

1 - I think they are refering to GUI apps as *external* - basically because they *detach* themselves. An *internal* command, then would be one that is typically run from the command-line & has no graphic interface.

2 - from the command-line it's preferable to use gksudo (kdesu for KDE) to launch GUI apps that you need admin privilages for - because it's designed for it's use.

3 - use sudo to launch terminal commands that you need admin (root) privilages for - sudo's there as a layer of protection

4 - press ALT-F2 - you can also add a run applet to the GNOME panel

I think one of the main reasons that it's recommended to run GUI apps from "Run Application" rather then a terminal - with "Run App" you don't have to leave the terminal open while your app is running.

---

