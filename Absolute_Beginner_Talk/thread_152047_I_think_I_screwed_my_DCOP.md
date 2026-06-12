---
title: "I think I screwed my DCOP"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by Princey on 2006-03-29
Here's my dilemna, hope someone can help me out. I recently (yesterday) upgraded (got a bigger one) my hard drive. This time around, I split it into 3 partions: /swap /(root) and /home. I had backed up my home directory unto my USB Thumb Drive and after installing a freesh breezy installation, I ran apt-get update and updated my system, even kde up to 3.52. Everything went smoothly, so I shut down then booted into failsafe mode and copied back the contents of my home directory I had on the usb drive unto the home partition and rebooted. After logging in, I get this error message:

> There was an error setting up inter-process communications for KDE. The message returned was:
Could not read network connections list
/home/princey/.DCOP Server_MCES_0

Please check that the "dcopserver" program is running

What should I do, delete the said file or is there a command that I should type to reconfigure DCOP?

---

### Post by firehead on 2006-03-29
hmm not sure wether this is of any help, but did you check the file-permission on the file named? 
maybe the dcop-server just hasn't got the right to acces this file (i had similar problems because of thi reaseon, i had to 'sudo cp' my files between backup disk and actual disk and thus changing file permissions...)
if this ain't the reason why it doesn't work, i can't help you either...sorry ;-)

good luck

---

### Post by Princey on 2006-03-29
[QUOTE=firehead]hmm not sure wether this is of any help, but did you check the file-permission on the file named? 
maybe the dcop-server just hasn't got the right to acces this file (i had similar problems because of thi reaseon, i had to 'sudo cp' my files between backup disk and actual disk and thus changing file permissions...)
if this ain't the reason why it doesn't work, i can't help you either...sorry ;-)

good luck[/QUOTE]

Thanks for the info, I'll give it a try. I can't get the KDE GUI up so I'll try failsafe mode and the terminal to see what I can get.

---

### Post by Princey on 2006-03-29
I booted using the live cd but noticed that no file or folder was listed DCOP. I see MCOP as being listed. I've been fighting with no luck to get the usb drive mounted using the live CD to copy the folder. Grateful for any assistance. I'm locked out of my desktop.

------------------------
Update
------------------------
I've tried using the command > sudo apt-get install --reinstall kde and still have problems logging in. I do have the .DCOP file it talks about on my back up, however that back up is on my thumb drive and I can't figure out how to mount it using failsafe mode so I could copy the file. Is there any other way that it can be done?

---

### Post by Princey on 2006-03-29
Well, I didn't actually solve my problem even after 6 gruesome of searching on the net and trying different stuff. I had to reformat. Just wondering, is there any particular directories that one should back up?

---

### Post by knubbe on 2006-03-31
[QUOTE=Princey]Here's my dilemna, hope someone can help me out. I recently (yesterday) upgraded (got a bigger one) my hard drive. This time around, I split it into 3 partions: /swap /(root) and /home. I had backed up my home directory unto my USB Thumb Drive and after installing a freesh breezy installation, I ran apt-get update and updated my system, even kde up to 3.52. Everything went smoothly, so I shut down then booted into failsafe mode and copied back the contents of my home directory I had on the usb drive unto the home partition and rebooted. After logging in, I get this error message:



What should I do, delete the said file or is there a command that I should type to reconfigure DCOP?[/QUOTE]



OK. My system has worked fine for months, but now i upgraded to KDE 3.5.2 (from 3.5.1) and now i get the same error. 

I moved my /home/knubbe/.kde to /home/knubbe/.kdebackup and now i can login into KDE again - but it's the default settings, like if i havent done any modifications to KDE's settings (fonts, colors etc).

Is it possible to downgrade KDE again? Or is there an easy solution for this?

---

### Post by knubbe on 2006-03-31
ok. solution: make sure your ~/.kde is owned by you (recursively).
 
"sudo chown -R knubbe:knubbe /home/knubbe/.kde"

....assuming my name is user name is "knubbe".

---

