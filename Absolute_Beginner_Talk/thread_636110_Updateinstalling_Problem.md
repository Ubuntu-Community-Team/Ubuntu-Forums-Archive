---
title: "Update/installing Problem"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by spoonman1144 on 2007-12-09
Whenever I try to update to 7.10, or try to install anything it says that it cant install because there can only be one update program running at once, and to close it and try again. The problem is that I cant find what program is running. The computer has been shut down and restarted multiple times and still the same thing. Is there a command that will kill all the currently running programs or something? Im new and I dont know my way around ubuntu.

---

### Post by CRCarl on 2007-12-09
Can you post the results of 
```

ps -ef
```

Thanks, 

C

---

### Post by meborc on 2007-12-09
usually this error occurs when you use apt from terminal at the same time the synaptic package manager is opened...

are you trying to update from synaptic? if so try apt from terminal```
sudo apt-get update
sudo apt-get install update-manager-core
sudo do-release-upgrade
```
be sure to close synaptic first...

edit: there is a good tool for terminal, which you can use to see what processes are running... and KILL them :) ... it is called htop, install it ```
sudo apt-get install htop
htop
```

---

### Post by Majorix on 2007-12-09
If nothing works, try upgrading to Gutsy using the recovery mode. You can choose to boot into recovery mode at the GRUB menu. Then there change all your sources to read gutsy and finally do an apt-get update && apt-get dist-upgrade.

---

### Post by spoonman1144 on 2007-12-09
when i try to install htop it says 
dpkg was interuppted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by CRCarl on 2007-12-09
So run 

```
dpkg --configure -a
```

---

### Post by meborc on 2007-12-09
> **CRCarl said:**
> So run 

```
dpkg --configure -a
```

probably you need to use ```
sudo dpkg --configure -a
```
sudo will give you root permissions

---

### Post by spoonman1144 on 2007-12-09
It wasnt working because I was using 'run dpkg -- configure -a'
but now it says I need superuser privilege

---

### Post by spoonman1144 on 2007-12-09
I got it, thanks everyone

---

