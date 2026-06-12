---
title: "Grub"
date: 2005-07-31
forum: Absolute Beginner Talk
---

### Post by lbut on 2005-07-31
I have both Windows XP and Ubuntu installed, and dual booting installed. Can I disable the 10 second count down timer when I first load windows, as I would like to choose the OS myself and not have it automatically loaded.

---

### Post by Xian on 2005-07-31
Open a terminal and enter the command below.
You need to edit the menu.lst file.

Then just comment out the line that reads 'timeout	10'.

```
$ sudo gedit /boot/grub/menu.lst
```
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout		10
```

---

### Post by lbut on 2005-08-05
Hmm I didn't manage. Can you please explain with easier language, such as load linux, open command or whatever instead of the technological words?  :-? 

Thank you

---

### Post by xmastree on 2005-08-05
It's not that difficult.

Load linux

Open a terminal by right clicking on your desktop and selecting open terminal

type this:
```
sudo gedit /boot/grub/menu.lst
```
in the terminal you just opened.

After entering your password, Gedit should open, displaying the menu.lst file

Find the line which says timeout = 10, and type a # at the beginning.

Save the file, and reboot.

That '#' at the beginning is used to preceed a comment, rather than a line of code. What you are doing is basically telling the system to ignore that line. It was a line of code, now it's a comment, like the lines above it.
You could just delete the line, that would have the same effect. But if you decide later that you want it back it's easier to do if it's still there...


Hope that's more understandable, if not don't hesitate to ask again.

---

### Post by charlieg on 2005-08-05
You can get a 'Root Terminal' from the 'System Tools' sub-menu of your applications menu.  From there you can edit (without the need for sudo) things like your grub configuration.  Root in Linux is the equivalent of administrative privileges in Windows.

Be careful if using a root terminal or even sudo (which gives you one-shot root access).  Root access is a license to kill your system if you're careless.

---

### Post by garydevitt on 2005-08-07
Hey, how do make windows my default load in GRUB? Had a look through that config file and I think ive found it but i dont want to go messing around with it just in case :)

> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0 
Im figuring I change default 0 to default 1 ?

---

### Post by xmastree on 2005-08-07
[QUOTE=garydevitt]Im figuring I change default 0 to default 1 ?[/QUOTE]If Windows is the first option, then yes, that's what you do.

Although IIRC they usually have four options:
Linux
Linux rescue
Memtest
Windows

In which case it would be '4' rather than '1'

---

### Post by vimme on 2005-08-07
4 is the right answer as 0 is the first number.

0 - Linux
1 - Linux rescue
2 - Memtest
3 - Other OS
**4 - Windows**

---

### Post by garydevitt on 2005-08-08
[QUOTE=vimme]4 is the right answer as 0 is the first number.

0 - Linux
1 - Linux rescue
2 - Memtest
3 - Other OS
**4 - Windows**[/QUOTE]
 Thanks folks!

---

