---
title: "Sharing files between two linux machines"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by Sitting Duck on 2007-09-16
Hello,

I have two computers on which I have installed Ubuntu 7.04 (No dual-booting, I made a complete switch to linux).  One is connected by wire to my router, the other (my laptop) is connected through wireless.  I would like to be able to search for files located on my desktop computers using the laptop or to print files located on the laptop with the printer plugged to the desktop computer.

My questions then are...
Is any of that possible?
Is there a guide somewhere showing how to do it?

Thank you.

---

### Post by earobinson on 2007-09-16
if you setup ssh ```
sudo apt-get install ssh
``` you can try this [http://www.howtogeek.com/howto/ubuntu/how-to-mount-a-remote-folder-using-ssh-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/how-to-mount-a-remote-folder-using-ssh-on-ubuntu/)

---

### Post by kfrance on 2007-09-16
It is possible. I haven't set up either of these things and it may require a little work on your part.  You are wanting to set up a NFS (network file system) and a print server. This can be done using Samba. Samba has some fairly nice help files and tutorials. It does have a lot of options that make is a little difficult to sort through but given a few hours you should be able to figure it out.  Hope this puts you on the right track.

---

### Post by Kilz on 2007-09-16
You could also use [nfs auto mount.]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

---

### Post by cvaty on 2007-09-16
hey sitting duck, im attempting to do the same thing as you at the moment....
what are your thoughts about how your going to get this done?

let me know what works out for you

---

### Post by Mud.Knee.Havoc on 2007-09-17
Kilz, that's a great guide you've linked to.  I've used nfs to network my computers for a long time, but it has some great tips that I'm ashamed to admit that I didn't know until now. :D

---

