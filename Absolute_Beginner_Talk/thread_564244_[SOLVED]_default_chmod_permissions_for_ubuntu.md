---
title: "[SOLVED] default chmod permissions for ubuntu?"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by superpenguin79 on 2007-09-30
Hi,  started toying around setting up a share this afteroon, and in the midst of configuration it seems to somehow have locked out my home dir from r/w.   Does anyone know the main chmod permissions for the file system and home dir in ubuntu by chance?   Everything else is working fine and I set the home back to 666 and it seems to work and I can still get access to the file system as the sudo, but I wanted to be certain permissions are not going to caus me any further grief... ;)   any best suggestions for chmod permissions for the user I have setup outside of the sudo at this point?   Thanks in advance.

---

### Post by Pumalite on 2007-09-30
[http://catcode.com/teachmod/](http://catcode.com/teachmod/)
[http://www.perlfect.com/articles/chmod.shtml](http://www.perlfect.com/articles/chmod.shtml)
[http://www.aota.net/Script_Installation_Tips/changemode.php4](http://www.aota.net/Script_Installation_Tips/changemode.php4)

---

### Post by superpenguin79 on 2007-09-30
Thanks for the links, I will run through them and give it a shot.  I think I have larger prob's than I thought I had caus I restarted and it would not even load xwindow properly and denied access to cd to the /home dir. I was able to get into the root and can browse all my files, but seems it won't let me get at my former user account.. hehe   Might just be a good point to back up the docs, blow out the system and clean install than to figure out what went awry at this point...  Thanks again

---

### Post by bodhi.zazen on 2007-09-30
You can try changing permissions of your home directory to 700 or 766

System files are owned as root and should remain so. If you changed a number of system files (like / or /etc) it is often easier to re-install.

FYI to become root :```
sudo -i
```

---

### Post by superpenguin79 on 2007-10-01
thanks, tried chmoding as root to a couple other options and logging back in as root when it still wouldn't let me boot the home dir...  tried the sudo -i as well and denied permissions to /etc/sudoers... :(     so... while under root I made the list of stuff I had installed and attempted to grab copies of files I had downloaded and was denied those too...  so... In the midst of a good old fashioned image this morning... Thank god I back up everything important over the network otherwise.. anywho.. Thanks for the help guys. appreciate it.

---

