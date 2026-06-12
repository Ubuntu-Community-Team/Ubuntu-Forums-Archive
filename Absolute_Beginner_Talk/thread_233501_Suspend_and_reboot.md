---
title: "Suspend and reboot"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by lordsteff on 2006-08-10
Hello

How can I suspend my laptop and not shutdown, but restart after the suspend? 

Thank you

---

### Post by rowanparker on 2006-08-10
What do you mean by "restart after the suspend"?
Do you mean resume or what?

---

### Post by bhoughton on 2006-08-10
Do you mean hibernate?  If so,there should be an option for it when you choose System/Quit...

---

### Post by lordsteff on 2006-08-10
I mean suspend to disk. You could probably also say hibernate or sleep.

When logging out of Gnome I can choose the Suspend option. It suspends to disks and then powers off the laptop. This is ok.

But I also need a way to suspend to disk and then reboot. The reason

1. I want to restart and boot into Windows
2. The next time I choose ubuntu, it should resume from disk to make booting faster

So I need both: Suspending and then reboot. 

I know it is possible. I used Gentoo Linux for a year now on my laptop, and I got it to work. There I used the suspend2 kernel and the hibernate script. Don't remember the exact command, but I think it was just calling "hibernate" with a restart parameter.

But on Ubuntu it does not work this way, there is not even a hibernate script. 

So: What can I do to suspend/hibernate and then restart instead of powering off?

---

### Post by bhoughton on 2006-08-10
On my desktop, when I choose "Hibernate" from the options, my box goes off.  When I hit the power button the next time, I am loaded into BIOS and should I have more than one OS (have in the past but don't currently) I would be able to choose the one to boot into.  If I choose Ubuntu, the subsequent startup is much quicker and all of my previous settings, open programs, etc are presented to me when complete.

This hopefully will do what you want to.  

Also, try making sure that in System>Preferences>Power Management, you have the first option on the "General" tab set to hibernate.

Hope this is what you are looking for.

---

### Post by lordsteff on 2006-08-10
No, I want something else. Probably difficult to explain.

The normal hibernate process is:

1. Save current state to disk (hibernate)
2. Shutdown

I want to reach following (e.g. by executing a command in the terminal)

1. Save current state to disk (hibernate)
2. Reboot (no shutdown here)

I often switch between Windows and Ubuntu, and I want to save time when Ubuntu boots the next time, thus using hibernate. But when rebooting to load Windows, I don't want to shutdown the laptop.

---

### Post by rowanparker on 2006-08-11
I see what he means but I don't know how to do it.

---

