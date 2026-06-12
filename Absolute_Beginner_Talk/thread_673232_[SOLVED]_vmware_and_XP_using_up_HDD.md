---
title: "[SOLVED] vmware and XP using up HDD"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2008-01-20
After a lot of research and [expert help here]("http://http://ubuntuforums.org/showthread.php?t=670616"), I have all of vmware-server removed from my HD except as below:
                          ```
peter@Gutsy7_10:~$ sudo updatedb  
 peter@Gutsy7_10:~$ locate vmware  
 /root/.vmware

```Now what is the command to remove (/root/.vmware) I have tried many combinations as you can see here:
                          ```
peter@Gutsy7_10:~$ sudo updatedb  
 peter@Gutsy7_10:~$ locate vmware  
 /root/.vmware  
 peter@Gutsy7_10:~$ locate vmdk  
 peter@Gutsy7_10:~$ sudo su  
 root@Gutsy7_10:/home/peter# remove .trash  
 bash: remove: command not found  
 root@Gutsy7_10:/home/peter# rm .vmware  
 rm: cannot remove `.vmware': No such file or directory  
 root@Gutsy7_10:/home/peter# /trash/.vmware  
 bash: /trash/.vmware: No such file or directory  
 root@Gutsy7_10:/home/peter# rm /trash/.vmware  
 rm: cannot remove `/trash/.vmware': No such file or directory  
 root@Gutsy7_10:/home/peter# rm /.trash/.vmware  
 rm: cannot remove `/.trash/.vmware': No such file or directory  
 root@Gutsy7_10:/home/peter#  
 
```Also what would be the command for removing the (/root/.trash) file ??

---

### Post by Shazaam on 2008-01-20
Not an answer to your command question but a tip...
Right-click the desktop
Choose "Create launcher"
Name it what you want
In the command section input (if using gnome) "gksudo nautilus" (without the quotes)
Use whatever icon you want

!!!!!!!WARNING!!!!!! When you use this launcher you have UNRESTRICTED root access for everything!  Be carefull when using it as you can easily render your installation useless.

There is a slight bug, you have to check off  "View>Show hidden files" (or hit control+h) every time nautilus opens using this launcher.

---

### Post by kindafunnylookin on 2008-01-20
Thanks for your reply. I use nautilus all the time, and I have with this problem as well. However, I forgot the hidden files. Your reminder just gained me back 202GB.
Thanks again.

---

