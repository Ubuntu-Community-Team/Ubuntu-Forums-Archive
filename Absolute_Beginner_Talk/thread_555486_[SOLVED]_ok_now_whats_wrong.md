---
title: "[SOLVED] ok now whats wrong?"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by leedsdevil on 2007-09-20
ok i installed 6.06 and did all the updates rebooted and went to insatll 7.4 *** i get to the last 8 mins it froze up so i shut it down for a reboot nothing no screen so i hit grub go back one and i get the tan color screen after i enter password  what the heck is up ive not had this problem and now i like to finish the pc plz help....thanks to all that do what they do here

---

### Post by Jeroen Vernooij on 2007-09-20
Hi,
If I understand well, you tried to upgrade 6.06 to 7.04.
This is not supported nor recommended.
You should have upgraded 6.06 to 6.10 to 7.04.

However, to fix your system, I should reboot in recovery mode, login, and type
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

if that doesn't work, try 
```
sudo apt-get -f install
```

If you need more help with that, just post.
Good luck

---

### Post by leedsdevil on 2007-09-20
thx for your reply but ok i get into recovery and code that you gave didnt work at all im not sure bout logging in in recovery mode.. i can get as far as recovery not much further

---

### Post by Jeroen Vernooij on 2007-09-20
Ok what do you see after you entered recovery mode?
A black screen with:
```
<computername>: login:
```??

If so, type your username <enter> password

then type the commands in my previous post.

---

### Post by leedsdevil on 2007-09-20
well i get the black screen yes but i get  root@gdesktop as the last things it said

---

### Post by Ubuntized! on 2007-09-20
so u are already logged on as root?!! aren't u?

---

### Post by Jeroen Vernooij on 2007-09-20
That's good, that means that you are logged in and can type commands.

try to type ```
apt-get -f install
``` and tell me what happens

if nothing happens, type
```
apt-get update && apt-get upgrade && apt-get install ubuntu-desktop
```

---

### Post by leedsdevil on 2007-09-20
ok if thats where i am i tried running the posted lines and i get E:dpkg was interrupted, you must manually run dpkg --configure -a to correct the problem

---

### Post by Jeroen Vernooij on 2007-09-20
Ahh I've had that problem also at one time.
So just type in 
```
dpkg --configure -a 
```
:)

---

### Post by leedsdevil on 2007-09-20
i see this may take some time i will post when this completes

---

### Post by Jeroen Vernooij on 2007-09-20
Ok, most probably it will be fixed after that.
Try to reboot after that.

If it isn't fixed, get back to recovery mode and type
```
apt-get update && apt-get upgrade && apt-get install ubuntu-desktop
```

---

### Post by leedsdevil on 2007-09-20
ok great i will do that  and if any further problems arise i will repost thx for the great help

---

### Post by leedsdevil on 2007-09-20
ok well this was going fine till... it seems its hanging up( generating mime/codec maps )is this normal? been bout 15 mins

---

### Post by Jeroen Vernooij on 2007-09-20
Crap, that sucks. Well maybe give it some more time. Is your harddisk still being accessed? You can see this when your Harddisk-LED on your computer flickers.

You can also see what's going on by entering another console, by pressing:
CTRL-ALT-F1
If nothing happens, try CTRL-ALT-F2 or F3

If something happens, you will see <computername>:Login:

type your username, enter, password, enter
then you are in a different console.

Type 'top' to see if dpkg is still running and using CPU%. 

You can go back to the dpkg console by typing
CTRL-ALT-F7 or some other F-key (don't know which you are in now)

---

### Post by leedsdevil on 2007-09-20
WOW thanks after all that.. what i did was shut it down reboot and redid in new kernel its works YAY thanks for sticking with me

---

### Post by Jeroen Vernooij on 2007-09-20
Strange:-?
But at least it is working now. \\:D/

Next time to prevent problems just upgrade to the next version, and don't skip one :)
If you skip one, a complete reinstall is much better.

---

