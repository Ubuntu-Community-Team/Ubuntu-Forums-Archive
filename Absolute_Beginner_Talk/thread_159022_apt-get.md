---
title: "apt-get"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by Caligula on 2006-04-12
I'm trying to install the culmus hebrew fonts with the apt-get, but I get stuck when i'm supposed to give the command "apt-get install culmus_0.101-4_all". The Deb file is saved on the Desktop, and I'm in the Desktop...

I get this message:
> E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

I totally didn't manage to do it through the synaptics...

Can anyone help?
thanks

---

### Post by Caligula on 2006-04-12
here is what I get...

---

### Post by meborc on 2006-04-12
wait... you have downloaded the .deb file? to install a deb file you have to run the command:

**sudo dpkg -i <filename>.deb**

in the terminal... you use **apt-get **to GET stuff and install :) not to install deb files

or i didn't understand your post correctly :mrgreen:

EDIT: read this [https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto) to understand what is synaptic and what does it do... btw, synaptic is just a gui frontend for apt...

---

### Post by Caligula on 2006-04-12
here is the right one

---

### Post by meborc on 2006-04-12
see this video [http://video.google.com/videoplay?docid=5253052326994067125&q=ubuntu&pl=true](http://video.google.com/videoplay?docid=5253052326994067125&q=ubuntu&pl=true) for how to install stuff in ubuntu... also read the breezy guide in my sig (not the dapper one!)

---

### Post by Caligula on 2006-04-12
Thanks, I think I got wrong instructions earlier...
I did that, got three new lines, and that's it?
Here's how it looks:
> josh@ubuntu:~/Desktop$ sudo dpkg -i culmus_0.101-4_all.deb
Password:
Selecting previously deselected package culmus.
(Reading database ... 59150 files and directories currently installed.)
Unpacking culmus (from culmus_0.101-4_all.deb) ...
Setting up culmus (0.101-4) ...

josh@ubuntu:~/Desktop$

Does that mean it's installed?

---

### Post by Caligula on 2006-04-12
Thank's for the video, but i still don't have flash... I'll mess with that when i've got the more important stuff up and running...

I'll read the guide, thanks.

---

### Post by meborc on 2006-04-12
yes :D ... when there are no 'error messages' then the install went well... try using the font from openoffice

---

### Post by Caligula on 2006-04-12
Well,
so it did install the culmus package, I changed the keyboard layout to hebrew, but I still can't write in hebrew...
How do I switch languages?
I tried to write hebrew in openoffice, but I don't know for sure which fonts were in the culmus package, and I don't know how to change to hebrew...

what do I do?
Thanks

---

### Post by Mustard on 2006-04-12
Try this link.  I found it while searching with the keywords 'Hebrew font'.
[http://www.ubuntuforums.org/showthread.php?t=81105](http://www.ubuntuforums.org/showthread.php?t=81105)

---

### Post by MenZa on 2006-04-12
[QUOTE=Caligula]I'm trying to install the culmus hebrew fonts with the apt-get, but I get stuck when i'm supposed to give the command "apt-get install culmus_0.101-4_all". The Deb file is saved on the Desktop, and I'm in the Desktop...

I get this message:


I totally didn't manage to do it through the synaptics...

Can anyone help?
thanks[/QUOTE]

You are experiencing this because regular users aren't allowed to install.You have to do ***sudo* apt-get install culmus_0.101-4_all**.

---

### Post by Caligula on 2006-04-12
thanks,

i managed to get to write in hebrew, but no matter how much I play with the keyboard settings I can't manage to get to switch from hebrew to english with alt-shift, to write in english now I need to hold down the alt key, which is a total headache...

---

