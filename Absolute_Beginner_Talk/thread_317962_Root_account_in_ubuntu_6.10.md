---
title: "Root account in ubuntu 6.10"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by lance_klusener on 2006-12-13
Hello people , 
              I wanted to know how does one go about to create a root account in ubuntu 6.10 .

---

### Post by peterj on 2006-12-13
The root acount is already there however it's stronly advisable that you don't log in as root. Instead use the 'sudo' command and key in your password on prompt. There are various security and safety reasons for this.

---

### Post by lance_klusener on 2006-12-13
But there is some scneraio that i am faced with which forces me to log in as root or create a root account if one doesnot exsist

---

### Post by dann0 on 2006-12-13
I simply type "sudo bash", and enter the password.
Then I'm root for as long as I need.

When done, just type &#8220;exit&#8221; and you are back at your normal prompt.

In most cases however, it's enough typing &#8220;sudo&#8221; before the command.
Ubuntu remembers your password for some minutes, so you don't have to enter it all the time.

---

### Post by Crooksey on 2006-12-13
```
$sudo su
```

Works fine.

---

### Post by lance_klusener on 2006-12-13
So "sudo" is the only way to get to a root account , isnt there any account which has the username as "root" which you can log into and remain as root forever in ubuntu

---

### Post by dorcssa on 2006-12-13
> **lance_klusener said:**
> So "sudo" is the only way to get to a root account , isnt there any account which has the username as "root" which you can log into and remain as root forever in ubuntu

Why do you want to remain as root "forever"?:-s

---

### Post by lance_klusener on 2006-12-13
I am installing something that requires me to remain as root for considerable amount of time , also out of curiosity is it possible to do it ?

---

### Post by Rumor on 2006-12-13
I believe it *is* possible. but if you install something as root, then your normal user might not have permission to use whatever it is you are installing since the preferences, settings, data files, etc. would be installed in /home/root/.program_name.

If you install this whatever it is using sudo, you will remain root as long as that command is running, regardless of how long it takes.

But, to set your root password: ```
sudo passwd root
``` after that, you can ```
sudo su
``` to your heart's content.

---

### Post by chettyk on 2006-12-13
> **lance_klusener said:**
> I am installing something that requires me to remain as root for considerable amount of time , also out of curiosity is it possible to do it ?

The steps you have to follow to enable the root account are:
[LIST=1]
[*]Set root password
[*]Unlock root account
[*]Enable root graphical login
[/LIST]

Set root password:
```
sudo passwd root
```

Unlock root account
```
sudo passwd -u root
```

Enable root graphical login:
**System > Administration > Login Window > Security**
Check box for **Allow local system administrator login**

But be warned: You can easily trash your system while working as root, especially if you are not used to Linux.

I suggest you disable the root account after you are through:
```
sudo passwd -l root
```

Good luck!

---

