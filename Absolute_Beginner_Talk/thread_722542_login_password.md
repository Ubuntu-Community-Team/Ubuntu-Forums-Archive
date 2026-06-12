---
title: "login password"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by tadcan on 2008-03-12
I installed 7.10. However I cant login. In the page which asked for a name and password, I gave that. The next page asked for my name and login name. When I typed that some black dots appeared the password field. So I presumed it was the previous one I entered. 

At the login page I've entered my name, my login name, but the password is refused. 

I am dual booting with Xp and I have space on the hard drive. What is the best way to retry an install.

---

### Post by mikeyphi on 2008-03-12
> **tadcan said:**
> I installed 7.10. However I cant login. In the page which asked for a name and password, I gave that. The next page asked for my name and login name. When I typed that some black dots appeared the password field. So I presumed it was the previous one I entered. 

At the login page I've entered my name, my login name, but the password is refused. 

I am dual booting with Xp and I have space on the hard drive. What is the best way to retry an install.

If you want to reinstall, use the LiveCD and take the Manual option at the partition section. Choose the old Ubuntu partition, delete it, then set it as the new partition. Leave the Swap partition as is.

---

### Post by bodhi.zazen on 2008-03-12
first make sure it is not something simple like having caps lock on.

If that fails you can easily reset your password without having to re-install.

Boot to recovery mode

At the command line type:```
passwd <user>
```

where <user> is your log in name.

Reboot.

---

### Post by tadcan on 2008-03-12
I checked id CAPS was on, but no. But I did press shift to caps the letters. 

Should I have set a different password in the second page under my user name?

---

### Post by bodhi.zazen on 2008-03-12
Hard to say what happened. Usually you type in your user name and password (X2 for the password) and that is it ...

---

### Post by tadcan on 2008-03-12
Just so I understand the first page requiring a password is the root access. The second is your user name login password?

---

### Post by bodhi.zazen on 2008-03-12
No, Ubuntu uses sudo and the root account is locked. I do not know why you had two screens like that perhaps you entered two different passwords (and repeated a step)?

We could look at /home to see your user names and /etc/passwd to look at your system...

---

### Post by tadcan on 2008-03-13
I think I know what I did. At the migrate user and settings I thought I was setting up my account.

I went into recovery mode as you instructed and reset the password. Still didn't let me log in. So I did a fresh install and I can log in now.

Next get my wireless to work. Then find out if Grub can be changed to read  my usb keyboard.

---

### Post by sir4taye on 2008-03-14
was it a laptop? I've seen some that power on with the num locks on where the numpad is within the alphabet and can confuse. Did that make sense?

---

### Post by tadcan on 2008-03-14
yes that makes sense, but i dont have a laptop.

---

