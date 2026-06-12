---
title: "How do I add lines?"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by nothingspecial on 2008-02-21
When following how tos and guides it often says words to the effect of -
  Add these lines to your /ect/apt/sources.list or something similar.

For example in a how to about webcams it says
add the line modprobe drivermodulename to /etc/rc.d/rc.local to enable the camera at boot time.

How do I do this , not just that instruction, but in general.
And what am I doing when I add lines to /blah/blah/blah

Thanks in advance.  I`m ready to start understanding what I`m doing instead of just copying and pasting thoughtlessly the whole time.:)

---

### Post by Liet_Kynes on 2008-02-21
To add lines to a file means the following. eg. To add the line blah blah to /etc/blah you do the following.
```
sudo gedit /etc/blah
```

This will open up a text editor with the file /etc/blah in it. You then type in the line "blah blah" in that file. Save it and exit.


That might be a bit of oversimplification.

sudo means you running the command as the root (administrator) user. gedit is the text editor.

I hope that was clear if not I'll try again :)

---

### Post by FrozenFox on 2008-02-21
EDIT: Liet answered a quarter of a second before I pressed submit. ;)

---

### Post by jan quark on 2008-02-21
if you want to get further pieces of information about a specific command you can run
```

man command
```

in terminal to open a manual describing the functions and the syntax of the command
you leave the manual pressing 'q'

---

### Post by nothingspecial on 2008-02-21
I think I get it. Thanks guys!:guitar:

---

### Post by drs305 on 2008-02-21
From the command line, the easiest way to add a line to a text-type file is simply:
```
echo "type the line you want entered" >> /filepath/filename
```
Example: echo "add this line" >> /home/username/myfile

If you need to add a blank line to the end of a file:
```
echo "" >> /filepath/filename
```
(Quotes without a space)

If you need to add it to a system file, preceed echo with sudo.

---

