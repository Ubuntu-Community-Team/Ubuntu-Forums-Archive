---
title: "Help with installing a .deb"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by rickhimar on 2006-03-20
Hi,

 I have Ubuntu running on my HP pavilion ze4300. Everything works fine. Had to do some tweaking to get the DLink wireless working. I have one last thing to do and I think I will be up and running. I travel a lot and use Juno as my dial-up ISP. Juno has a debian package and I down-loaded it from their web-site.  I have yet to figure out how to install it. I have tried all kinds of options but this one below is the furtherest I have ever gotten. The command lines and feedback are quoted below:

"rickhimar@DI-624:~$ sudo dpkg -i /home/rickhimar/desktop/juno.deb
dpkg: error processing /home/rickhimar/desktop/juno.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/rickhimar/desktop/juno.deb

I am a completely non-technical type so any help would be apreicated.

v/r rickhimar

---

### Post by arnieboy on 2006-03-20
[QUOTE=rickhimar]Hi,

 I have Ubuntu running on my HP pavilion ze4300. Everything works fine. Had to do some tweaking to get the DLink wireless working. I have one last thing to do and I think I will be up and running. I travel a lot and use Juno as my dial-up ISP. Juno has a debian package and I down-loaded it from their web-site.  I have yet to figure out how to install it. I have tried all kinds of options but this one below is the furtherest I have ever gotten. The command lines and feedback are quoted below:

"rickhimar@DI-624:~$ sudo dpkg -i /home/rickhimar/desktop/juno.deb
dpkg: error processing /home/rickhimar/desktop/juno.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/rickhimar/desktop/juno.deb

I am a completely non-technical type so any help would be apreicated.

v/r rickhimar[/QUOTE]
try the following:
```
sudo dpkg -i /home/rickhimar/Desktop/juno.deb
```
Everything in Linux is case sensitive.

---

### Post by Jucato on 2006-03-20
Try going to the directory where you downloaded the deb file and type:
```
sudo dpkg -i *filename_of_deb*
```

---

### Post by rickhimar on 2006-03-20
Thanks,

That seemed to work, however, I can't find the application. One of the search applications did find some files which I think are in root. I tried the add application tool but it appears to only cover things in repositories. How do I find the application and get it to desktop?

v/r rickhimar

---

### Post by Jucato on 2006-03-20
the executable/binary files for the installed applications are found in /usr/bin (unless stated otherwise). you can run them just by typing the name of the app, (in your case, *juno* I presume) either from the terminal or from a Run command dialog box (Alt+F2).

I'm not familiar with how you add entries in the Applications menu in GNOME, so I can't help you there. Just browse through the /usr/bin directory if you need to look for the apps you installed.

---

