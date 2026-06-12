---
title: "Re: Getting Wireless Working"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Arken on 2007-03-22
Oh, nvm.
Can you help me with my problem? I can't get WINE to work.

---

### Post by aysiu on 2007-03-22
What program are you trying to run in Wine?

---

### Post by Arken on 2007-03-22
I'm trying to install my drivers for my WMP54GS Linksys Wireless Adapter. Problem is, it's an .exe. So, I tried to get WINE to open it, and it keeps saying that its not in /wine.
Problem is also, I can't make a "wine" folder. I need like the equivelent "Program Files" like a windows, but in Edgy.

---

### Post by Arken on 2007-03-22
Anyhow, Linux is giving me migranes.
Are there any user friendly os's apart from any linux that's free?
Nobodies replying... pm me, and I'll give you my aim so we get a problem fixed, instead of sitting here.

---

### Post by aysiu on 2007-03-22
> **Arken said:**
> I'm trying to install my drivers for my WMP54GS Linksys Wireless Adapter. Problem is, it's an .exe. So, I tried to get WINE to open it, and it keeps saying that its not in /wine.
Problem is also, I can't make a "wine" folder. I need like the equivelent "Program Files" like a windows, but in Edgy.
I don't have any experience with getting tricky wireless cards to work, but I think what you're looking for is *ndiswrapper*, not Wine.

---

### Post by Arken on 2007-03-22
THANK YOU! THANK YOU FOR ALL YOUR HELP! Seriously, the guide said to get wine.

---

### Post by aysiu on 2007-03-22
> **aysiu said:**
> I don't have any experience with getting tricky wireless cards to work, but I think what you're looking for is *ndiswrapper*, not Wine.
One of these threads might help you:
[ HowTo: WPA with wpa_supplicant](http://www.ubuntuforums.org/showthread.php?p=1550472#post1550472)
[HOWTO: Broadcom 4318 Wireless Cards](http://www.ubuntuforums.org/showthread.php?p=1737525#post1737525)
[Wireless network problem with Linksys wmp54gs card](http://www.ubuntuforums.org/showthread.php?p=1665203#post1665203)
[Linksys WMP54GS Wireless Card](http://ubuntuforums.org/showthread.php?t=152292&highlight=WMP54GS)

---

### Post by Arken on 2007-03-22
I need help installing ndiswrapper.
:(

---

### Post by aysiu on 2007-03-22
> **Arken said:**
> I need help installing ndiswrapper.
:(
Type these commands into the terminal: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.backup
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ndiswrapper-utils
```

---

### Post by TopHatCat on 2007-03-22
Exactly what function does ndiswrapper perform, anyway? I'm aware of the Ubuntu bug where restarting your computer can cause your wireless to cease working (although you can still see your SSID on WiFi-Radar). I thought it had something to do with that bug?

---

### Post by Arken on 2007-03-22
> **aysiu said:**
> Type these commands into the terminal: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.backup
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ndiswrapper-utils
```
It asks me for a password but it dont type, then it quits.
Either my computer is retarded or Ubuntu is retarded.

---

### Post by aysiu on 2007-03-22
In this case, Ubuntu's "retarded," but it's not something that's going to be fixed (believe me, [I've tried](http://ubuntuforums.org/showthread.php?t=214393)).

When you type your password in it, you will get **no visual feedback** that it's being accepted. No flashing cursor, no asterisks.

It is still being accepted. Just type your password and hit *Enter*.

---

### Post by Arken on 2007-03-22
Now the window won't open.

---

### Post by Arken on 2007-03-22
Direvtory doesn't exist, apparently. Could you check your code entirely? Maybe say like: 
sudo mv /apt/etc...
*enter*
sudo mv /apt...


Etc.

---

### Post by Arken on 2007-03-22
mv: missing destination file operand after '/etc/apt/sources.list'

---

### Post by Arken on 2007-03-22
Way to not be cool linux, I used to worship you. Now, I hate you.

---

### Post by Arken on 2007-03-23
Umm... I might just move my computer downstairs, and put an ethernet port in...
So, thanks anyhow.

---

