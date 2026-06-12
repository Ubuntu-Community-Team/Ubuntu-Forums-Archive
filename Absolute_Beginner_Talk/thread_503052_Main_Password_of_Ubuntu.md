---
title: "Main Password of Ubuntu"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by Snitz on 2007-07-17
I finished installing Ubuntu now, but I don't remember typing in a username and a password and now when Ubuntu loads it asks me for a username and password and I'm not being able to get it.

Is there a main user/pass that I should know about? and if not, what can I do about it?

PLEASE HELP!

---

### Post by Majorix on 2007-07-17
Did you really install Ubuntu 5.04? :o

---

### Post by Outrunner on 2007-07-17
Try using 'oem' or 'OEM' as username - without the quotes.

---

### Post by sancho panza on 2007-07-17
Did you follow [these instructions]("https://help.ubuntu.com/community/GraphicalInstall")? It does ask you for username and password. Look at the screenshots.

---

### Post by Snitz on 2007-07-17
No, I installed Ubuntu 7.04.

> Try using 'oem' or 'OEM' as username - without the quotes.
And what about the password?

---

### Post by sanderella on 2007-07-17
Try reinstalling, and remember your user name and password this time.....:?

---

### Post by Synth3t1c on 2007-07-17
> **sanderella said:**
> Try reinstalling, and remember your user name and password this time.....:?

unfortunately this is your only option

---

### Post by Snitz on 2007-07-17
OK. there is seriously something wrong. Because I installed it ni text-mode and it didn't ask me for a graphical mode. Yet, its loading a desktop and it has detected my soudcard.

And now its asking me for a username and a password.

---

### Post by Sweet00th on 2007-07-17
try ubuntu
or leave it blank and hit enter...
if that doesn't work you will have to reinstall, i used text base installer and default name was ubuntu.

---

### Post by Snitz on 2007-07-17
I can't reinstall it as I don't have the CD with me (it's with my friend) and the .iso file is on my windows partition and windows XP is not opening saying that I have a hal.dll file missing after installing Ubuntu.

What to do now?
I tried OEM and it didn't work.

---

### Post by Outrunner on 2007-07-17
[http://www.computerhope.com/issues/ch000490.htm](http://www.computerhope.com/issues/ch000490.htm) :-k

I think it's a known problem, but I don't have any other information besides that.

---

### Post by Snitz on 2007-07-17
Anyway I got the hal.dll from my friend's PC and I booted from windows XP and when I goto recovery mode it asks for my Administrator's password which I have no clue what it is. (Not my "Snitz" pass but the "Administrator" pass)

---

### Post by Outrunner on 2007-07-17
> **Snitz said:**
> Anyway I got the hal.dll from my friend's PC and I booted from windows XP and when I goto recovery mode it asks for my Administrator's password which I have no clue what it is. (Not my "Snitz" pass but the "Administrator" pass)

It's quite possible that you didn't set one while installing Windows. I don't know anyone that does :D Just try pressing 'enter'

---

### Post by Snitz on 2007-07-17
I'll try that, what if I copied the hal.dll from the CD I have it on to the windows dir. Would it work?
At least that way, I can burn ubuntu on a cd and reinstall it.

---

### Post by sancho panza on 2007-07-17
Thats wierd...It shouldnt ask for your password unless you already set it up. A fresh reinstall wont take long, and follow [the instructions]("https://help.ubuntu.com/community/GraphicalInstall") closely this time.

---

### Post by Snitz on 2007-07-17
I'm trying to enter windows XP to be able to make a fresh installation but on the recovery mode of windows its asking for the Administrator's password, I just pressed enter and said that it's the wrong password.

I know you're trying to guess what passwords I type, but that's not the case, I swear I didn't set any password on both OS :P

---

### Post by Snitz on 2007-07-17
I'm reinstalling a fresh copy of windows xp sp1 without deleting my files so I can get in and burn ubuntu. But I guess all my drives are messed up now. I'm in deep ****!

---

### Post by sancho panza on 2007-07-17
Its ok... **** happens! Thats the reason why its always recommended that you backup all your important data/settings before installing any operating system, be it windows or linux. Good luck!

---

### Post by Snitz on 2007-07-17
I have tried reinstalling winxp and it gave me an error and didn't finish, now the grub boot loader is gone and I cannot enter ubuntu anymore.

That sucks. I don't know what to do!

---

### Post by Immolatus on 2007-07-17
In windows, the first established user is admin by default, so the admin password should be that account password.

It sounds to me like you've installed the "alternate" Ubuntu and in that case the default login is user: ubuntu password:oem (<--neither are case sensitive).

My suggestion would be to: 1. reinstall windoz and let it do what ever the hell it wonts.
                                                   2. download and burn ubuntu 7.04 at a low speed like 4X
                                                   3.reboot and let the timer on the first screen run out so it boots "live".
                                                      To insure that you get a graphical install. Also 7.04 did away with tho           whole default user thing so you will be able to input your own.

---

### Post by Immolatus on 2007-07-17
BTW what did the error from win look like??

---

### Post by bapoumba on 2007-07-17
There is a way to change the oem password, but you need to access grub menu to be able to boot in recovery mode. I do not know about the windows things, so if you get there, I mean grub menu, you do not need to reinstall.
I'll be watching the thread, just chime in.

---

### Post by Carlos Santiago on 2007-07-17
Enter in single mode and reset your user password. Just do this:
1. Reboot and in the grub menu select edit (type e)
2. Then select the kernel line and select edit again
3. Dont change anything, just add the word 'single' (without quotes) at the end of the kernel line.
4. Now select boot (I think is option b, check it)
5. When the prompt came up type 
```
ls /home
```
Those are the names of your users. For example lets say you have their the user snitz
6. Now type 
```
passwd snitz

```
7. Just type and confirm the new passwords and dont forget them ;-)
8. Reboot normally and use the new passwords

---

