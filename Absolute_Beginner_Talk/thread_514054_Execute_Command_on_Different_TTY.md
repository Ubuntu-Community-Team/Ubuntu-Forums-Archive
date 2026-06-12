---
title: "Execute Command on Different TTY"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by nhandler on 2007-07-31
I want to be able to do something like this:
On TTY1:
ls | TTY2

On TTY2 you would then see a list of all the files in the current directory of TTY1.

I know about screen and sending something to the background. But for my purposes, this would be the best solution. Is this possible?

---

### Post by steve.horsley on 2007-07-31
I did this to send data to another xterm terminal:
**ls -l > /dev/pts/0**
The command who will tell you who is logged on at which terminals. but if you are logged on in sevelal consoles, I don't know how you tell which is which. If you aren't logged in on the destination terminal then you need to be root to have write permissions to the device.

---

### Post by nhandler on 2007-07-31
That worked to output to tty1-tty6. However, I can not output to tty7 (where X is running). I am attempting to launch an application (like gedit). So I type:
gedit > /dev/tty7

I have tried that with and without sudo. Both times I get a permission denied error.

---

### Post by steve.horsley on 2007-07-31
Woosh! See those goalposts move.

What are you trying to do? Your first post suggests you are trying to pipe a text stream to a terminal, the second suggests you are trying to launch a GUI application against a specified X server. These are very different things to do. What are you trying to actually achieve?

---

### Post by nhandler on 2007-07-31
I'm trying to achieve both. I have a script running constantly on tty6. That script needs to be able to execute any type of command, text and gui, on tty7,

---

### Post by steve.horsley on 2007-08-01
Try this:

1) On the GUI console (tty7), open a terminal and execute the command:
**xhost +localhost**

2) Ctrl-Alt-F6 and log in on tty6 (as the same user as is logged in on the tty7 GUI). Then execute these two commands:
[B]export DISPLAY=localhost:0.0
xeyes &[/B]

3) Ctrl-Alt-F7 back to the GUI and notice the xeyes GUI.

If you want to pipe text to a terminal, try this:

1) On the GUI, open a terminal, and enter the command:
**who**
Make a note of the device name, probaly **pts/0** for the first open GUI terminal.

2) Ctrl-Alt-F6 and log in on tty6 (as the same user as is logged in on the tty7 GUI). Then execute these two commands:
[B]export DISPLAY=localhost:0.0
ls -l > /dev/pts/0[/B]

3) Ctrl-Alt-F7 back to the GUI and notice the directory listing in the terminal window.

---

### Post by nhandler on 2007-08-01
The first part of your post won't work for me. When I enter 'xeyes &' on tty6, I get an error saying it can't open the display. I ran the xhost +localhost command on tty7 and the export DISPLAY thing on tty6.

But the second part (text) worked great. I was able to send text from tty6 to a terminal I had open in tty7

---

### Post by steve.horsley on 2007-08-01
Dammit I forgot a bit. Sorry.

0.5)
On the GUI console, start **System->Administration->Login Window**. Go to the **Security** tab and un-check **Deny TCP connections to X-server**. 
Restart X.

---

### Post by nhandler on 2007-08-01
Thanks a Ton!

You have no idea how much this means to me. I'm so glad to have it working.

---

### Post by steve.horsley on 2007-08-01
Glad I could help.

---

