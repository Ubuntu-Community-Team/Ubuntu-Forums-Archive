---
title: "[SOLVED] running script as root during boot"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by banda on 2008-01-28
to make my webcam work with skype, everytime i boot i have to run the following commands in the terminal



> sudo rmmod ov51x-jpeg

sudo modprobe ov51x-jpeg forceblock=1



after this the webcam works till i restart the system.

to fix this i am looking for a way to run theese two commands automatically as root when i login.

any fix??

---

### Post by emarkd on 2008-01-28
Read this:

```
man update-rc.d
```

---

### Post by banda on 2008-01-28
the file is way beyond my level of understanding of ubuntu...(i am trying to make sense of it though)
a little more explanation please?

---

### Post by emarkd on 2008-01-28
1.  Write the commands you need into a script:
```
#!/bin/sh
whatever...
whatever...

```

2.  Save it in /etc/init.d.  You'll have to use sudo for this

3.  Make the file executable

```
sudo chmod +x yourscriptfile
```

4.  Add it to the runlevels

```
sudo update-rc.d yourscriptfile defaults
```

I think that'll work...

---

### Post by Dr Small on 2008-01-28
Or you can add your commands to /etc/rc.local

---

### Post by banda on 2008-01-28
@emarked
i get an error in the last step

> rahul@box:~$ sudo cp '/home/rahul/skype_mod' '/etc/init.d' 
[sudo] password for rahul:
rahul@box:~$ sudo chmod +x '/etc/init.d/skype_mod' 
rahul@box:~$ sudo update-rc.d '/etc/init.d/skype_mod'  defaults
update-rc.d: /etc/init.d//etc/init.d/skype_mod: file does not exist

EDIT-
@drSmall

thanks for the tip.. it worked:))

---

### Post by emarkd on 2008-01-28
The path to the script is understood to be /etc/ init.d.  Try it without specifying the path.

---

### Post by banda on 2008-01-28
@emarked
thankyou

now i know 2 ways to do this.:)

---

### Post by emarkd on 2008-01-28
You're welcome.  I learned a new one myself :)

---

