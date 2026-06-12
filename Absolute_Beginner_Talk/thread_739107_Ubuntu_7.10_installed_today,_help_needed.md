---
title: "Ubuntu 7.10 installed today, help needed"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by robintoal on 2008-03-29
Afternoon my potential saviors,

I have just installed Ubuntu, Gutsy Gibon I believe, and I have a number of issues i'm hoping somebody will be able to help me with. 

1. Resolution options - It's all too big, and I need to be able to increase the resolution but the options only allow for the current or one size smaller. The monitor is new and was cool when working with vista, although nothing else was. 

2. Installing new programs - When I try to install a new program, Limewire - just in case I need to switch to XP, the package installer tells me that only one software management tool is allowed to run at the same time, please close synaptic or others. As far as I can tell I am not running any other tools, and I have restarted my computer to try to ensure that. I don't seem to have a task manager so I don't know how to confirm if another program is running. 

3. External hard drive - I have an external hard drive with everything I saved from my previous vista installation, but I cannot mount the drive. NTSF is marked to be in use. It tells me to this mount -t ntfs-3g /dev/sdb1 /media/disk -o force, I do this through terminal but i'm informed that only root can do that.

Any and all assistance will be welcomed! RT

---

### Post by 505 on 2008-03-29
1. You probably need the correct video drivers for your card. What kind of video card do you have?

2. Wait a bit after booting your computer. Ubuntu checks for upgrades after the boot, thus a package manager is running then. You do have a task manager, it's under Applications->System tools->System monitor.

3. Prefix that command with 'sudo' to run the command as root, thus 'sudo mount -t ntfs-3g /dev/sdb1 /media/disk -o force' they type *your* password.

---

### Post by Inxsible on 2008-03-29
1) What graphics card do you have ?
2) You can only run 1 software installation at a time. So you cannot have Add/Remove and Update Manager and Synaptic Package Manager open at the same time, if you want to install something.
3) Put a sudo in front of the command and it will work

---

### Post by Mauler5858 on 2008-03-29
For mounting the hard drive add ```
sudo
``` before your command.

---

### Post by Dr Small on 2008-03-29
3. The simplest way, would be to open up Nautilus (the file browser) and on the sidebar, mount the external drive (if it is there, of course).

---

### Post by robintoal on 2008-03-29
In reverse order, 

3. - it seemed to complain a little bit, forced mount, unclean shutdown, but whatever it works. I'm really impressed by this whole forum thing, certainly quicker than calling microsoft. 

2. When I first installed it did install a load of updates and it seems to have finished. I have rebooted several times since. On a fresh boot, I try to install without doing anything else and I still get the same message. I do not have a system tools option under my applications drop down bar, so I cannot check if either the update manager or the package manager are running. I'm definitely not in the add/remove section either. Only this problem left! 

1. It is an nvidia graphics card, i got warnings saying that it wasn't supported but I had an option to enable it, which is what I did but too little effect. How would I find out the exact card so I could find the drivers? - Scratch that, I went to the screen resolution and just changed it, my apologies. 

RT

---

### Post by ugm6hr on 2008-03-29
1. Have you found the "Restricted Drivers"?  They will install a proprietary driver for you.

If that didn't work, post the output from:
```
lspci
```

This will tell us what your graphics card is.

2. How are you trying to install?  From Add/Remove, Synaptic, dpkg...

Not sure I know how to resolve this problem.

3. External HDs should automount if you plug them in after booting.

Otherwise, you can mount it from Places->Computer (double-click on the correct disk)

---

### Post by Inxsible on 2008-03-29
The System Monitor is under System>>Administration>>System Monitor

---

### Post by robintoal on 2008-03-29
I am trying to install by opening the limewire.deb folder, which produces the package installer - the status is all dependencies are satisfied. 

And just as I was about to tell you the full error, it works! You guys collectively are ace, my huge electronic appreciation. RT

---

