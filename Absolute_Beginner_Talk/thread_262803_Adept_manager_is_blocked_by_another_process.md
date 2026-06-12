---
title: "Adept manager is blocked by another process"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by buntolith on 2006-09-22
Hi,

I'm running Kubuntu 6.06. Yesterday I tried to download the sun-java5-plugin plus 7z program. I left the computer running for a while and when I checked the progress of the download it had stopped at 20% because I had to approve to some sort of licence agrement for the java plugin. But I couldn't click ok or go return because the download had frozen. I thought I'd give it another try tomorrow. So I stopped the adept manager. When I try to run the adept manager today I get the following message:

"You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one"

Now I don't know what to do here. I had a look in the performance monitor/process table but I couldn't find any processes to kill. 

Does anyone have a clue of what to do?

---

### Post by Jucato on 2006-09-22
run this in Konsole:

```
sudo dpkg --configure -a
```

That will basically continue where the installation was stopped, that is, during the license agreement.

---

### Post by Rul on 2007-11-28
Thanks I had the same problem, but as soon as I ran that command it told me something about a mistake during an upgrade and then it started to work, Great!!!

---

### Post by nichpakaich on 2008-03-21
Great, just the same issue I faced before, now it works :)
Thanks.

---

### Post by FergusMorris on 2008-06-21
Thank you! I too had this problem and have now fixed it!

---

