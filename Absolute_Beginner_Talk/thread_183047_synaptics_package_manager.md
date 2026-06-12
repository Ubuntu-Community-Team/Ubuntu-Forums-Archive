---
title: "synaptics package manager"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2006-05-27
Hi, I have never been able to update my packages through synaptics because I have never had it working! I am getting this error:

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

This happens when i try to update the packages using the reload button. I know it is nothing to do with the internet connection because it is configured in exactly the same way as the rest of Ubuntu and that all seems to work fine. Hope someone can help, because it means I cant get any packages, and everything i need to install so far needs packages!

Thanks in advance!

---

### Post by tkjacobsen on 2006-05-27
what is in your /etc/apt/sources.list

---

### Post by tkjacobsen on 2006-05-27
try to back it (sources.list) up, and make a new:
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by Sef on 2006-05-27
Have you seen if the same problem comes up if you use the terminal?

sudo apt-get update

sudo apt-get upgrade

---

### Post by tommy1987 on 2006-05-27
if u do sudo apt-get update I get loads of lines, and after each could not connect to blah blah. So im trying to reconstruct my sources.list at the moment.

---

### Post by sam hassell on 2006-05-27
if you want an easy solution and are on breezy, try automatix.
[http://ubuntuforums.org/showthread.php?t=138405&highlight=sources.list](http://ubuntuforums.org/showthread.php?t=138405&highlight=sources.list)

---

