---
title: "How to get rid of being asked my password"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-05-31
I solved the problem of being asked pw at bootup, by going to administration->login window->security. But still, if I put the computer in "standby" mode, then upon reawakening it asks me my password. And upon going into "administration" it asks me my password. And at some time during the downloading and installing of programs, it asks me my password. There are many times and occasions when it asks me my password. I don't need the security, I'm the only one using my computer!!! How do I get it to stop checking my password???

---

### Post by dondad on 2007-06-01
I am quite new at ubuntu, but this is what I have seen so far:

You probably could get rid of the asking all of the time by running as root, but that is not a good thing to do. The reason for the password is that you are usually running as a user, but can bump up to admin status for an operation, then return to user status.

The way that I see it, the password is not so much for security, but rather to protect you from yourself. It makes you think before you do something that could damage your install. Windows asks all kinds of questions about whether you "really, really" want to do something, but linux does not. If you run at root and accidentally tell it to delete your entire partition, it will say "ok" (after it is done). If you can do anything you want without a password, eventually you will type something wrong and poof!

It may seem like a pain, but I wouldn't do it
(Just 2cents from a very new user)

---

### Post by Patrick K on 2007-06-01
I concur.

---

### Post by Inxsible on 2007-06-01
> **swarup said:**
> I solved the problem of being asked pw at bootup, by going to administration->login window->security. But still, if I put the computer in "standby" mode, then upon reawakening it asks me my password. And upon going into "administration" it asks me my password. And at some time during the downloading and installing of programs, it asks me my password. There are many times and occasions when it asks me my password. I don't need the security, I'm the only one using my computer!!! How do I get it to stop checking my password???

It will always ask you for your password if you want to change some system setting. The re-awakening from stand-by lock can be disabled like so
Press Alt + F2 and type in gconf-editor

Once it opens Go to apps -- > gnome-power-manager. Look for keys called 
lock_on_suspend
lock_on_hibernate
lock_on_blank_screen

Disable all three of those and you should be good to go !

---

### Post by eentonig on 2007-06-01
You know, there is a reason why linux was so much more secure then windows.:-k

The reason why it asks you you're password, is because 
1. you're trying to do something beyond the safe boundaries of your $HOME folder.
2. The application needs to provide a password to an external server and has that in your keyring.

Personally, I think it's way better then blindly typing <ok>. If you don't like it, I thing you'll be more comfortable by using windows.

But I would advice against any technique that removes or eliminates the need to enter passwords when doing system related tasks. (Unless you're the only user and your pc will never connect to the internet.)

---

### Post by mlentink on 2007-06-01
You only ***think*** you're the only user of your computer. There are those who enjoy turning your machine into a part of a botnet to be used for spamming or even more malicious things.  If you don't believe me, open up your firewall.
Unix/Linux was designed from the ground up to be a system for multiple users, so it takes into account that not all users are friendly, good natured citizens. Windows wasn't and hence the many security problems. Even so, in Viista, Microsft has adopted which was common practice in *ix systems for many, many years: the need to type in a password as soon as you want to do system-changing or endangering activities. Even if you were to go back to Windows, you'll have to get used to this. For your own benefit.

---

### Post by zvacet on 2007-06-01
It is not recommended thing to do but if you want it here you go

[http://ubuntuforums.org/showthread.php?t=435906&highlight=visudo]("http://ubuntuforums.org/showthread.php?t=435906&highlight=visudo")

---

### Post by swarup on 2007-06-03
> **Inxsible said:**
> It will always ask you for your password if you want to change some system setting. The re-awakening from stand-by lock can be disabled like so
Press Alt + F2 and type in gconf-editor

Once it opens Go to apps -- > gnome-power-manager. Look for keys called 
lock_on_suspend
lock_on_hibernate
lock_on_blank_screen

Disable all three of those and you should be good to go !


I tried to follow the above--but when I press "Alt + F2", nothing happens! So I couldn't get past the first step. Please help someone.

---

### Post by scott_g on 2007-06-03
> **swarup said:**
> I tried to follow the above--but when I press "Alt + F2", nothing happens! So I couldn't get past the first step. Please help someone.

The Alt + F2 just opens a run command.  You can get the same result by opening a terminal and typing the command.

As a side note, there is link to this configuration dialogue in the main menu (for gnome), it may be hidden though (right click on the menu, click edit, then find "System Tools", click on it, then check "Configuration editor".  Close the menu editor, browse through the main menu to System Tools, and there should now be a link to "Configuration Editor"; click on it, and you will have bypassed typing the command into the terminal.)

I would also advise against disabling the password protection; 99/100 times you won't need it, but on that last time, you'll kick yourself for disabling it; I know I have.

Either way works;
Scott

---

### Post by Feba on 2007-06-03
Please don't disable sudo. It seems annoying at first, but after awhile, you'll hardly ever find yourself using it more than two or three times a day, and you really appreciate how secure it makes your system.

---

### Post by drs305 on 2007-06-03
You are presumably an adult and the choice to disable or alter password protection is yours (ok, you've been warned). You can change how often you are asked for your password. The default is either 10 or 15 minutes, depending on what source you read. I don't know if it would carryover after hibernation. 

To change it from the default time:

Make a backup copy of /etc/sudoers:
```
sudo cp /etc/sudoers ~/Desktop/sudoers.bak
```
Edit the /etc/sudoers file. Note: this is a file you don't normally want to mess with. You edit it in a special way (ok, you've been warned again):
```
sudo visudo
```
Add the following line. Change the username to your username and the 10 to how many minutes you want to pass before you are asked again for your password:
```
Defaults:username timestamp_timeout=10	
```

Once you have edited the file, exit and save the file by CTRL X to exit, Y to save. ENTER (it will say it is saving as default name of /etc/sudoers.tmp - just hit enter to whatever name automatically appears).

---

### Post by swarup on 2007-06-03
> **scott_g said:**
> The Alt + F2 just opens a run command.  You can get the same result by opening a terminal and typing the command.

As a side note, there is link to this configuration dialogue in the main menu (for gnome), it may be hidden though (right click on the menu, click edit, then find "System Tools", click on it, then check "Configuration editor".  Close the menu editor, browse through the main menu to System Tools, and there should now be a link to "Configuration Editor"; click on it, and you will have bypassed typing the command into the terminal.)

I would also advise against disabling the password protection; 99/100 times you won't need it, but on that last time, you'll kick yourself for disabling it; I know I have.

Either way works;
Scott

Thanks to both Scott and Feba. I was able to follow the above directions without a hitch. As per both of your suggestions, I will not disable sudo or password protection, in order to maintain the security of the system. But I assume that disabling the request for a password when reawakening from standby/suspend, will not present a security risk. So I'll satisfy myself with this for now, until I become more familiar with the workings of Ubuntu. Thanks again.

---

### Post by swarup on 2007-06-03
> **drs305 said:**
> You are presumably an adult and the choice to disable or alter password protection is yours (ok, you've been warned). You can change how often you are asked for your password. The default is either 10 or 15 minutes, depending on what source you read. I don't know if it would carryover after hibernation. 

To change it from the default time:

Make a backup copy of /etc/sudoers:
```
sudo cp /etc/sudoers ~/Desktop/sudoers.bak
```
Edit the /etc/sudoers file. Note: this is a file you don't normally want to mess with. You edit it in a special way (ok, you've been warned again):
```
sudo visudo
```
Add the following line. Change the username to your username and the 10 to how many minutes you want to pass before you are asked again for your password:
```
Defaults:username timestamp_timeout=10	
```

Once you have edited the file, exit and save the file by CTRL X to exit, Y to save. ENTER (it will say it is saving as default name of /etc/sudoers.tmp - just hit enter to whatever name automatically appears).

Thanks, drs305. The above is useful to have. I'll save it for when I am more familiar with what I really need. For now, it's a bit more complex than what I want to toy with. But I may do it in the future, when I have a better handle on how it all works. --Thanks again.

---

