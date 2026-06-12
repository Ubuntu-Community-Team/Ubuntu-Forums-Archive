---
title: "Sudo launcher"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by k3pp0 on 2006-11-29
Hi there, here is my first nobbie question:
in ubuntu I download and installed moz thunderbird.
First time i run it from shell with sudo ./thunderbird.
Everything was ok, i configure it all and worked perfectly.
Then i came to make a nice desktop launcher.
Here is the problem: giving the command (in launcher properties) /home/.././thunderbird the program starts, but there are no settings stored, it runs as it was the first time.
if i chenage the command in "sudo /home/..././thunderbird" the launcher works  only if i have typed some time before a sudo command in terminal.

How can i make a launcher command run with sudo? 


Tnkx!!

---

### Post by slimdog360 on 2006-11-29
Have you tried changing the permissions of the folder?

sudo chmod 777 -R /home/.../thunderbird

---

### Post by Obor on 2006-11-29
Welcome to Ubuntu :) 

Because you run thunderbird as a root (using sudo) when you done your settings - your profile is owned by root. You should run it without sudo when you setting it up to make yourself the owner instead of root. 

You shouldn't run graphical programs using sudo anyway. [Check here about graphical sudo.]("http://www.psychocats.net/ubuntu/graphicalsudo") 

Edit: Or change permissions as above.

---

### Post by k3pp0 on 2006-11-29
Thanks for replyes :)
Think I wille reconfigure it all for launching without sudo command.
Now I'll search for a fast way to transfer thund. settings and mail...it should be enough to copy all data folder into new profile folder...i think...

---

### Post by mcduck on 2006-11-29
from this on, you'll also most likely want to use Ubuntu's own package manager to install applications. Just check Applications/Add/Remove and System/Administration/Synaptic Package Manager..

Here's a nice guide how to install apps the easy way: [http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

