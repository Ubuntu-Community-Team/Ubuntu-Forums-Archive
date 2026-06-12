---
title: "removal help"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by skyjacker on 2007-10-23
Please help. I need to remove kontact COMPLETLY because the one I have now is broken. I tried removing it with Adept Add/remove, and then "sudo aptitude pruge kontact". Then installed new using Adept Add/remove. When install was finished, I had the same info as before, and it still doesn't work (cannot receive mail):confused:. I know it is set up correctly.  I am really growing weary of this problem.

---

### Post by Dr Small on 2007-10-23
I always use this, to purge my configuration files:
```
sudo apt-get remove *applicationame* --purge
```

Dr Small

---

### Post by skyjacker on 2007-10-23
> **Dr Small said:**
> I always use this, to purge my configuration files:
```
sudo apt-get remove *applicationame* --purge
```

Dr Small Thanks, I'll try it.

---

### Post by Dr Small on 2007-10-23
If that doesn't work, try manually removing the configuration files.

Dr Small

---

### Post by skyjacker on 2007-10-23
> **Dr Small said:**
> If that doesn't work, try manually removing the configuration files.

Dr Small It didn't work. How do I remove the confg files manually?

---

### Post by skyjacker on 2007-10-23
Can anyone help me with this???

---

### Post by skyjacker on 2007-10-24
PLEASE help! No matter what I do, I cannot completly remove kontact and do a re-install. I've tried synaptic (complete remove w/config files), Sudo apt-get remove --purge,etc.etc. After removal I do an install and all my files are still there. I suspect the package I have is broken because I can no longer receive mail. Step by step please, I am fairly new to ubuntu.:confused:

---

### Post by skyjacker on 2007-10-24
Anyone able to help me with this???

---

### Post by skyjacker on 2007-10-24
PLEASE help! No matter what I do, I cannot completly remove kontact and do a re-install. I've tried synaptic (complete remove w/config files), Sudo apt-get remove --purge,etc.etc. After removal I do an install and all my files are still there. I suspect the package I have is broken because I can no longer receive mail. Step by step please, I am fairly new to ubuntu.:confused:

---

### Post by Sef on 2007-10-24
> Anyone able to help me with this???

Please have some patience.  Everyone is a volunteer here, and the person who can answer that may be on here in a few minutes, hours, maybe even a few days.

---

### Post by skyjacker on 2007-10-24
PLEASE help! No matter what I do, I cannot completly remove kontact and do a re-install. I've tried synaptic (complete remove w/config files), Sudo apt-get remove --purge,etc.etc. After removal I do an install and all my files are still there. I suspect the package I have is broken because I can no longer receive mail. Step by step please, I am fairly new to ubuntu.

---

### Post by caffienefree on 2007-10-24
Try locate kontact? Use that output to see if there are still configuration files on your PC when you uninstall.

---

### Post by skyjacker on 2007-10-25
> **Sef said:**
> Please have some patience.  Everyone is a volunteer here, and the person who can answer that may be on here in a few minutes, hours, maybe even a few days.

Sorry, I accidently entered this post answer times since I thought my pc was acting up.

---

