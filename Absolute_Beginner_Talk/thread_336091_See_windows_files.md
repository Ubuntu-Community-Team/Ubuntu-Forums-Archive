---
title: "See windows files"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by rbhigday on 2007-01-11
Is there an easier way to see network file other than ```

i press alt+f2 and type in the IP of my windows machine, smb://192.168.0.3
```

or create an icon on desktop or in menu to bring up the network to see files on other pc's running XP?

---

### Post by gh0st on 2007-01-11
Just go to Places -> Network Servers on the main menu bar. That should let you browse your network just like Network Neighborhood does in windows.

It certainly works for me. All the SMB shares on my network just pop up in a Nautilus browser :) I think you can create shortcuts to the folders and stuff if you want as well.

---

### Post by hoges on 2007-01-11
I found that mine appeared in places under the comp's ip address.

I did it this way...

Places-->Connect to server
Select service type from drop down menu (in my case windows share)
Server (ip address)
Any additional info you want/need to add
Hit connect

There should be a menu item under places

---

### Post by rbhigday on 2007-01-12
Thanks I was foolishly looking for a menu prompt for Nautilus and doing this ](*,) because i could see it was installed but never found a menu option for it.

---

### Post by blackened on 2007-01-12
I used to use the "Connect to Server" option, but there's an alternative.  With sshfs you can mount network filesystems and include them in your local directory structure. 
Ex. All my music and videos are stored on my fileserver, but mounted in my local home directory under ./Music and ./Video. To me it's just as if they were stored on my regular workstation. 
Howto is [here]("http://www.ubuntuforums.org/showthread.php?t=103860&highlight=sshfs").

---

