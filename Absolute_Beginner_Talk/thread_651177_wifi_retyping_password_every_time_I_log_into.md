---
title: "wifi retyping password every time I log into"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by jordilin on 2007-12-27
Is there any way to make Gnome remember my wifi password, so I do not have to type it everytime I log into a session. Gnome keyring does not seem to remember it.

---

### Post by salamba on 2007-12-27
Install libpam-gnome-keyring

as long as you actually logon through gdm  (not with auto logon) then your keyring should be unlocked.

---

### Post by Ghost_Dog on 2007-12-27
Where do you find the libpam-gnome-keyring module.

---

### Post by walkerk on 2007-12-27
I suggest using WICD instead of Network Manager. It will connect to the internet at boot w/out asking for your password. Also it will allow you to set static IPs.

See my signature for an installation guide or simply visit [wicd.sourceforge.net]("http://wicd.sourceforge.net")

libpam-gnome-keyring should be installed by default... If not in terminal type:
```
sudo apt-get install libpam-gnome-keyring
```

Though there is quite a bit more work to get it to not ask for your password... search the forum for other threads... there are several. Or use the better alternative: WICD

---

### Post by jordilin on 2007-12-27
libpam is installed by default it seems. I have removed it and then the keyring popped out for the password. When I put my admin pwd it popped out again. It seems that he did not like my admin password (I use two users with admin privileges in my box). I have reinstalled libpam and now it does not pop out. The network applet tries to connect when I log into but after a while asks for the password again. 
I see that the keyring stores the wifi password, but it is different than the one I type. Don't know if it is encrypted inside the keyring. Imho keyring has always been a dark side for me in gnome. Kde deals with this stuff much, much better.
If someone can shed more light on this problem...

---

