---
title: "My xorg.conf file is messed up  -- how do I fix it in terminal?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by satchelpig on 2007-04-23
I made an error in my xorg.conf file, and the result is that I am completely without a graphical interface now.

I am fairly sure i know what my error was, but I don't know how to get into the file and edit it without a GUI.  Can someone guide me?

Thanks.

---

### Post by nanotube on 2007-04-23
well, if you have some time, you'd want to learn some general basics of the commandline, by going through linuxcommand.org

if you want to be quick about it instead, then:
1. log in at the console, with your username and password. you will be shown a prompt that ends in '$'

2. enter command 
```
sudo nano /etc/X11/xorg.conf
```
this will launch a nice text-mode editor.

3. make whatever edit you think will help.

4. hit "control-x" to exit, and say yes to save

5. start X by issuing command
```
sudo /etc/init.d/gdm start
```
and see if that brings up the gui. 

that should get you started. :)

---

### Post by devnulljp on 2007-04-23
Reset your xorg by issuing this command on the command line.

(Drop to a trminal using cntrl-alt-F1, and log in)
then type

sudo dpkg-reconfigure -phigh xserver-xorg

then 

sudo /etc/init.d/gdm start (or kdm or just startx depends how you're set up)
That should at least get you started.

---

### Post by satchelpig on 2007-04-23
Thanks very much . . . I have my GUI back!

---

