---
title: "How to free disk space..."
date: 2005-08-17
forum: Absolute Beginner Talk
---

### Post by alquimista on 2005-08-17
Hi,
I planned to train myself on linux and comming back and forth from WinXP; for this I have a 5Gb partition for Kubuntu. Little by little I'm getting myself away from Windows... the problem is that my 5gb Kubuntu partition has 95% usage... and getting bigger.
I got into Synaptic to check installed software and get rid of those I don't use... but the list is huge and many is KDE system software I can't uninstall. Is there a way to free spece, like in Win, deleting tmp files (or similar) not used? 

I noticed too that there is software I was not aware of, and was not in the K menu, like kjots or kdf. Is there a way to indentify user applications (not system softwrae) I can get rid of?

Yesterday I donwloaded amarok-1.3, yet it didn't work and, and reinstalled the  original amarok, removing the 1.3 install. Is there a place where the amarok-1.3.deb is sotred so I can delet it?

Thanx,
Guillermo

---

### Post by kiddo on 2005-08-18
Especially if you have a fast filesystem such as ReiserFS, I would strongly suggest using the application named "Filelight". You will know where you space ran off.

---

### Post by doclivingston on 2005-08-18
.debs that have been downloaded get put in /var/cache/apt/archive, you can remove everything from this directory but "lock" and "partial" safely.

```
sudo rm /var/cache/apt/archive/*.deb
```

---

### Post by alquimista on 2005-08-18
Thank you very much!!!!!!!!!!

---

### Post by AudioPhlake on 2008-07-24
Thank you, as I am in a similar situation- XP user looking to migrate (and loving what I see! :) ).  On my system, the folder name was "archives" with a plural "s".  I don't know if this is a typo or just my system.


sudo rm /var/cache/apt/archives/*.deb

Thanks again.

---

