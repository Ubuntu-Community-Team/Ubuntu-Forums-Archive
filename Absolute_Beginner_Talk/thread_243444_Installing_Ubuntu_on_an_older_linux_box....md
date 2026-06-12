---
title: "Installing Ubuntu on an older linux box..."
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by recycle on 2006-08-25
I was able to install Ubuntu on an old notebook at work with the dual-setup (Ubuntu/Windows XP). An after using it and liking it, I've decided to install it on an old Linux box I have, but which I haven't used in a couple of years. The box is running RedHat 7.1 and it prompts me to login once it boots up. The problem is I don't remember the username and password. Also, the BIOS isn't setup to detect the CD-rom first so it isn't reading the Ubuntu CD. When RedHat is booting up, I can type Ctrl-x to get a prompt that reads "boot:". If I hit enter or type linux, then RedHat continues to boot. What can I type at this prompt to get it to read the CD-rom instead?

---

### Post by bullgr on 2006-08-25
can you setup the bios to boot from cd first? or is it not supported? how old is your pc?

in my PII 350 i can setup the bios to boot from cd first...

and by the way... it's better to install xubuntu in a old system, if you install ubuntu with gnome when the system will be very slow.

---

### Post by Jerome36 on 2006-08-25
To have the computer read the CD Rom drive, before the hard drive, you're going to have to enter the BIOS and change it there.  When you first start the computer, BEFORE Linux even begins to boot, the BIOS will run through its checks.  Somewhere on the screen you should see something like "Press F2 to enter setup."  It varies from computer to computer.  Some require you press F2, others F12, DEL, etc.

Also, like bullgr suggested, you might want to consider Xubuntu, rather then Ubuntu.  I don't know what your system specs are, but Xubuntu uses the Xcfe desktop enviornment, rather then Gnome (in Ubuntu).  Xcfe is lighter and less demanding then Gnome, so it's better for older systems.

---

### Post by amo-ej1 on 2006-08-25
Can you identify the bootloader ? According to me the old Red Hat has installed lilo and not grub (the main difference is that with grub you can edit some settings on the fly, with lilo you can't). The way to recover access to the machine can be fairly simple, you simply enter "linux single" at the boot prompt, this will boot the machine in single user mode and you'll be able to recover your password. But this won't get your much further with your booting issues. 
The fastest solution might be to remove the harddisk, put it in a newer (faster) machine, install ubuntu from on that machine and insert it back in the old machine. This will offcourse require you to redo some auto detection (mainly X server related).  But this will get you started. 
Other options are: install grub  from the recovered red hat en trick grub into booting from the cd or try to get the installer to work from the recovered red hat (but i'm totally unsure if this works or even is possible)

---

### Post by recycle on 2006-08-25
> **bullgr said:**
> can you setup the bios to boot from cd first? or is it not supported? how old is your pc?

in my PII 350 i can setup the bios to boot from cd first...

and by the way... it's better to install xubuntu in a old system, if you install ubuntu with gnome when the system will be very slow.

Thank you for the help.

i think i need to be logged in to be able to change the BIOS, unless it can be changed during the boot up process.  i'm not able to log in since i can't remember the username/password and i haven't seen anything in the boot up sequence that would allow me to access or change the BIOS.

the pc is about 4 years old. it has an Intel Celeron CPU.

---

### Post by bullgr on 2006-08-25
ok, if like you say it's 4 years old then you can change the boot priority from the bios...

start the computer and hit the "del" key until you go in bios (in some motherboards you need to press "F12", see the screen then you start you pc what is writen).

in the bios change the boot priority to first boot to cd...

after that put the ubuntu cd in the cd-rom drive and restart the pc to install ubuntu (your pc is not so old, you can install ubuntu).

you don't need to login to your old installed linux...

---

### Post by amo-ej1 on 2006-08-25
indeed, you should be able to access your bios by hitting one of the F-keys at startup (should be printed on the screen), after that you should simply change the boot order of the drivers. I don't think it would even be possible (ipmi and such excluded) to change the boot order from within a linux system.

---

