---
title: "error during distro upgrade has crippled system"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by phobophilia on 2008-04-08
Hi all. I come here as a recent convert and fledgling penguinista who has managed to blow up my system real good-like. 

Last night, I attempted to update my system from 7.04 to 7.10. Things were going pretty well until about halfway through the installation of the new packages. when I encountered a bunch of fatal errors when it tried to upgrade evolution (and its dependent packages.) The updgrade aborted, and gave me a terminal command that I wasn't quick enough to write down and use.

I try update manager again (synaptic package manager was no help), and it says it can't find any of its sources for downloading components. I give up, and reboot (BAD idea.)
Now, whenever I attempt to boot up, I'm greeted by a blank desktop and two error messages: nautilus won't work because there's something wrong with bonobo, and bonobo won't work because something's missing/misplaced (if it helps, I'll get you the exact error messages.)
I'm stuck with a blank desktop at some ridiculous screen resolution, and my formerly fiesty fawn seems more like a shufflng member of the undead. 

I've tried poking around in recovery mode, but without a root password (which resides on a tiny strip of paper I've long sense lost), I can only get back to the crippled desktop, which is no help. 

I've also tried using the liveCD to extract my personal files from the smouldering ruins and put them on my external USB hard drive, but it says that I don't have the adequate permissions to write to that folder. But... how could I use su/sudo to copy without a set administrative account on the CD?

I'm sorry I'm so verbose, and that I haven't got the foggiest idea what I'm doing. As a true n00b, I throw myself on the mercy of ye gods of linux. Help?

---

### Post by mgranet on 2008-04-08
I'm curious. When you try to copy data to your external drive, what exactly does the error message say?

---

### Post by mister_pink on 2008-04-08
Don't know about the rest of it but you can sudo on the live CD, it doesn't ask for a password so be careful!

---

### Post by tangibleorange on 2008-04-08
> **phobophilia said:**
> Hi all. I come here as a recent convert and fledgling penguinista who has managed to blow up my system real good-like. 

Last night, I attempted to update my system from 7.04 to 7.10. Things were going pretty well until about halfway through the installation of the new packages. when I encountered a bunch of fatal errors when it tried to upgrade evolution (and its dependent packages.) The updgrade aborted, and gave me a terminal command that I wasn't quick enough to write down and use.

I try update manager again (synaptic package manager was no help), and it says it can't find any of its sources for downloading components. I give up, and reboot (BAD idea.)
Now, whenever I attempt to boot up, I'm greeted by a blank desktop and two error messages: nautilus won't work because there's something wrong with bonobo, and bonobo won't work because something's missing/misplaced (if it helps, I'll get you the exact error messages.)
I'm stuck with a blank desktop at some ridiculous screen resolution, and my formerly fiesty fawn seems more like a shufflng member of the undead. 

I've tried poking around in recovery mode, but without a root password (which resides on a tiny strip of paper I've long sense lost), I can only get back to the crippled desktop, which is no help. 

I've also tried using the liveCD to extract my personal files from the smouldering ruins and put them on my external USB hard drive, but it says that I don't have the adequate permissions to write to that folder. But... how could I use su/sudo to copy without a set administrative account on the CD?

I'm sorry I'm so verbose, and that I haven't got the foggiest idea what I'm doing. As a true n00b, I throw myself on the mercy of ye gods of linux. Help?

about the recovery mode - why does your root account have a password? in default ubuntu setups, your root account doesn't have a password. what happens when you boot into recovery mode?

---

### Post by phobophilia on 2008-04-08
I'm afraid I couldn't tell you *exactly* what it says- I'm kind of at my university's computer lab at the moment. It just says something like "You do not have adequate permission to write to this folder", and I really don't remember setting any sort of access permission on that drive.

---

### Post by mgranet on 2008-04-08
If you can perform a console login, you should be able to write to your external. It's probably a LiveCD issue that's preventing it.

---

### Post by phobophilia on 2008-04-08
> **tangibleorange said:**
> about the recovery mode - why does your root account have a password? in default ubuntu setups, your root account doesn't have a password. what happens when you boot into recovery mode?

(lines and lines of "driver x is starting for y", etc., and then: )
Give root password for maintenance
(or type Control-D to continue):

Ctrl D gets me to the regular login screen. If I log in, I get:
(popup window): Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to register the file manager view server.

(popup window): The panel has encountered a fatal error. The panel could not register with the bonobo-activation server (error code: 3) and will exit. It may be automatically restarted.

If I click ok, I get the blank desktop.

I set a root password because (quite frankly) I am/was a paranoid n00b. The root password as I wrote it down (found it!) does not work- I think I may have reset it. (Once again, more n00b brilliance on my part.)

---

### Post by mgranet on 2008-04-08
sudo is a very secure method of performing administrative tasks. There is no need to set a root password. Even if you are paranoid. You are probably best in saving your data through the console, and then starting with a fresh, clean install of 7.10.

---

### Post by tangibleorange on 2008-04-08
> **phobophilia said:**
> (lines and lines of "driver x is starting for y", etc., and then: )
Give root password for maintenance
(or type Control-D to continue):

Ctrl D gets me to the regular login screen. If I log in, I get:
(popup window): Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to register the file manager view server.

(popup window): The panel has encountered a fatal error. The panel could not register with the bonobo-activation server (error code: 3) and will exit. It may be automatically restarted.

If I click ok, I get the blank desktop.

I set a root password because (quite frankly) I am/was a paranoid n00b. The root password as I wrote it down (found it!) does not work- I think I may have reset it. (Once again, more n00b brilliance on my part.)

ok. you should still be able to use sudo to run root commands. try this:

[LIST]
[*]log in to the blank screen you mentioned earlier
[*]press ctrl+f1 - that should take you to a CLI login - login with your regular username and pass (not root)
[*]try copying your folders to an external drive with the command prefixed with sudo.
[/LIST]

---

