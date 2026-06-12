---
title: "nano how to save /etc/X11/xorg.conf"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by chick penguin on 2007-01-18
I am in nano 
trying to save the file /etc/X11/xorg.conf which I have edited directly
have said "yes"
how to save /etc/X11/xorg.conf in terminal window 
it says:

File name to write:/etc/X11/xorg.conf

do not know what to select to save the file.

I looked in themanual but do not understand what "meta" means in nano or how to select it from the bottom of the screen's menu
I understand ^ = Ctrl.

TIA for any help.

---

### Post by JamieC on 2007-01-18
Hey there, firstly, are you root (using sudo to run nano)?

If so, simply press CTRL + O and then hit return to save your changes to the file.

---

### Post by kebes on 2007-01-18
To save a file in nano, just exit (Ctrl+X) and when it asks to save just press "y" for yes.

However in order to save a system file like xorg.conf, you need to run nano as "root"... you can do this with the sudo command:

sudo nano /etc/X11/xorg.conf

It will ask for your password. If you provide your password, this will open nano with the authority to modify the file.

---

### Post by chick penguin on 2007-01-18
>>>running as sudo in tty2, have edited the config file and now want to save and reboot to see if I can get the xserver to work.

I just need to save the file.

It says:
File name to write:/etc/X11/xorg.conf
and is waiting with a blinking cursor for something but I do not know what to select.
I tried your Ctrl + O but nothing happened.

Thanks for your prompt reply. 

[I]> **JamieC said:**
> Hey there, firstly, are you root (using sudo to run nano)?

If so, simply press CTRL + O and then hit return to save your changes to the file.[/I]

---

### Post by JamieC on 2007-01-18
After hitting CTRL + O, hit return or enter to confirm the write to the open file. 

Nano must be running as sudo so you have permissions to write to the xorg configuration file.

---

### Post by chick penguin on 2007-01-18
When I do CTRL + O and return it asks if I want to save it under a different name
I say no and return
then I just end up back at the same line asking me what file name to write. I am just going around in a circle.

yes, sudo tty2

> **JamieC said:**
> After hitting CTRL + O, hit return or enter to confirm the write to the open file. 

Nano must be running as sudo so you have permissions to write to the xorg configuration file.

---

### Post by JamieC on 2007-01-18
Have you tried to exit (CTRL + X) and answer "yes" to the prompt to save changes?

---

### Post by chick penguin on 2007-01-18
OK
I did CTRL + X and said yes
now back to where I will do the
command
sudo /etc/init.d/gdm restart
here's hoping...

> **JamieC said:**
> Have you tried to exit (CTRL + X) and answer "yes" to the prompt to save changes?

---

### Post by JamieC on 2007-01-18
Good luck! If you followed the instructions and the file saved successfully everything should be fine.

---

### Post by chick penguin on 2007-01-18
> **JamieC said:**
> Good luck! If you followed the instructions and the file saved successfully everything should be fine.

>>>It save it OK and I was able to reboot but xserver failed to start. Tried reinstall on apt-get reinstall xserver no luck. Tried to install ati drivers that installed fine and rebooted.

Nopers, dead penguin. Have to wipe the disk and reinstall.
Thanks for your help and all the help that the posters gave.
I learned a great deal. 
Hope re live again in my next life.

---

### Post by JamieC on 2007-01-18
A reinstall was not necessary, there are several ways you could have successfully got the X server to run again (such as reconfiguring it using dpkg-reconfigure).

Anyway, be sure to follow the instructions very closely next time, and don't give up! It just takes time and lots of people here will be willing to help you.

Better luck next time.

---

### Post by chick penguin on 2007-01-18
[QUOTE=JamieC;2032627]A reinstall was not necessary, there are several ways you could have successfully got the X server to run again (such as reconfiguring it using dpkg-reconfigure).

>>>Yes, thank you I did try the dpkg-reconfigure and that did not work and also tried -phigh xserver-xorg. I tried the HZ and Vert specific numbers. editing the config file. 
Just couldn't figure out what it was.

>>>I did my best to follow the instructions exactly as I could. However, I am a green penguin and dead penguin.

---

