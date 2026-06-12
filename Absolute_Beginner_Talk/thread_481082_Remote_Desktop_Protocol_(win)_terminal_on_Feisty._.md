---
title: "Remote Desktop Protocol (win) terminal on Feisty. Possible?"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-06-22
Can I connect to Windows Vista 2003 Terminal Server, using some Remote Desktop Terminal Protocol on Feisty?

I mean...
In my office, we have a Server with Windows 2003 Terminal Server, and all workers connect to a user on the server connected via Remote Desktop (no vnc). So, the only thing we do is start our terminal, and then connect to windows 2003 remotely. Can I do this with Feisty? I don't want to use Windows XP on my desktop computer.

Sorry for my english mates :P  I try my best!

---

### Post by ahvargas on 2007-06-22
You can try krdc. It work well for me.

---

### Post by Kosimo on 2007-06-22
How can I install it?
Add and remove?

---

### Post by wormser on 2007-06-22
Use apt-get in the shell.  Applications> Accessories> Terminal

```
sudo apt-get install krdc
```

---

### Post by Kosimo on 2007-06-22
> **wormser said:**
> Use apt-get in the shell.  Applications> Accessories> Terminal

```
sudo apt-get install krdc
```

Cool.
Thanks

---

### Post by Kosimo on 2007-06-22
And the last question :P

Can I join a windows domain on my network?

Samba allows this?

---

### Post by wormser on 2007-06-22
It looks like you can.
[http://ubuntuforums.org/showpost.php?p=2540611&postcount=2](http://ubuntuforums.org/showpost.php?p=2540611&postcount=2)

---

### Post by eentonig on 2007-06-22
> **Kosimo said:**
> Can I connect to Windows Vista 2003 Terminal Server, using some Remote Desktop Terminal Protocol on Feisty?

I mean...
In my office, we have a Server with Windows 2003 Terminal Server, and all workers connect to a user on the server connected via Remote Desktop (no vnc). So, the only thing we do is start our terminal, and then connect to windows 2003 remotely. Can I do this with Feisty? I don't want to use Windows XP on my desktop computer.

Sorry for my english mates :P  I try my best!

you get a default client installed who can do that. 

If you look in the aplications\Internet\Terminal Services (or something),

---

### Post by tomservo291 on 2007-06-22
Even better, use rdesktop from the command line.  The GUI that is installed by default has limited options.  By using the commandline (you can type just 'rdesktop' and it will print all of the options) you can specify custom screen resolutions and some other nifty things.

Rdesktop 1.5 is faster and better then windows own terminal services to a windows machine.

---

