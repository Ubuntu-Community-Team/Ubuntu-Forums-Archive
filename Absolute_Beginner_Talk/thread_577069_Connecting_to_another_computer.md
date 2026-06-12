---
title: "Connecting to another computer"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by ariodante on 2007-10-15
My school gives the following instructions for people wanting to download software from one of their websites:

[INDENT][I]1. Click on  "Start" and choose "Run..."

2. Type \\babs.its.yale.edu\msdn-iso in the Run... box and hit ENTER.

There are two backslashes in front of "babs.its.yale.edu" and one backslash between ".edu" and "msdn-iso". Do not use any spaces or other punctuation.

3.  IMPORTANT: If you are asked to log in, enter your netID with the word "yale" and a backslash "\" in front of it.

For example, if your netID is "zzz321", you would enter yale\zzz321 as your user name.

4.  After a few seconds, a window should appear with a list of files in it.
[/I][/INDENT]

If I want to connect to the same computer using Ubuntu (I have a VPN set up), what do I need to do?  What software do I need to have installed and how do I use it to connect to the computer listed above?

Thanks!

---

### Post by Dr Small on 2007-10-15
It probably uses telnet, so you could try telneting to it, by doing the same thing, but drop off the "\\"

Dr Small

---

### Post by ariodante on 2007-10-15
The machine refuses telnet and SSH connections.  Friends can connect from their Windows machines using the instructions given.  I just wonder what the Ubuntu/Linux equivalents are.

---

### Post by russell.h on 2007-10-15
Its a samba share. I forget how to set that up though. Probably install samba packages, then tell nautilus to "connect to server" or something along those lines.

---

### Post by Keith_Burton on 2007-10-15
I believe the equivalent would be:
smb://babs.its.yale.edu/msdn-iso
Try typing that into Nautilus (or Konqueror, if you're using Kubuntu).

---

