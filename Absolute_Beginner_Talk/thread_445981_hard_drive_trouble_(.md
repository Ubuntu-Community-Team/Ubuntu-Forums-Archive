---
title: "hard drive trouble :("
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by jimbam on 2007-05-16
hi im a total newb at this linux stuff. i only got it yesterday and it was all pretty easy for me, but today when i went on my computer and tried to listen to music i got an error message. heres a screenshot of it [ATTACH]32751[/ATTACH] anyone know how to get past this? please help if so

---

### Post by laidback on 2007-05-16
Welcome jimbam,
Now I'm no expert but it looks to me as though this is a disc drive/partition issue. From what I can see on your screen shot you appear to have 1 hdd of approx 75Gb, if this is true than I suspect that it is already mounted and that you have attempted to mount it again..this will cause an error. I wouldn't expect to have to mount your hdd again, since Ubunt is running it is already available. Click on Home of File System to navigate through your hdd. Where is your music?

---

### Post by netwerx on 2007-05-16
Hi there. 

First, lets try this.

first, goto terminal (Applications > Accessories > Terminal)
then type in "sudo fdisk -l" (lowercase L)

Please post what is displayed to you, here.

And we will take it from there.

---

### Post by jimbam on 2007-05-16
[ATTACH]32757[/ATTACH] this is what comes up... nothing lol am i doing something wrong? and also i have 2 hard drives one wich is only 9GB, wich has ubuntu installed on it, and the other wich is 74.50GB, that has my music on it. i dont mind if i lose all my music cos i will just put it back on with time its just really annoying me that i havent got a clue what to do.

---

### Post by netwerx on 2007-05-16
you need to type in a password.  this is the password used to logon.
did you type in your password, after you typed in the "sudo fdisk -l"?
you got a password prompt, but i can't tell if you typed it in or not.

---

### Post by jimbam on 2007-05-16
yeah i typed it in but thats all it did. when i typed it in tho nothing came up no asterix or anything

---

### Post by netwerx on 2007-05-16
astericks won't come up, that is normal.
please do it again, and when prompted, please type in your root password.  (usually the password used to login.

---

### Post by jimbam on 2007-05-16
i did it nd this is what came up "jimbam is not in the sudoers file.  This incident will be reported." [ATTACH]32760[/ATTACH]

---

### Post by tommcd on 2007-05-16
Are you able to use sudo for other things? Like "sudo apt-get update"? If not, then see this:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)
See if your username is listed at the admin:x:106: line.
You may need to chown the 74GB drive to get permission to use it.

---

### Post by netwerx on 2007-05-16
> **tommcd said:**
> Are you able to use sudo for other things? Like "sudo apt-get update"? If not, then see this:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)
See if your username is listed at the admin:x:106: line.
You may need to chown the 74GB drive to get permission to use it.

good point.  thanks tommcd.

---

### Post by jimbam on 2007-05-16
wow u 2 thanks so much for your help. that worked perfectly nd now i can listen to music!!!

---

