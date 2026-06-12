---
title: "ubuntu connet to windows server 2003"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by wakatobi on 2005-12-01
How can I connet ubuntu 5.10 to my office server using windows server 2003

help...............:confused:

---

### Post by Koybe on 2005-12-01
What do you mean? Connecting to a share, connecting through VPN... ?

---

### Post by Abhi Kalyan on 2006-10-20
Am having this serious Problem too.
Have a windows 2003 server running a doamin and i dont know how to connect my uduntu system to this so as to enagble file sharing, Print sharing.
Internet sharing is happening, thats how am in thi fforum.
So some body HELP PLEASE

---

### Post by Abhi Kalyan on 2006-10-20
> **wakatobi said:**
> How can I connet ubuntu 5.10 to my office server using windows server 2003

help...............:confused:

just type 
sudo gedit /etc/samba/smb.conf
and change 
Code: security = user
Code: security = share
I hope it'll help, I'm not sure about my memories 
don't foget to restart samba: sudo /etc/init.d/smbd restart – restarting did not work for me! others did
thread : Windows computer connecting to me
helped by: sYs^
After this i had gone and installed some extra files relating to samba from Synaptic package manager. but did install smb2www.

---

### Post by Abhi Kalyan on 2006-10-21
Credits to Mr. Grey : he had given me this solution from the thread"Corporate shifting to ubuntu..."- Till now all his suggestions have worked perfectly, so am sure this will work- Please post the outcome-
"
This is a little more complicated to explain... and there are many ways of doing it. First thing you are going to want to do...

Code:sudo apt-get install samba smbfs

SMB is the protocol that Windows PCs use for filesharing. Samba is a reverse-engineered application for Linux that supports it.

After you've installed Samba, for a nice graphical way of connecting, open up Nautilus, and try to connect to smb://x. Alternatively, you can try Places->Network, and try to connect to a Windows network.

If you would like to have the share mounted in your filesystem, that's a little trickier, but can still be done quite easily. (It's a little faster and more reliable than using Nautilus anyway). A good guide for how to do this is this one.
[http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/](http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/)
"

---

### Post by Abhi Kalyan on 2006-10-25
Dear wakatobi,
Did the solution work?
It has worked for me.
It would be great if you confirm.
if it did not, we should be able to get help. Thank you once again

---

