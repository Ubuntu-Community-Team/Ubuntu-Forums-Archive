---
title: "dual booting with Ubuntu"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by smitty423 on 2006-10-19
im currently running a duel boot with windows an Ubuntu and transitioning for a change over from windows.But in the process everytime  i boot to Ubuntu it is alway's updating and wont let me do anything?i'm trying to set it up to the point where i can remove window from the disk c altogether and start new what can i do to speed the updating up? and  do i need to install antivirus and firewall ;)

---

### Post by ReaderRat on 2006-10-19
It takes some time for the updater to download files and install them in your programs. This just takes time. You don't need anti-virus software with Ubuntu, but if you need the security of it, take a look at ClamAV at [**[color=RED]Clam Anti-Virus[/color]**](http://www.clamav.net/binary.html)
You currently have a firewall, I believe, and you can control it by installing **[color=RED]Firestarter[/color]**, a GUI interface for it.

---

### Post by grim918 on 2006-10-20
If you want to stop the updating you can go into```
 System->Preferences->Sessions
``` Then click on Startup Programs tab and remove the entry that says update-notifier. You should keep in mind that if you do this then you will need to run your updates manually. You could set up a crontab to update the computer lets say on a weekly schedule if you don't like the updates taking place every time you log in.

---

### Post by ReaderRat on 2006-10-20
You can install firestarter like this:
Run this in Terminal (Applications>Accessories>Terminal) :
```
sudo aptitude update
```
You will be asked for your password (You will not see what you type in.)
Then run this:
```
sudo aptitude install firestarter
```
This will install Firestarter in your Applications>Internet menu.

---

