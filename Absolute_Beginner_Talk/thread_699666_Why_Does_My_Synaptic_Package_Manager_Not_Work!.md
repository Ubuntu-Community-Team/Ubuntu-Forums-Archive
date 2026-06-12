---
title: "Why Does My Synaptic Package Manager Not Work!?"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by lookmomimonlinux on 2008-02-17
This is what I get when I open it: [B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
[/B

---

### Post by timbounceback on 2008-02-17
Applications->Accesories->Terminal; then run:
```
sudo dpkg --configure -a
```

---

### Post by lookmomimonlinux on 2008-02-17
now it says, [sudo] password for victor:

and it won't let me type anything.what am I to do now?

---

### Post by xeth_delta on 2008-02-17
> **lookmomimonlinux said:**
> now it says, [sudo] password for victor:

and it won't let me type anything.what am I to do now?

None of the characters are shown when typing the password in the terminal. Run the command, type the password and press ENTER.

---

### Post by lookmomimonlinux on 2008-02-17
alright, it looks like it did something, some lines ran down the terminal and now it seems to be finished...i don't really understand what those lines meant or what I was doing exactly though. What's the next step?

---

### Post by sb12 on 2008-02-17
try opening synaptic again

---

### Post by lookmomimonlinux on 2008-02-17
well synaptic works now, thank you, BUT while trying to install gtkpod i received this message: E: /var/cache/apt/archives/sun-java6-jre_6-03-0ubuntu2_all.deb: subprocess pre-installation script returned error exit status 1


Can anyone help me fix this , please?

---

### Post by xeth_delta on 2008-02-17
> **lookmomimonlinux said:**
> well synaptic works now, thank you, BUT while trying to install gtkpod i received this message: E: /var/cache/apt/archives/sun-java6-jre_6-03-0ubuntu2_all.deb: subprocess pre-installation script returned error exit status 1


Can anyone help me fix this , please?

try
```
sudo apt-get install -f
```

---

