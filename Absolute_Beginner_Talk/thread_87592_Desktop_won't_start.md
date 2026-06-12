---
title: "Desktop won't start"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-11-08
Since I have no replies from the Breezy group....:???: 

SInce my upgrade to Breezy I am unable to boot into the desktop. My system always stop at the CLI login. I ahve to login and then run "startx" to get the desktop up. Then I can only have one user open at a time. I have tried a lot of things, the most useless so far is to configure Xserver. Maybe someone here have the info I need???

---

### Post by yoyoned on 2005-11-08
If when you type startx everything works,  the problem is that the display manager is not starting.  try installing gdm
```
sudo apt-get install gdm
```

---

### Post by GrootBrak on 2005-11-10
I upgraded again and installed GDM seperately. Now my login works perfectly!!! Don't know if there was an update in breezy or not that also could have effected it, but the upgrade definetely did not include gdm this time, I had to install seperate. Unfortunatley I never checked the version I had before I installed gdm. Thank you  **_so_** much yoyoned!!!

---

