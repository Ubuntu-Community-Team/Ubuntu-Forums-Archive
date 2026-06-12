---
title: "can not add samba users"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by kgeil on 2006-09-07
Hi, I know this one has entered the forums before, but I've spent my entire evening trying every fix I could on the web, to no avail.  I'm running Ubuntu 6.0.6, and am trying to get file sharing set up with a windows box.  I have added users to the ubuntu system, (system administration/users and groups,but when I try to add users to samba, I just get the following error message:

Failed to initialise SAM_ACCOUNT for user [sarah]. Does this user exist in the UNIX password database ?
Failed to modify password entry for user [sarah]

following is the entire text from my konsole:



kevin@kevin-desktop:~$ sudo smbpasswd -a [sarah]
Password:
New SMB password:
Retype new SMB password:
Failed to initialise SAM_ACCOUNT for user [sarah]. Does this user exist in the UNIX password database ?
Failed to modify password entry for user [sarah]
kevin@kevin-desktop:~$


I have tried this several times, reinstalled samba, restarted the machine, tried (and failed) to run SWAT, and have had no luck so far.

Any help will be greatly appreciated.

Thanks,

Kevin

---

### Post by djsroknrol on 2006-09-07
If you did the users and groups first, I'd pay another visit there first to see what's wrong there...I'll bet you'll find it in there. I had a similar experience with groups and permissions getting in the way of my shares.

---

### Post by kgeil on 2006-09-07
Do I need to set up a particular group for samba users?  Adding users seems straightforward, but when I hit the groups tab, I get a bit lost...

Thanks,
Kevin

---

### Post by djsroknrol on 2006-09-08
I set up a group that mirrored my intranet inside the house with open permissions for all as I want access at every box. 

Name your group and then add users as needed.

---

### Post by anaconda on 2006-09-08
> **kgeil said:**
> 
kevin@kevin-desktop:~$ sudo smbpasswd -a [sarah]

I know almost nothing of samba, but the above line looks STRANGE!!
you didn't actually write [sarah] ??

I thik this would be more like it:
sudo smbpasswd -a sarah

in manpages there often are those extra []-marks, but they just mean that insert the text here, and not to include those []..

hope this helps..

---

### Post by kgeil on 2006-09-08
Hi, I followed the advice of botha DJ and Anaconda, and it went smoothly.  Anaconda, I picked up those brakets around [sarah] when I was hunting for anything to make this work.  

Thanks again,

Kevin

---

