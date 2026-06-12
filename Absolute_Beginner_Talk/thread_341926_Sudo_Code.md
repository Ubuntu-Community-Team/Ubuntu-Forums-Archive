---
title: "Sudo Code"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by Dave-C on 2007-01-19
I'm a newbie and really liking linux and learning alot of sudo code is there any way of like writing some sudo code then saving it like a file so when you click it, it will run your sudo code 
? like using dos on windows where you can save it as a file then click and it will perform a task in dos

---

### Post by Nik_Doof on 2007-01-19
You can write a script and save it as <filename>.sh , then you should be able to click and run. 

The first line of your script will have to include:

> #!/bin/sh

Scripting via one of the shells is very powerful, take a look at the [Bash Scripting Introduction Howto]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html").

Only problem I can think of is inputting your sudo password, but it depends on how it runs (it should run via Terminal).

---

### Post by pizzutz on 2007-01-19
Is it code that actually needs to be run with sudo, or just terminal command in general you mean?  you can put root-only commands in a script file without the sudo prefix and simply run the file from the terminal with sudo.

```
sudo ./<filename.sh>
```

it will prompt for the password once then run the script as root, however you should be careful with this.  You shouldn't be running commands as sudo unless absolutly necessary, and then you should be sure to know what you are doing as you can do serious damage to your OS that way, and Linux will NOT give a friendly "Warning! this will erase your entire filesystem permanantly. Are you sure [Y/N]".  It will just do it.

---

### Post by jd65pl on 2007-01-19
I wrote a document on simple bash scripting earlier today it might help you understand a few things please click this link, it is a pdf... [http://jamie.dumbill.googlepages.com/revdoc6.pdf](http://jamie.dumbill.googlepages.com/revdoc6.pdf)

---

### Post by Dave-C on 2007-01-19
am not doing nothin serious i dont think i have a problem loading usb's so i'm using 

fdisk -l
sudo pmount /dev/sda1 USB

to mount it and 

pumount /dev/sda1 

to unmount just wanted to make it easy

---

### Post by Dave-C on 2007-01-19
is there anyway or writing that code in like a text document and saving it so it runs when i open it like saving it on text editor then saving as a file type that will run it in terminal

---

### Post by jd65pl on 2007-01-19
Follow my document it is not hard to follow and will help you to make a script for what you want.

Thanks

---

### Post by po0f on 2007-01-19
Dave-C,

For mounting filesystems, it would be much easier to just add a relevant entry to /etc/fstab, so you could just type `mount /media/files` (or whatever) and `umount /media/files`.

```
[FONT="Courier New"]/dev/sda1 /media/files ext3***** defaults,noauto,user 0 0[/FONT]
```
*: Change ext3 to whichever filesystem the partition actually uses.

---

### Post by bodhi.zazen on 2007-01-19
> **jd65pl said:**
> I wrote a document on simple bash scripting earlier today it might help you understand a few things please click this link, it is a pdf... [http://jamie.dumbill.googlepages.com/revdoc6.pdf](http://jamie.dumbill.googlepages.com/revdoc6.pdf)

sounds good, but the document was only 2 pages long and looked incomplete. ? ?

---

### Post by jd65pl on 2007-01-19
Yeah I''m half way through it it should be finished on monday, I might put it on the web when its finished.

---

