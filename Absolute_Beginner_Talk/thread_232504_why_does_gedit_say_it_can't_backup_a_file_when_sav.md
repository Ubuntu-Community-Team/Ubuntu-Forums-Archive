---
title: "why does gedit say it can't backup a file when saving?"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by JohnJSal on 2006-08-08
Every time I try to save a file with gedit, it warns me that it can't create a backup and asks if I'm sure I want to save it. First off, why can't it create a backup? Secondly, and more importantly, I already turned off the option to make backups when I save, so I don't know why it's even trying.

Is there a way to stop this so I can just press 'Save' and it's saved?

Thanks.

---

### Post by Jose Catre-Vandis on 2006-08-09
I usually get this when I open up a file across the network, so kind of understand why a backup won't be made. Is this the case with you? Also it may be you have "interesting" permissions settings that will allow you to save the file, but not to add/create/modify other files to that directory.

---

### Post by taurus on 2006-08-09
> **JohnJSal said:**
> Every time I try to save a file with gedit, it warns me that it can't create a backup and asks if I'm sure I want to save it. First off, why can't it create a backup? Secondly, and more importantly, I already turned off the option to make backups when I save, so I don't know why it's even trying.

Is there a way to stop this so I can just press 'Save' and it's saved?

Thanks.
Are you trying to save something to the system instead of in your home directory?  What file are you talking about here?

---

### Post by JohnJSal on 2006-08-09
Nothing I'm doing involves networks, so it's not that. It's just random files that I open and try to save. None of them are being saved to ~, so obviously they are going elsewhere on my system. One was saved to my shared partition but still prompted me.

I think this usually happens when I open gedit manually and edit a file. Last night I was doing

sudo gedit /etc/X11/xorg.conf

and I was able to press "Save" without any prompts.

---

### Post by Zar on 2006-08-09
I get the same message whenever I try to save on any fat32 partition.

---

### Post by MaximB on 2006-08-09
1.it could be the files you are trying to save over are "read only"
change it if you like
2.and try always editing your files with the "sudo" command.

---

### Post by JohnJSal on 2006-08-09
> **MAXDDARK said:**
> 1.it could be the files you are trying to save over are "read only"
change it if you like
2.and try always editing your files with the "sudo" command.

I use sudo when I invoke gedit from the terminal (and I don't have this problem), but how do I do this if I just want to open a file by using the regular GUI browser, or open up gedit manually from the menu?

---

### Post by Brunellus on 2006-08-09
perhaps it's related to file permissions?  fat32 doesn't support all the file permissions that linux filesystems need.

---

### Post by junglepeanut on 2006-08-09
If it does not have to do with the files being in read only for regular user i.e the /etc/X11/xorg.conf is protected you will not be able to save with out  sudo. If it is your home folder you should not need this unless the owner of the computer has put some strong restrictions. But I figure you are the owner as you can sudo.

If this is a case where everywhere you have this problem maybe you could try 

 going to your menu and you should be able to create a run icon which just runs a command from the terminal but you dont see a terminal etc. Your just make a magic button basically. Then give it the command 'sudo gedit' but this would just open the editor you would still have to then navigate to the file, plus you would need to enter your password all the time ugh. As such I hope somebody chimes in with a better fix.

---

