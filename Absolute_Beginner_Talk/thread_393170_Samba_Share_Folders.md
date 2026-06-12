---
title: "Samba Share Folders"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by marianoi on 2007-03-25
Hello everyone,

I'd have a question...

I turned the share folder option on in both Ubuntu and Windows (Win is running as a virtual machine). I can see the PCs connected to the network but I cannot connect to them. Here is the problem:

Ubuntu trying to connect to Windows:

1) I can see the Win machine.
2) If I double click on it a window pops up saying Ubuntu could not connect to the PC (it takes like 2 min for the window to pop up)

Windows to Ubuntu:

1) I can see the Ubuntu machine.
2) When I click on the PC a Window pops up asking me for a User name and Password. If I put my Ubuntu user name and pass it says it is incorrect...so I cannot connect either.

Does anyone know what am I doing wrong? Do I have to configure something else??? 

Thanks for helping!!

Cheers

Mariano

---

### Post by tgunner on 2007-03-25
Is the Windows virtual machine running on the same PC as ubuntu?

---

### Post by lamalex on 2007-03-25
create an ubuntu user with the same username and password as your windows user. that should fix your password issue

---

### Post by marianoi on 2007-03-25
Hello,

Thanks!

Yes, the virtual machine is running in the same Ubuntu box. I enabled the Share folder option in VMware...

Do the Ubuntu and the Win user names have to be the same? If so, what password should I use? The win or the Ubuntu's one? :confused: 

Thanks gain!

Mariano

---

### Post by lamalex on 2007-03-25
ubuntu needs a user that is the same as windows, it doesn't have to be your primary user. it just needs to be a user who COULD log in, so if your windows username is fakename, and the password is fakepass, make an ubuntu user fakename with password fakepass.

---

### Post by Mellon on 2007-03-25
yep you need to setup a samba user and password 

sudo smbpasswd -a 'user'

---

