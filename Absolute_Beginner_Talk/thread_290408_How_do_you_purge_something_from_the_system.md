---
title: "How do you purge something from the system?"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-11-01
I need to remove the installation of Swiftfox I did and reinstall it through Automatix2, reason is swiftfox doesnt follow the rules of firefox, such as it won't use java but firefox does and other things so I need to remove it. Its not in my adept database nor is it in add/remove. I tried sudo -rm swiftfox and it is still there. Should I try sudo -purge swiftfox? I don't want to affect my firefox installation.

can someone point me in right direction?

---

### Post by xyz on 2006-11-01
I think we need to know how exactly you installed it first.

---

### Post by jrings on 2006-11-01
You can try

sudo aptitude remove swiftfox

and see if it finds it. Otherwise, tell us how you installed it!

---

### Post by maddbaron on 2006-11-01
well i downloaded the .sh file to my desktop then opened terminal did cd then chmod and installed it. I saw on this site someone said how to install firefox so I assumed it was the same for swiftfox since my firefox install works fine. At the time my automatix wasnt working right. now i cant find it in adept or in my add/remove...


now its installed i right clicked my link icon and found something.

> /opt/swiftfox/swiftfox is where the thing said it is.

do I sudo apt-get remove /opt/swiftfox/swiftfox ?

---

### Post by podunk on 2006-11-01
If you installed it through Automatix2 it has a graphical uninstall utility built in.

---

### Post by maddbaron on 2006-11-01
didnt install thru automatix2 used .sh file then cd then chmod 

> cd ~/Desktop
chmod +x install-swiftfox.sh


then it got installed then i added firefox, firefox works fine swift doesnt.

---

### Post by bluenova on 2006-11-01
Swiftfox doesn't have any kind of installation, you just run it. So you can just delete it.

---

### Post by bodhi.zazen on 2006-11-01
You may try:

```
whereis swiftfox
```

and

```
locate swiftfox
```

to locate (and then delete) all files associated with swiftfox.

---

### Post by xyz on 2006-11-01
This not necessarily related to swiftfox but it's nice to know about it:
[Cleaning up all those unnecessary junk files...]("http://www.ubuntuforums.org/showthread.php?t=140920&highlight=remove+files")

---

### Post by maddbaron on 2006-11-01
so delete the .sh file? but then how do i remove the swiftfox links from my menu > Internet area?

---

### Post by bluenova on 2006-11-01
If using Edgy, the menu editor is in your preferences.

---

### Post by jaboua on 2006-11-01
If it's installed in /opt/swiftfox and didn't scatter any other files around, swiftfox and firefox should be able to be installed at the same time... However, solution:
sudo rm -rf /opt/swiftfox

NEVER do this to files you install with apt/aptitude/synaptic/gdebi/adept/whatever (unless you are a pro with special reasons and understand the concequences), only to files you install without uninstallers, like many .sh or .bin files (however many of these have uninstallers as well, uninstallers are usually the best alternatives). RM is a dangerous command, so be careful...

Also, for future reference: you add "sudo" before a command you need special priveleges to execute - in your example, "-rm" is no command, but "rm" is and the minus-whatever are command arguments that control what the command will do.

---

### Post by maddbaron on 2006-11-01
> **bodhi.zazen said:**
> You may try:

```
whereis swiftfox
```

and

```
locate swiftfox
```

to locate (and then delete) all files associated with swiftfox.

> maddbaron@baronworks:~$ whereis swiftfox
swiftfox: /usr/bin/swiftfox /usr/X11R6/bin/swiftfox /usr/bin/X11/swiftfox


So do I 

> sudo delete swiftfox: /usr/bin/swiftfox /usr/X11R6/bin/swiftfox /usr/bin/X11/swiftfox

?

---

### Post by jaboua on 2006-11-01
Icons are usually added in /usr/share/applications, with their icon graphics residing either in /usr/share/pixmaps or /usr/share/icons. You may remove them (but again, I don't want to nag, but RM is dangerous, so be careful...)

---

### Post by jaboua on 2006-11-01
The command is "sudo rm filename1 filename2" or "sudo rmdir emptyfolder" or "sudo rm -rf filename2/foldername1 filename2/foldername2". But are you sure there is no uninstaller?

---

### Post by maddbaron on 2006-11-01
nope no uninstaller i just used the .sh and konsole

so its
>  sudo rm /usr/bin/swiftfox /usr/X11R6/bin/swiftfox /usr/bin/X11/swiftfox

?

---

### Post by maddbaron on 2006-11-01
it worked. thanks for the help

---

