---
title: "Can't access hard drive."
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by -Race- on 2006-09-04
Hello. I have finished installing Ubuntu and started to grasp a basic understanding of it. However I have a probelm that has probably been stated before. I am trying to install World of Warcraft using wine. I have the game installed on Windows but I would like to trasnfer the folder and all to be usable by Ubuntu. I try to access my harddrive under Computer-File Browser but it gives me unable to mount selected volume. I click Details and I get 
error: device /dev/sda2 is not removable

error: could not execute pmount

How can I get around this to be able to transfer World of Warcraft, and other things i,e music to Ubuntu?

---

### Post by taurus on 2006-09-04
You need to mount it by hand first before you can access it...  Open a terminal, Applications -> Accessories -> Terminal, and type

```

sudo mkdir /media/windows
sudo mount -t ntfs /dev/sda2 /media/windows
sudo cd /media/windows
sudo ls -la

```

---

### Post by -Race- on 2006-09-04
I did that command and I can access it but it displays that it has no date (0 Bytes) Is that a problem or is there extra that needs to be done?

---

### Post by taurus on 2006-09-04
Yes, run each command with a return key and tell me which command gives you the error message and what is the error message!  Otherwise, I can't really help you since I don't know which command is the problem and what exactly the problem is!!!

---

### Post by -Race- on 2006-09-04
Sorry, changed my edit however I did follow this guide.
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
Did it all however when I open the HD it says it cannot view the contents of "windows"

---

### Post by taurus on 2006-09-04
So, does you have something like this in your /etc/fstab?

```

/dev/sda2   /media/windows   ntfs   defaults,umask=0222   0   0

```
Then, you still need to mount it with

```

sudo mkdir /media/windows
sudo mount -a

```

---

### Post by -Race- on 2006-09-04
I realized that I dont know where my partition is mounted. Before redoing all these steps how can I find out where it is mounted.For example
/media/hda1

---

### Post by taurus on 2006-09-04
"df -d" will show you all the partitions are currently mounted on your machine...  Again, even after you edit /etc/fstab, you still have to mount it with the "sudo mount -a" command!!!

---

### Post by -Race- on 2006-09-04
Hmm alright thank you very much. I"ll redo this all the right way. Will update with results.

---

