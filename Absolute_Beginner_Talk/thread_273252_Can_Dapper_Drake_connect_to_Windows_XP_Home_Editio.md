---
title: "Can Dapper Drake connect to Windows XP Home Edition shares?"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by pisapiag on 2006-10-07
Can Dapper Drake connect to Windows XP Home Edition shares? If the answer is simply no, please tell me so and I'll stop losing my time over this issue. If someone has actually succeeded in doing so, please post a detailed procedure, as I'm totally dumbfounded. ](*,) 
I can see the shares but when I try to authenticate as an XP admin on the XP box, Dapper refuses to reckon.
Thanks for your patience.

---

### Post by jordanmthomas on 2006-10-07
The answer is yes, so you have to keep banging your head.  :D

Are you concerned with security?  It sounds like you have set up filesharing incorrectly (or with authentification) in Windows itself.  Can Windows machines access it?  

Try turning off any sort of passwords and see if you can get it to work.

---

### Post by pisapiag on 2006-10-08
Concerned with security? I'm primarily a Windows user so you know I have to be. Actually, the box I'm using Ubuntu on right now used to be a XP box whose owner was the least bit concerned about security. It was rendered unusable so I proceeded to try Linux. I'm a Windows expert but a total newbie with Linux distros. I'm not about to compromise security on my XP box just to get Ubuntu  access to shared drives. My Windows box is three years ols and has been serving me flawlessly since the beginning. 
From what I can see from these forums is that a previous version of Ubuntu was much more efficient in connecting to Windows shares. It seems I'm not the only one having this unresolved problem. And this is not the first one. I've been struggling for the last two weeks getting my soundcard to work, then my wireless NIC, and now this share problem. A friend of mine using Fedora didn't have any problem with his box. I got all the Fedora CDs ready to replace Ubuntu if I can't find a solution. But I'm not one to give up easily so.. here I am, asking for your help. 
I still want to give Ubuntu a chance but patience has its limits. Thanks for yours.

---

### Post by pisapiag on 2006-10-08
Well, I may have found the solution. It appears that the only share that Windows XP Home Edition will allow a Ubuntu box to connect to without any fuss is the SharedDocs one or any other share created under. As far as I'm concerned, any other won't work. I don't know the situation with XP Pro as I don't have such a box at home and I can't experiment that at work. I don't know if the fault is Windows' or Ubuntu's nor do I really care. I hope this post will help some of you.
Take care.

---

### Post by Kulgan on 2006-10-08
all I did was enable filesharing on the Windows box, share a folder, then on Ubuntu go "Places -> Network Servers -> wait -> Windows Network -> wait -> wait  then I got all the shared folders. I had to lower the firewall settings on the Windows box, though (Zonealarm).

---

### Post by andb on 2006-10-08
Absolutely can. If you arent afraid of the command line, its really easy. 
sudo mount -t smb //IP.ADD.RESS.HERE/SHARENAME /MOUNTPATH 

Try doing info on mount and smbmount and you'll find the command line can even enter the windows password and userr name for you. And if you want it all done automatically at boot, you can add a line to /etc/fstab (which controlls all mounted volumes) to do it for you. Youll find other posts about that for sure here!

---

### Post by jordanmthomas on 2006-10-08
nevermind. sorry.

---

