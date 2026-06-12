---
title: "Kiba dock uninstal?"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by PFSpectrum on 2008-04-09
I installed kiba dock thinking it would be cool folowing a guide from the forums... but the only reason i wanted it was because of the awesome gravity.. but for some reason its not working. So now i just want to remove the thing from my applications bar but im not sure where i installed it to. How would i uninstall this? please help?



also what is the equivilent of C:\program files in ubuntu? like where all software goes by default?

---

### Post by overdrank on 2008-04-09
> **PFSpectrum said:**
> I installed kiba dock thinking it would be cool folowing a guide from the forums... but the only reason i wanted it was because of the awesome gravity.. but for some reason its not working. So now i just want to remove the thing from my applications bar but im not sure where i installed it to. How would i uninstall this? please help?



also what is the equivilent of C:\program files in ubuntu? like where all software goes by default?

Hi and you can try the command ```
sudo apt-get remove --purge kiba-dock
```
and then I would follow with 
```
sudo apt-get autoremove
sudo apt-get autoclean
```

---

### Post by PFSpectrum on 2008-04-09
i put that in and i got this D= 

mike@mike-desktop:~$ sudo apt-get remove --purge kiba-dock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kiba-dock

---

### Post by overdrank on 2008-04-09
> **PFSpectrum said:**
> i put that in and i got this D= 

mike@mike-desktop:~$ sudo apt-get remove --purge kiba-dock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kiba-dock

:confused: Have you tried synaptic manager, and search and remove?

---

### Post by PFSpectrum on 2008-04-09
i searched kiba-dock , and kiba, and didnt come up with any results D=

---

### Post by kujaabi on 2008-05-13
uninstall it using synaptic package manager (under system/administration) not the add/remove application.

---

