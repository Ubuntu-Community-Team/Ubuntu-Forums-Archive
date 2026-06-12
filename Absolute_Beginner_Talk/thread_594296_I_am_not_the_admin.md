---
title: "I am not the admin?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by em11488 on 2007-10-27
I just installed ubuntu 7.10, I am new to linux all together and I dont know what I am doing. I want to learn how to use it, but for some reason my school wont allow me to get on the internet bc virus protection and stuff. It tells me to dl this file called CSA.sh . then it says set it to read, write and execute through properties. its not giving me the option. im assuming because i am not admin. wtf. so how am i supposed to fix this and run this program. keep in mind i know nothing. i might as well have a linux IQ of 20

---

### Post by taurus on 2007-10-27
Where did you save that file?  Assuming you've saved it to ~/Desktop, open a terminal and do

Applications -> Accessories -> Terminal
```
cd ~/Desktop  <-- Change to directory where you've saved it.
chmod 755 CSA.sh <-- Change permissions so you can execute it.
./CSA.sh <-- Run the darn thing from a terminal.
```

---

### Post by em11488 on 2007-10-27
it says permission denied.

---

### Post by taurus on 2007-10-27
What are the outputs of these commands from a terminal then?

```
cd ~/Desktop  <--  There shouldn't be an output for this command.
ls -la
file CSA.sh
```

---

### Post by Het Irv on 2007-10-27
If the file is on the desktop right click it and check its permmissions.  Make sure that it is set to run as Executable.  If that doesn't work try running the last command on Taurus's first post with "sudo" and then a space in front of it.

---

### Post by em11488 on 2007-10-27
there isnt, it says operation not permiited when i type csa.sh
and permission denied when i do ./csa.sh

---

### Post by PilotJLR on 2007-10-27
Try:
```

cd ~/Desktop
chmod 755 CSA.sh
./CSA.sh

```

I think the chown in a previous post was a typo (we've all done it!).
These commands are assuming the filename is CSA.sh   
Linux is CASE sensitive, so case does matter!

---

