---
title: "Permissions won't allow me to open terminal"
date: 2005-12-27
forum: Absolute Beginner Talk
---

### Post by Nameless on 2005-12-27
I changed my permissions on what I think was my user directory and now I'm not able to launch anything from my user. I can't even launch terminal to change my permissions.  

What can I do to correct this?

---

### Post by Nameless on 2005-12-27
Let me add a little bit to this:  I am at full screen terminal screen and I'm prompted to login into my computer.  It reads:  [comp name] login: 

I enter my user ID and password and I'm told: Unable to cd to "/home/[user]"

That's where I'm stuck.  I'm thinking this is not an easy problem to fix, but hopefully I'm wrong. 

Thanks

---

### Post by steve.horsley on 2005-12-27
[QUOTE=Nameless]Let me add a little bit to this:  I am at full screen terminal screen and I'm prompted to login into my computer.  It reads:  [comp name] login: 

I enter my user ID and password and I'm told: Unable to cd to "/home/[user]"

That's where I'm stuck.  I'm thinking this is not an easy problem to fix, but hopefully I'm wrong. 

Thanks[/QUOTE]

That sounds as though you actually managed to log in OK. Have a look and see what your home directory permissions look like with this command:```
ls -l /home
``` You could even try and fix it with these commands (replace 'user' with your username):```

sudo chown user:user /home/user
sudo chmod 750 /home/user
```

---

### Post by audax321 on 2005-12-27
If all else fails, try to get a hold of a LiveCD and then mount the partition and change the permissions that way.

---

### Post by Nameless on 2005-12-27
[QUOTE=steve.horsley]That sounds as though you actually managed to log in OK. Have a look and see what your home directory permissions look like with this command:```
ls -l /home
```[/quote]

I tried "ls -l /home" at "root@[computer]:~# prompt and this is what it said: 

total 4
drwxr-x--- 29 nate nate 4096 dec 27 11:49

> You could even try and fix it with these commands (replace 'user' with your username):```
sudo chown user:user /home/user
```

How do I know what my user is?  Will it just be my sign on for the compuer? 

```
sudo chmod 750 /home/user
```

I tried this and I got this response:

"Sudo: can't open /etc/sudoers : Permission denied"  Shoul I not use "sudo" at the beginning of that commnand?

---

### Post by alinuxfan on 2005-12-27
it looks that your username is nate so where the other people have put "user" put "nate"
I am new too, but that seems to be your user name

 You could even try and fix it with these commands (replace 'user' with your username):
Code:

sudo chown user:user /home/user 
sudo chmod 750 /home/user

---

### Post by Nameless on 2005-12-27
I tried the above, but I don't seem to be having any luck.  Does this show that I have the right permissions? 

Prompt: root@jnddesktop:/home/nate# I entered
```
 ls -l
``` 

and I received the following: 

```

total 56
drwxr-xr-x 2 nate nate  4096  dec 21 20:39 Desktop ("Desktop" is in blue)
drwxr-xr-x 2 nate nate  4096  dec 26 22:39 Temp ("Temp" is in blue)
-rw-r--r-- 1 nate nate 33180  dec 20 09:35 automatix-ubuntu_4.0-1_i386.deb (in red)
-rwxr--r-- 1 nate nate    326  dec 21 21:24 automatix.log (in green)
```

I still get the message "Unable to cd to /home/nate" when I try to login.  

Would the above mean that the root is not able to cd?

---

