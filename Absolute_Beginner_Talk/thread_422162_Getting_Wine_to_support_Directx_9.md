---
title: "Getting Wine to support Directx 9?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by doan_m on 2007-04-24
Ok. SO I have fiesty installed on the comp with the most recent version of Wine under my belt. (0.9.35 IIRC). I installed Warhammer 40,000: Dawn of War: Dark Crusade, but then it failed to run. I know this is because I dont have any direct X9 support for it. I already have the WineCVS.sh file but I need to know how to install it, and also what other things I need to install.

Thanks in advance.

---

### Post by pay on 2007-04-24
Make the script executable ```
chown 775 WineCvs.sh
./WineCvs.sh
```or just```
sh WineCvs.sh
```If you want to install a program  you will probably want to be root though so put sudo infront of the commands.

---

### Post by doan_m on 2007-04-25
hmmm... it says that it cant open for some reason when I type those commands in those terminal. I figure i'm doing something wrong.

---

### Post by justin whitaker on 2007-04-25
> **doan_m said:**
> hmmm... it says that it cant open for some reason when I type those commands in those terminal. I figure i'm doing something wrong.

Probably need to throw a su or sudo before those commands then. Permissions might be the issue.

---

### Post by doan_m on 2007-04-25
well, i am the only admin file on the comp so i dont think permission is an issue. I also did add sudo to this commands. 

All right this is what i did:
 
the WineCVS.sh file is saved on my desktop. I just opened terminal and typed in those commands(i used the second one that pay gave me) and i did add sudo before then. Still it wont open.

---

### Post by marko_4454 on 2007-04-25
are you in the Desktop's directory?

if not, just do this:

```
sudo sh Desktop/WineCVS.sh
```
<This is the relative path trying to access it from home>

Also, try and copy/paste the exact error you are given. That helps way more than just us trying to guess the error.

---

### Post by doan_m on 2007-04-25
This is the result I got using the command you gave me.
> milo@milo-desktop:~$ sudo sh Desktop/WineCVS.sh
test: 43: ==: unexpected operator
Desktop/WineCVS.sh: 48: Syntax error: "(" unexpected
milo@milo-desktop:~$ 




Man do I suck.

---

### Post by marko_4454 on 2007-04-25
> **doan_m said:**
> This is the result I got using the command you gave me.


Well, the problem is inside the Wine, not your problem anymore. Sadly, I dont know how to fix it.
you can go inside the shell, but I do not recommend. You should wait until someone smarter than me is able to help you. 
Sorry....

> Man do I suck.
Do you think everyone learned everything in one day? lol...not really...we all suck at some point. Its just that linux has a bigger learning curve. 
Enjoy the ride :)

---

### Post by Verbious on 2007-04-28
you will need to type

```
sudo bash WineCVS.sh
```

But running this script will not fix your problem of DirectX not working properly.  There is probably not enough DirectX support built in to Wine to run your game.

Have you checked here:  [WineHQ APPDB]("http://appdb.winehq.org/appview.php?iVersionId=2576") ?

It appears to work very well under Wine.  Many Silver and a Gold rating.

The WineCVS script is to build wine from the CVS.

0.9.36 Wine was just released.

---

