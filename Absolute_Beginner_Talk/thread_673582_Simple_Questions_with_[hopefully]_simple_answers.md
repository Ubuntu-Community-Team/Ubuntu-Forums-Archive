---
title: "Simple Questions with [hopefully] simple answers"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by MoonDoggie on 2008-01-20
Hello Ubuntu friends,
    I am an experienced computer user who is just diving into linux.  I have some simple questions I would like explained if possible.  Let me take a moment to thank all of you veterans for posting in "Absolute Beginner Talk" to share your experience, as agonizing as it can be sometimes I'm sure.

To my questions:

Firstly, I had problems after my initial install of Gutsy.  I was having all kinds of ```

ata3.00: revalidation failed (errno=-5)

```
errors, etc.  With the help of the threads in this forum I was able to fix it easily by booting from the cd then
```

sudo cp /etc/initramfs-tools/modules /etc/initramfs-tools/modules.backup
gksu gedit /etc/initramfs-tools/modules

```
and adding the line
```

piix

```
to the bottom and then 
```

sudo update-initramfs -u

```
and rebooting.  This fixes all my errors upon bootup (Thanks to all who replied in threads about this problem) and gets me up and running.  

1.  This is a problem because I'm not sure what I'm actually doing when I do these commands and would appreciate some kind of explanation as to what I'm doing (the reoccurring theme "if you give a man a fish...")

2. Now I'm configuring my ATI graphics card in dual-head mode, trying to get it to recognize my full resolution on both monitors and when I reboot sometimes, my /etc/initramfs-tools/module file sometimes reverts back to normal (ie. no "piix" at the bottom) forcing me to reboot to cd and do the process all over again, I'm not sure why it does this, but it takes 5+ minutes to boot from the cd with all the ata errors.  Is there a better solution or at least one that would stick?

3. My ATI graphics card is detecting my primary monitor incorrectly (I'd rather it be my large 1680x1050 display, rather than my 1280x1024 display) I've looked through threads and found the ```
--display-type=horizontal,reverse
``` but that just switches which side the monitor thinks it's on (left or right), is there a way to have it switch my primary and secondary display altogether? 

Thank you for taking the time to read my (hopefully) simple questions and respond,
Colin


My Setup:
Linux/XP dual boot
Linux on seperate 400gb SATA HD partitioned: /, /home, /swap
Mobo: Asus P5WDH Deluxe
CPU: Intel Core 2 Duo e6600 (oc to 3.00ghz)
Memory: 2gb Corsair 6700 memory

---

### Post by shearn89 on 2008-01-21
Not sure about 2 and 3, but i can explain the commands to you!
```

sudo cp /etc/initramfs-tools/modules /etc/initramfs-tools/modules.backup

```
This changes to the root user (the admin) **<sudo>**, and backs up the file **<cp ....>**. This is so if we break it, we can fix it!
```

gksu gedit /etc/initramfs-tools/modules

```
This says "switch to root user" (**gksu**), and edit the file /etc/initramfs-tools/modules (**gedit <file>**). "gksu" is used in preference to sudo for graphical applications, for a reason i'm not 100% certain why. Its something to do with loading profiles or switching environments or something... Its good practice to use **gksu** for graphical stuff and **sudo** for cli stuff.

Adding the line "piix" to the bottom is probably telling the initramfs to load the module at boot. **initram** is the bit that handles all the booting and loading when the computer starts, and is hidden behind the smooth orange "loading" bar on the boot splash screen.

```

sudo update-initramfs -u

```
This says "switch to root user", and update the initramfs image.  I'm not certain what the -u switch does, try typing 
```

update-initramfs --help

```
into a terminal and see if that tells you.

I find the easiest way to learn about a command is either to add a "--help" switch to the end, or try "man <command>" which will show you the manual pages for it.

---

### Post by MoonDoggie on 2008-01-21
shearn89,
Thank you very much for sharing the knowledge that you knew!  I'll continue learning and expanding on this.  In reply to your message what is ```
piix
```?  I've googled it and found ```
ata_piix
```
 but no normal piix.  What is it and why does my computer need to load it to boot up correctly?  Just curious, and why won't my changes to /etc/initramfs-tools/modules stick?  :)

Thanks again shearn89,
Colin

---

### Post by shearn89 on 2008-01-21
i'm not sure. You could try adding ati_piix as well as/instead of piix. Also, make sure you're editing /etc/initramfs-tools/modules as root (sudo before hand), and make sure you save before exiting. Small things, but i often forget them.

---

### Post by dstew on 2008-01-21
initramfs = "Initial RAM file system". It is an abbreviated Linux system that is loaded as-is into memory, to start the boot process.

---

