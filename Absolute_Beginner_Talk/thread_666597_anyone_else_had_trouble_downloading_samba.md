---
title: "anyone else had trouble downloading samba?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by bradmayne on 2008-01-13
hey i tried downloading samba after it broke on me.  everything was fine until yesterday at noon. so to try and fix samba,  I downloaded from synaptic. After I downloaded i went to configure samba by: sudo gedit /etc/samba/smb.conf  the template was almost blank! Could someone tell me what dependencies I need?  Also, the first time i set up samba i went to system, administration, then shared folder.  After i did that I was prompted to download the programs to set up the sharing. Is there a way i could just get the OS to prompt me to download again? I don't understand why samba broke on me.  Every posting i have seen on samba doesn't mention anyone having trouble downloading and they make little mention of trouble setting up samba.  Is there anyone out there that can give me a hand w/ this?  At this point I was thinking of buying support from cannonical as there is no one i know that can help me with linux cuz none of my friends or family use it.  Or alternatively, if someone out there can help me fix samba and get it working again I would gladly send you a money order or something to that effect.  This is the only problem I have had with ubuntu but it's driving up the wall.  So, if you can help let me know either here or by private message.

---

### Post by dstew on 2008-01-13
> hey i tried downloading samba after it broke on me.I do not understand what happened. How did samba break? I guess you might have had a mis-configuration. Then you reinstalled the package smbclient, correct? I believe it you do that, the original smb.conf file is retained. I think you need to reconfigure, not re-install.

EDIT: [Here ]("http://ubuntuforums.org/showthread.php?t=202605")is an Ubuntu forum page on configuring Samba. It has a good sample smb.conf that can serve as a starting point.
More: [https://help.ubuntu.com/7.10/server/C/configuring-samba.html](https://help.ubuntu.com/7.10/server/C/configuring-samba.html)
Yet more: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by bradmayne on 2008-01-13
samba won't allow me to connect to the windows pc. i tried following that guide last nite. it doesn't help.  and i don't believe that it was retained because the template was messed up that i downloaded.

---

### Post by bradmayne on 2008-01-13
hey i got the samba template downloaded okay.  now, i set it up and when i click on the windows neighborhood icon nothing happens. i click the icon and it says selected. but thats it! any ideas anyone? and like i said before im willing to make it worth your while as im sure this would be cheaper than getting support from cannonical

---

### Post by dstew on 2008-01-13
Have you set up sharing on the Windows computer?

---

### Post by bradmayne on 2008-01-13
yes like i said before, everything was fine until the yesterday.. i have a feeling that nautilus  is broken or maybe a permission problem.  Now not to sound rude but i keep getting questions that are answered in my original post! please i'm not retarded (at least not today) konquerer works smb4k works. by works i mean that i can view files from the windows machine. i just can't do it in nautilus. now can anyone help me?

---

