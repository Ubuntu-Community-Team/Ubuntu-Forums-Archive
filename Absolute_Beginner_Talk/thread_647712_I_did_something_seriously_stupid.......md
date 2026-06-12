---
title: "I did something seriously stupid......"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by thedonutman on 2007-12-22
...I unstalled Xubuntu, planning on setting up a little home file and torrenting box.

Before I even got a chance to do anything, I er....forgot my username......and password.

I think I remember my password, but I don't remember what username I set. Whats the default username for the Xubuntu installation? 


I can't be bothered to reinstall the OS again, is there a quick way to find out what username I set?


(I'm a newbie to Linux, but I'm pretty competent with computers in general, so I should understand *some* technical stuff :))

---

### Post by wormser on 2007-12-22
There is no default user name.  You can boot into recovery mode.  Then navigate to the home directory to see what the user name is.

```
cd /home
```

```
ls
```

You should now be able to see the user name.  Now you need to change the password.

```
passwd username
```

Reboot and log in.

---

### Post by lgambett on 2007-12-22
this is quite easy to solve... when the boot loader shows you have to select the recovery mode. Using this mode you will start in command mode without the need of a password.
The command cat /etc/passwd will show you the users list of you PC (but not the passwords...) In this mode you can also give the command adduser to add a new user (use man adduser for the full syntax of the command). BTW no default user name is created during X/K/Ubuntu installation.

---

### Post by Ex-windows on 2007-12-22
> **lgambett said:**
> this is quite easy to solve... when the boot loader shows you have to select the recovery mode. Using this mode you will start in command mode without the need of a password.
The command cat /etc/passwd will show you the users list of you PC (but not the passwords...) In this mode you can also give the command adduser to add a new user (use man adduser for the full syntax of the command). BTW no default user name is created during X/K/Ubuntu installation.

So goes this mean anyone can get into my comp doing this command? 
And if yes How would one prevent that??

---

### Post by jken146 on 2007-12-22
Yes, it does -- in recovery mode you are root.  To prevent this, the easiest way is to set a password for GRUB, so that only the default option loads unless the correct password is put in.

---

### Post by adam.tropics on 2007-12-22
If they had physical access to it yes. You could edit your /boot/grub/menu.lst to take away the recovery mode boot option, but I wouldn't really think it a great idea on a home system, or necessary. At the end of the day you can take away this boot option, but with physical access to the machine, all anyone needs is a live cd to get your 'stuff' anyway!

edit:lol, forgot about grub password!!

---

### Post by Zenthes on 2007-12-22
> **Ex-windows said:**
> So goes this mean anyone can get into my comp doing this command? 
And if yes How would one prevent that??

They have to physical access but yes, quick power cycle and they can be at recovery mode in less than 40 seconds.

---

### Post by kellemes on 2007-12-22
> **Ex-windows said:**
> So goes this mean anyone can get into my comp doing this command? 
And if yes How would one prevent that??

- Set a root password
- Set a BIOS-password.
- Set a Grub-password.
- Encrypting your disks.

etc.. Lots of options..

Just remember that someone having physical access doesn't need a password to attack your system.

---

### Post by Ex-windows on 2007-12-22
Thank you for letting me kow that. I
guess I should do that and put back the bios password as well.
How does one install a grub password safely (lol) I say that cuz My grub lateley has been a real pain.
Thanks. 
OOOps didnt see all those reply come in lol

---

### Post by Zenthes on 2007-12-22
Thing about that is if they have physical access, its a matter of time.  You can reset bios, there goes that password.  Grub password can be bypassed with a Grub boot disk, and i don't know what to do about root password :-p 

Like i was saying its only going to slow them down.

---

### Post by bufsabre666 on 2007-12-22
wow thats totally stupid how could you do that

just kidding man, same thing happend to me on my first instal back in the 6.06.1 daysl, but back then i didnt know about these forums, this would of been helpful to me, but i just did a reinstall...

 call me lazy

---

### Post by Ex-windows on 2007-12-22
> **Zenthes said:**
> Thing about that is if they have physical access, its a matter of time.  You can reset bios, there goes that password.  Grub password can be bypassed with a Grub boot disk, and i don't know what to do about root password :-p 

Like i was saying its only going to slow them down.

WOW, SO I guess that leaves the "Encryption" Idea. I saw that mentioned b4. 
But how does one do that? 
Can I use the encryption tool that is available through Add/Remove> ANd the next Q would be is that a good one???
 Thanks again

---

