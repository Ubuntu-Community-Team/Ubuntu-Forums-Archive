---
title: "permission not granted"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by thelugnut on 2007-10-21
I would like to creat a folder in "opt" and place some files there.

I get the 
"You don't have permission ..." message.

What am I doing wrong, please?

---

### Post by LeeAdkins on 2007-10-21
Most system folders are owned by the root user and don't allow you to access them.
In short, you need to put "sudo" before your commands in these situations.
Adding stuff to the opt folder is fine, but be very careful using sudo just to get through the security elsewhere in the system. It is the same as if you were to go through the Windows or System folders on a windows machine playing around.

You'll use sudo all the time though, so keep it in mind.

---

### Post by Maestro23 on 2007-10-21
/opt is owned by root.  You need root permission to do anything in there.  Use** sudo** in front of your commands.

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

*Be careful when messing around in areas owned by root.

---

### Post by smacattack on 2007-10-21
you can type sudo nautilus in terminal and it will open a new file browser with full root privileges. that's what i usually do in that situation.

like the above posts have mentioned though... be careful in root.

---

### Post by corney91 on 2007-10-21
If you wanted to make the folder in nautilus, the command would be ```
sudo nautilus
```
Then you can move to the /opt folder and do whatever you want. But be CAREFUL.:)

---

### Post by steve.horsley on 2007-10-21
In general, when launching GUI apps with root privs, you should use gksudo rather than just sudo. e.g.
gksudo nautilus

Otherwise there is a risk of leaving a lock fiile that prevents launching applications later.

---

### Post by thelugnut on 2007-10-21
Most grateful to you all. 

I understand and I will use great care with "sudo".

Thanks to all

---

