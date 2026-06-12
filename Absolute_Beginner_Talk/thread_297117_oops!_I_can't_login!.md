---
title: "oops! I can't login!?"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by mahavishnuO on 2006-11-10
So, first things I'm a newb. I am try to get away from windows. 

I installed ubuntu dapperdrake and logged in a few times on the username oem without any problems. Then, i remembered reading somewhere to run oem sudo-config-prepare to get rid of the oem account and set up a new account. So i did that, and made a new account, and entered the password and everything. BUT, now when i go to log in it says my username password combo is wrong, so i can't get in? And I can't log in on oem.

Please help me. ubuntu is sweet but now i can't log in! ](*,) 

------------
mahavishnuO

---

### Post by taurus on 2006-11-10
Are you sure the cap is not on since Linux/Unix is case sensitive!!!  Otherwise, boot your Ubuntu into recovery mode from GRUB menu and at the prompt, see what is the username in /etc/passwd...

```
cat /etc/passwd
```
It should be the last line in that file and assuming for a second it's john, then you can change the password for john with

```
passwd john
```
Reboot and see if you can log into john with the new password...

---

### Post by mahavishnuO on 2006-11-11
okay i booted ubunto from recovery mode and figured out that the username is 'nobody' which i definately did not enter after i did the oem sudo-config-prepare thing.

but now, when i log in, i get an error saying there is no root directory /, and it asks me to try a failsafe session and it still gives me the same error. so now i can log in, but i then it kicks me out back to the login screen due to the error. 

any advice O taurus?

---

### Post by warjowuch on 2006-11-11
Sounds like he is looking in the wrong place for the root dir. If this dir really was not there, he would not have started up the login screen... I don't know how to fix this, but it might be a key. But it really is a guess.

---

### Post by IanGB on 2006-11-11
Perhaps you just managed to set up a user with your sudo config and did not change root. Did you try to use the old log in detail again instead of the new changed one?

---

### Post by mahavishnuO on 2006-11-12
it just seems like when i log in, the root that is set isn't right. it gives me an error like 'no root / in HOME' or something i think. is there some code to set the root that is associated with my login name? i still get kicked back to the login screen before i even see the desktop.

---

### Post by mahavishnuO on 2006-11-13
okay here are the actual errors that i get.

On login i get this:
"Your home directory as listed as '/nonexistent' but it does not appear to exist. Do you want to log in with the / (root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session."

And then even if i use a failsafe gnome i get:
"User's $HOME./dmrc file is being ignored. This prevents the default session and language from being saved..."

and then it kicks me out after an error which has details
"could not create directory /nonexistent"


is there a simpler way to reinstall ubuntu? i have nothing valuable on it yet, i just installed like a week ago. its messed ahhhh](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by taurus on 2006-11-13
Try to boot into recovery mode again.  Now, see if there is a $HOME for your user which in this case I will assume john.  

```
ls -la /home
ls -ls /home/john/.dmrc
```

---

### Post by mahavishnuO on 2006-11-16
It seems there is no $HOME for any user. i tried the code given above for the user 'nobody' which is a user that i found with cat /etc/passwd. I never created an account 'nobody.' the account name i created was mahavishnu and it doesnt recognize it. if i run ```
ls -ls /home/sudo/.dmrc
``` or ```
ls -ls /home/root/.dmrc
``` it doesnt work either, (if its supposed to im not sure.)

If i reformat my partitions where ubuntu is installed, (linux Ext3 and Linux Swap) will my GRUB menu be messed up. If it wouldnt be, then I could just reformat the partitions and reinstall ubuntu from the cd?

---

### Post by taurus on 2006-11-16
> **mahavishnuO said:**
> It seems there is no $HOME for any user. i tried the code given above for the user 'nobody' which is a user that i found with cat /etc/passwd. I never created an account 'nobody.' the account name i created was mahavishnu and it doesnt recognize it. if i run ```
ls -ls /home/sudo/.dmrc
``` or ```
ls -ls /home/root/.dmrc
``` it doesnt work either, (if its supposed to im not sure.)

If i reformat my partitions where ubuntu is installed, (linux Ext3 and Linux Swap) will my GRUB menu be messed up. If it wouldnt be, then I could just reformat the partitions and reinstall ubuntu from the cd?
First of, there is no such thing as /home/sudo UNLESS you've created a user sudo which you are NOT supposed to!  I don't even think the system will allow you to create a user sudo.  Meanwhile, root should be in /root, not /home/root!!!  What are the output of these two commands from a terminal then?

```
ls -la /home
cat /etc/passwd
```

---

### Post by mahavishnuO on 2006-11-16
The code ```
ls -la /home
```
yields

total 8
drwxr-xr-x 2 root root 4096 Nov 9 02:26.
drwxr-xr-x 21 root root 4096 Nov 8 10:26..


The other piece of code cat /etc/passwd gives me at least 24 lines of a whole bunch of stuff. Is there something specific from it i should look for?

---

### Post by taurus on 2006-11-16
Looks like there are no directories for any user on your system under /home.

I just want to see the last few lines in /etc/password to see if you have any user in there!  Otherwise, you can boot into recovery mode from GRUB and create a user if you have none on your system right now.

---

### Post by mahavishnuO on 2006-11-16
the last line says OEM Configuration (temporary user) /home/oem or something like that.

do i use the following code to create a user (from one of your posts from another topic)

```
sudo useradd -m -s /bin/bash john
sudo passwd john

```

---

### Post by mahavishnuO on 2006-11-16
SUCCESS!

i created a new account using

```
useradd -m -s /bin/bash username
passwd username

```

kudos to taurus! thanks a lot for the help.

---

### Post by taurus on 2006-11-16
By the way, you were using the alternate CD for Dapper which means you need to run "sudo oem-config-prepare" to create a new user with sudo capability!  I guess you don't have to now since you already created one by hand.  You can now remove user oem if you wish...  ;)

---

