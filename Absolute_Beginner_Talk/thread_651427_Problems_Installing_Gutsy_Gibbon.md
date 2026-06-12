---
title: "Problems Installing Gutsy Gibbon"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by curlyt on 2007-12-27
Hi all,

I'm brand-new to Linux / Ubuntu, trying to see what all the fuss is about.  I have an older laptop I'm dedicating to this project, so I installed from the alternate installer CD and nuked XP, for what I thought would be maximum chance of success.  Installer worked OK, but when I rebooted to run for the first time, I get dumped out to some sort of text screen.  First, there's some language about Irqpoll and the message that "nobody's listening."  Then, I see a list of actions, like "Starting ACPI Services [OK]" and "Running Local Boot Scripts [OK]."  Then there's a text prompt for my username and password that I added, which it accepts.  Then, I get a prompt with my username and ~$.  What am I supposed to do here?  How do I get to a GUI interface?  

For the irqpoll message, I tried adding "irqpoll" to the kernel commands on the "grub" boot menu -- doesn't seem to work?  

Any thoughts or help?  I really want to try this out.

---

### Post by p_quarles on 2007-12-27
What happens when you run this command? (this will attempt to start the desktop manager):
```
sudo /etc/init.d/gdm start
```

---

### Post by spiderbatdad on 2007-12-27
i think noirqpoll  might be what you're looking for. If you post what type of laptop and some specs it might be easier to diagnose the problem.   There is a list of boot options under F1 F6. I've had luck with that cd on an older HP laptop by entering F6 at the grub screen and deleting rw quiet splash --    and inputing "noapic nolapic vga=771"  just like that with no quotes or --  or anything else, and starting right from where "rw" previously began.

---

### Post by irv on 2007-12-27
Try typing this at the prompt:
> sudo start x
You will be asked for your password.

---

### Post by curlyt on 2007-12-27
> **p_quarles said:**
> What happens when you run this command? (this will attempt to start the desktop manager):
```
sudo /etc/init.d/gdm start
```

I get:
"sudo: /etc/init.d/gdm: command not found"

---

### Post by curlyt on 2007-12-27
> **irv said:**
> Try typing this at the prompt:

You will be asked for your password.

That gives me:
"Unknown job x"

---

### Post by p_quarles on 2007-12-27
Did you perhaps install the server version of Ubuntu? 

Anyway, it really looks like the GUI is simply missing from this computer. Try installing it:
```
sudo apt-get install ubuntu-desktop
```
This will take a while to download and install, but it should fix the problem.

---

### Post by curlyt on 2007-12-27
> **spiderbatdad said:**
> i think noirqpoll  might be what you're looking for. If you post what type of laptop and some specs it might be easier to diagnose the problem.   There is a list of boot options under F1 F6. I've had luck with that cd on an older HP laptop by entering F6 at the grub screen and deleting rw quiet splash --    and inputing "noapic nolapic vga=771"  just like that with no quotes or --  or anything else, and starting right from where "rw" previously began.

It's an older machine, IBM Thinkpad, 1 ghz Celeron with 500 megs of RAM.  8GB hard drive.

I will try the "noapic nolapic vga=771" commands.

---

### Post by spiderbatdad on 2007-12-27
have you restarted with the cd in and tried entering the proper boot parameters?

---

### Post by irv on 2007-12-27
> **curlyt said:**
> That gives me:
"Unknown job x"
My mistake type
> sudo startx
No space, startx is all one.

---

