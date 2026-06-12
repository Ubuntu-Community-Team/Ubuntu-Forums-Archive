---
title: "I need some help with my wireless card..."
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by dswatuga on 2005-11-20
I have a MN-520 and have been struggling to get it working.

I downloaded ndiswrapper and went through synaptic and installed it, but now I have no idea what to do next. Do I open ndiswrapper somehow? I have my driver on a disk for the MN-520 but I don't know how to get it into ndiswrapper.

I'm really new to this and can't follow some of the directions I have found on this site in other posts.

Could someone very slowly help me? I'd appreciate it very much.

---

### Post by danne on 2005-11-20
You'll have to install it using the terminal..
for details check [https://wiki.ubuntu.com//SetupNdiswrapperHowto](https://wiki.ubuntu.com//SetupNdiswrapperHowto)
just follow all the steps mentioned...

---

### Post by aznboi on 2005-11-20
O man it took me so long to install my drivers... turns out htat i needed the latest version of ndiswrapper and i had a pretty old one. make sure u got ndiswrapper by uising the code:
```
sudo apt-get install ndiswrapper-utils
```

then i followed these directions:
```
http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver
```
and had my wireless card up and running.

---

### Post by dswatuga on 2005-11-20
Where do I need to run these commands?

"2. Get yourself in a root shell by running  sudo -s followed by your user's password."

---

### Post by juicybananahead on 2005-11-20
Oh dear, this is going to take a while! :) Open up a terminal by clicking on Applications->Accessories->Terminal. That's where you can type all your commands. Alternatively, press Ctrl+Alt+F1 and login using your login name and password. You can switch back to Gnome at any time by pressing Ctrl+Alt+F7.

---

### Post by dswatuga on 2005-11-20
Thanks, all has gone well until this command though.

"dpkg -i --force-overwrite ndiswrapper-modules-$(uname -r)_1.1-1_i386.deb"

and I get 

"cannot access archive: No such file or directory
Errors were encountered while processing:
 ndiswrapper-modules2.6.12-9-386_1.1-1_i386.deb"

Any suggestions?

---

