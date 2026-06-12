---
title: "How do i edit files in the file browser"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by smokeysaysno on 2006-07-13
Hey Ubuntu community, I've got an easy one that's been driving me up the wall.  I'm a brand new linux user, longtime windows/dos user.  I can't figure out how to edit, delete or move them within the file browser.  All that i can do is fool around with the programs in my home folder.  There are a lot of fixes that require you to edit files in these other directories, and as a windows user I could have fixed things in a snap.  I guess i still feel more comfortable doing that than doing it in the terminal.  How do i get the administrative access to change or delete these files??

---

### Post by GarethMB on 2006-07-13
I'm assuming you're using gnome. Type this into a terminal or press alt + f2 and type it in the dialogue that results.

```
gksudo nautilus 
```

gksudo is the command that we use whenever a GUI program needs to be run with root permissions. You use it without realising when you choose synaptic from the menu.

---

### Post by slimdog360 on 2006-07-13
you want to edit files   sudo gedit /.../.../nameoffile.prefix
remove something         sudo rm /.../.../nameoffile.prefix
copy something           sudo cp /.../.../nameoffile.prefix
there is plent of guides out there.

---

### Post by RhettBastid on 2006-07-13
use the **su**or **sudo**command to change to the root user.  You will be prompted for a password.  To edit text in the terminal, use nano, pico, or vi.  Nano and  pico are easier for beginners since they have commands listed at the bottom of the screen.  Type in for example:

sudo nano filename
password

or 

su
password
nano filename

It is a good idea before changing the contents of a config file to save it with a different filename such as filename.orig or filename.old.  That way if you screw it up, all you have to do is rename the filename.old file back to filename and the world is right again.

a note about the commands listed at the bottom of nano and pico:

The commands look like ^w, ^x, etc.  The ^ refers to the control key, so ^w means ^+w.  They also don't use words like save or save as.  Write means save, etc.

---

### Post by GarethMB on 2006-07-13
The op wants to browse the files he wants to edit as root in the file browser. The op also wants to avoid CLI. Neither of the methods you have recommended allow this.

gksudo nautilus is the best answer to the question the op asked.

---

### Post by slimdog360 on 2006-07-13
> **GarethMB said:**
> The op wants to browse the files he wants to edit as root in the file browser. The op also wants to avoid CLI. Neither of the methods you have recommended allow this.

gksudo nautilus is the best answer to the question the op asked.
give yourself a wrap why dont ya. 

Linux is built around the terminal so Id recommend throwing your self in the deep end and trying to solve problems that way. You will learn a lot faster.

---

### Post by bailout on 2006-07-13
Not a lot of help to you really, but probably as much as people telling you how to edit files in terminal when specifically say you don't want to do this;), but Konqueror, the kde file manager, has the ability to open files as root in a graphical editor. It really does make doing a quick edit to a config file much easier.

---

### Post by smokeysaysno on 2006-07-13
Awesome, it worked.  Thanks!  I did get this message though.

(nautilus:25561): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Is that anything serious?  And i also noticed you used the prefix gksudo, is that different than using sudo?

---

### Post by bailout on 2006-07-13
sudo is for the command line and gksudo should be used when opening a gui program in su mode

---

### Post by GarethMB on 2006-07-13
> **slimdog360 said:**
> give yourself a wrap why dont ya. 

Linux is built around the terminal so Id recommend throwing your self in the deep end and trying to solve problems that way. You will learn a lot faster.
Not everyone wants to learn the command line. It might not always be the fastest way to achieve a task. I use it when i want and i avoid it when i don't. As we have a choice, and ubuntu is all about choice, I see no point in pretending that options other than the terminal exist.

I may not have used ubuntu for long. But in my time, I've noticed increasingly the number of graphical ways of interacting with files increasing. In fact, it's probably possible once everything is set up to never have to use the terminal. Which is the way it's going to be if linux is ever going to get itself a dominant share of the desktop market: Not everyone has time to learn CLI.

As for this:

> 
GnomeUI-WARNING **: While connecting to session manager:
 Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
 
Is that anything serious? And i also noticed you used the prefix gksudo, is that different than using sudo?
This always appears whenever you use gksudo nautilus. I don't understand it but I've never had any ill effects from using this command, so don't worry about it. If I was to guess I'd say it's warning you that the file browser has root powers.

This is probably why everyone would recommend you to use the terminal, because you won't accidentally delete an important file. Just be sure to back up anything that you edit, that's remotely important before you start.

---

### Post by smokeysaysno on 2006-07-13
@ GarethMB

Thanks for your help.  It's exactly what i was looking for.  I'll definatly be using the CLI as I become more comfortable with it, but coming from a strictly windows background it's easier right now to work in nautilus.  

@ubuntu community  

Thanks for the other ways to do it.  Ubuntu rocks!

---

### Post by GarethMB on 2006-07-13
> **smokeysaysno said:**
> @ GarethMB

Thanks for your help.  It's exactly what i was looking for.  I'll definatly be using the CLI as I become more comfortable with it, but coming from a strictly windows background it's easier right now to work in nautilus.  

@ubuntu community  

Thanks for the other ways to do it.  Ubuntu rocks!
I totally agree with you. I was in your position just a few months ago. And doing everything by the terminal the first time you've done it is tough. Adjusting to a new file system structure takes time. And folders such as /etc /lib /usr crop in many places, which can confuse. After using gksudo nautilus, you're knowledge of the file system and your confidence will grow and you'll feel more comfortable.

---

