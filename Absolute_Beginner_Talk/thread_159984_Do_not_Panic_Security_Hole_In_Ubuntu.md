---
title: "Do not Panic: Security Hole In Ubuntu"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by catric69 on 2006-04-13
“An extremely critical bug and security threat was discovered in Ubuntu Breezy Badger 5.10 earlier today by a visitor on the Ubuntu Forums that allows anyone to read the root password simply by opening an installer log file. Apparently the installer fails to clean its log files and leaves them readable to all users. The bug has been fixed, and only affects The 5.10 Breezy Badger release. Ubuntu users, be sure to get the patch right away.”

[http://ubuntuos.com/2006/04/security-hole-in-ubuntu.html#comments](http://ubuntuos.com/2006/04/security-hole-in-ubuntu.html#comments)


How do I get the patch for this?  Or is it already been updated with the new kernel that I installed?

Eric.

---

### Post by Sutekh on 2006-04-13
This was fixed within 11 hours of the discovery (and this was weeks ago now), if you have done *any* Ubuntu software updates since then, it is fixed.

You can check for yourself, the first post will show you where the hole was.

[http://www.ubuntuforums.org/showthread.php?t=143334](http://www.ubuntuforums.org/showthread.php?t=143334)

---

### Post by catric69 on 2006-04-13
Thanks for the quick reply! 

How often are patches released?

Eric.

---

### Post by drummer on 2006-04-13
[QUOTE=catric69]Thanks for the quick reply! 

How often are patches released?

Eric.[/QUOTE]
Whenever they need to be, often every few days. I can't remember exactly, I've been using dapper which has ~30-50 updates a day :P

---

### Post by Sutekh on 2006-04-13
As soon as they are available??  I don't understand what you mean.  There is no real schedule for releasing patches.  They are done if something needs fixing and released ASAP.

---

### Post by jimrz on 2006-04-13
[QUOTE=catric69]Thanks for the quick reply! 

How often are patches released?

Eric.[/QUOTE]

If needed, as soon as developed/tested. No waiting around for scheduled "Black Tuesday" type cycles here

---

### Post by catric69 on 2006-04-13
[QUOTE=jimrz]If needed, as soon as developed/tested. No waiting around for scheduled "Black Tuesday" type cycles here[/QUOTE]


Gotcha! I am new to Linux/Ubuntu and I don't know how things fully work around the Ubuntu community.  Seems like a tight niche family and I will hopefully be staying a while.  Thanks!

Eric.

---

### Post by x5452 on 2006-04-13
so when you do the sudo apt-get update or upgrade, (whats the code for upgrade?) it installs and fixes patches?

also can someone tell me how to stop a single notification from always coming up to update my ffmpeg, i need to keep the old one, but the new notifier wont leave me alone

---

### Post by Sutekh on 2006-04-13
```
sudo apt-get update
```gets a new list of packages from your repositories
```
sudo apt-get upgrade
```searches the repositories for newer packages (based on the list of packages obtained from an update)

---

### Post by aysiu on 2006-04-14
[QUOTE=catric69]“An extremely critical bug and security threat was discovered in Ubuntu Breezy Badger 5.10 earlier today[/QUOTE] "[E]arlier today"? Try a month ago...

---

### Post by 3rdalbum on 2006-04-14
[QUOTE=x5452]also can someone tell me how to stop a single notification from always coming up to update my ffmpeg, i need to keep the old one, but the new notifier wont leave me alone[/QUOTE]

Try going into Synaptic and clicking on the ffmpeg package. Go to the Package menu and choose "Force Version...". You'll be asked which version you want to use. Choose the currently-installed version.

Does that stop the notifications?

---

### Post by x5452 on 2006-04-14
im sure it would have :mrgreen:  I had just heard from someone of an option in the edit prefs menu in synaptic to lock current version, and that worked.  thank you

---

