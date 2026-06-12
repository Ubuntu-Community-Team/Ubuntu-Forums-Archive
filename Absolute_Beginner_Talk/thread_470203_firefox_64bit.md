---
title: "firefox 64bit"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2007-06-10
I am following this guide [http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435) and now find; 1) I cannot get Java and Flash to work, and 2) I have lost permissions to delete unwanted files from my Desktop.


Any advice appreciated!

---

### Post by HereInOz on 2007-06-10
Do you really need to use the 64 bit version?  You will find that the software and driver support is much better for the 32 bit version.

The 32 bit i386 version will work happily with your AMD64, and could save you some pain.  But then, if this is a "project", and not just wanting to get Ubuntu working, then I understand.  I have never worked with the 64 bit install, so unfortunately, I can't help you.

---

### Post by Blender on 2007-06-10
To get flash working, use  [nspluginwrapper]("http://gwenole.beauchesne.info/projects/nspluginwrapper/") (not in the repos, you'll have to convert from RPMs or compile).
For Java, use the gcj plugin (package is called java-gcj-compat-plugin).

Hope this helps.

---

### Post by tchoklat on 2007-06-10
thanks for you help - any thoughts on the lost permissions?

---

### Post by tchoklat on 2007-06-10
I am getting this message also!
You don't have the right permissions to extract the files to the folder "/home/tony/Desktop

---

### Post by Blender on 2007-06-11
What does
```

$ ls -l ~ | grep Desktop

```
say?

---

### Post by tchoklat on 2007-06-11
tony@tony-desktop:~$ ls -l ~ | grep Desktop
drwxrwxr-x  3 root tony   4096 2007-06-11 22:47 Desktop

---

### Post by viciouslime on 2007-06-11
You might want to try simple64, that will install everything for you:

dpkg --remove simple64 simple64-data
wget [http://www.xnowherex.net/simple64/simple64_0.93_amd64.deb](http://www.xnowherex.net/simple64/simple64_0.93_amd64.deb) [http://www.xnowherex.net/simple64/simple64-data_16_amd64.deb](http://www.xnowherex.net/simple64/simple64-data_16_amd64.deb)
sudo aptitude install python
sudo dpkg -i simple64_0.93_amd64.deb simple64-data_16_amd64.deb

Paste that in to a terminal to install it.As for your desktop, it looks like it has become owned by root, run "gksudo nautilus" browse to /home/<your user name> right click the desktop folder select properties, then go to the permissions tab. Change it back to your username. Voilà. :D

---

### Post by tchoklat on 2007-06-11
tony@tony-desktop:~$ sudo dpkg --remove simple64 simple64-data
dpkg - warning: ignoring request to remove simple64 which isn't installed.
dpkg - warning: ignoring request to remove simple64-data which isn't installed.

tony@tony-desktop:~$ wget [http://www.xnowherex.net/simple64/si...0.93_amd64.deb](http://www.xnowherex.net/simple64/si...0.93_amd64.deb) [http://www.xnowherex.net/simple64/si...a_16_amd64.deb](http://www.xnowherex.net/simple64/si...a_16_amd64.deb)
--23:37:55--  [http://www.xnowherex.net/simple64/si...0.93_amd64.deb](http://www.xnowherex.net/simple64/si...0.93_amd64.deb)
           => `si...0.93_amd64.deb'
Resolving [www.xnowherex.net](www.xnowherex.net)... 70.86.137.98
Connecting to www.xnowherex.net|70.86.137.98|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
23:37:58 ERROR 404: Not Found.

--23:37:58--  [http://www.xnowherex.net/simple64/si...a_16_amd64.deb](http://www.xnowherex.net/simple64/si...a_16_amd64.deb)
           => `si...a_16_amd64.deb'
Connecting to www.xnowherex.net|70.86.137.98|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
23:38:00 ERROR 404: Not Found.


FINISHED --23:38:00--

---

### Post by Blender on 2007-06-11
Hmmm, you don't own your Desktop (:) sounds funny)

I'd say you do the following:
```

sudo chown -R tony:tony /home/tony/Desktop

```

This will make you (and your group) the owner of your Desktop folder as well as 
its contents.

Do you still have problems with the Desktop?

Edit: Didn't see viciouslime had posted a solution.

---

