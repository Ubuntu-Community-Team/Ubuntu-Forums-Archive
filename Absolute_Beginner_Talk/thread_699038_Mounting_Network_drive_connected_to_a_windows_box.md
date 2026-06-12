---
title: "Mounting Network drive connected to a windows box"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Chimera76 on 2008-02-17
I have a PC which I have a WD external drive connected to and mapped as a network drive in windows...

My laptop with Ubuntu on it cannot see or access this drive....i've tried numerous articles i've found on the web...and had mixed results...this is what i've tried:

editing fstab to include the device
Connecting to Server from Places Menu
mounting the device as a cifs and smbfs from the terminal

both of the mount from terminal commands have yielded timeout errors (I have opened the ports on my firewall on my windows box)

basically...i'm stumped...anyone have a quick awnser? :)

---

### Post by MasterJS on 2008-02-17
Right click the drive and click properties. Go to the share tab and set it to share. Then go to Places > Network in Ubuntu and click Windows Network. Find whether your server is MSHOME or Workgroup and go into which ever one it is. Then you should a folder with the username of your Windows PC. Click there and your folder should be there

---

### Post by Chimera76 on 2008-02-17
When I go into the Windows Network it is empty. I already changed my Workgroup in the Samba config file to what my workgroup is called too.

---

### Post by MasterJS on 2008-02-17
Have you set Windows to share that drive?

---

### Post by Chimera76 on 2008-02-17
Yes I have, the drive is accessable via another laptop running XP....so I know the share works :)

(thanks for your help so far btw...i'm tottally at a loss for whats up with this...)

---

### Post by MasterJS on 2008-02-17
Can Windows see a folder from your Ubuntu?

---

### Post by Chimera76 on 2008-02-17
How do you mean? I'm not trying to share from my laptop to my desktop....I am strictly trying to setup access to my external hard drive so I can stream my music etc... from it :)

---

### Post by MasterJS on 2008-02-17
I know what you mean, but it'd just like to know if it was something with the network or your samba configuration. It would help to know if Windows could see Ubuntu.

---

### Post by Chimera76 on 2008-02-17
Actually...no it can't....

---

### Post by MasterJS on 2008-02-17
Can you ping between the two computers? you know typing in the terminal or command box ```
ping ***.***.***.***
``` The ip address of the OTHER computer where the asterisks are

---

### Post by Chimera76 on 2008-02-17
both ping each other with no lost packets

---

### Post by Chimera76 on 2008-02-17
Okay! Worked on this through the night....now i'm at a point where I can see my drive in Places>Network

but I still can't mount the device via my fstab file....I get a mount error 6, which tells me that i'm not using the right share name....but I used the one right off of the Network window and still no luck...what am I doing wrong?

---

### Post by Efros on 2008-02-17
I always use the IP number in fstab

---

### Post by Chimera76 on 2008-02-17
That doesn't work either...same error.

---

### Post by Efros on 2008-02-18
These may be of some help

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=463367](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=463367)

[http://www.thatsquality.com/ubuntu/mounting-windows-smb-file-shares-using-cifs](http://www.thatsquality.com/ubuntu/mounting-windows-smb-file-shares-using-cifs)

Good luck

---

