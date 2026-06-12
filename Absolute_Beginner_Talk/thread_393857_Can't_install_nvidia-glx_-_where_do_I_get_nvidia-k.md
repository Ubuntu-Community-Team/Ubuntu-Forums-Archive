---
title: "Can't install nvidia-glx - where do I get nvidia-kernel?"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by smith.norton on 2007-03-26
I am trying to install nvidia-glx. I have already installed the following two packages.

1. nvidia-kernel-common_20051028+1_all.deb
2. nvidia-kernel-source_1.0.8776+2.6.15.12-28.1_amd64.deb
3. linux-image-2.6.15-23-amd64-generic_2.6.15-23.39_amd64.deb
4. linux-kernel-headers_2.6.11.2-0ubuntu18_amd64.deb
5. linux-restricted-modules-2.6.15-23-amd64-generic_2.6.15.11-1_amd64.deb
6. linux-restricted-modules-common_2.6.15.12-28.1_all.deb

After installing the above, I try to install nvidia-glx.

```
smith@everest:~/software/amd64deb$ sudo dpkg -i nvidia-glx_1.0.8776+2.6.15.12-28.1_amd64.deb
(Reading database ... 86526 files and directories currently installed.)
Preparing to replace nvidia-glx 1.0.8776+2.6.15.12-28.1 (using nvidia-glx_1.0.8776+2.6.15.12-28.1_amd64.deb) ...
Unpacking replacement nvidia-glx ...
dpkg: dependency problems prevent configuration of nvidia-glx:
 nvidia-glx depends on nvidia-kernel-1.0.8776; however:
  Package nvidia-kernel-1.0.8776 is not installed.
dpkg: error processing nvidia-glx (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nvidia-glx
```


The error message says that, I must first install, nvidia-kernel-1.0.8776. But I believe I have already installed the nvidia-kernel-common and nvidia-kernel-source packages. What else do I need to install so that I can proceed with the installation of nvidia-glx?

---

### Post by AtrejuT on 2007-03-26
I don't have nvidia myself, but there is a rather lengthy guide e.g.
[http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/nVIDIA)
for edgy. Maybe that helps...

good luck

atreju

---

### Post by smith.norton on 2007-03-26
Thanks Atreju for your response. I didn't get what I need there.

The installation fails because it is specifially looking for nvidia-kernel-1.0.8776 package. I am running Dapper. I am trying to search the .deb file for this (since I do not have Internet). But I can't find this file for dapper.

Can anyone please help me?

---

### Post by deuchar1 on 2007-03-26
Hey smith.norton.

I just recently installed my Nvidia card (GeForce FX 5200) and had the same problems as you. I found the easiest solution was to run Envy, an installer that grabs all the necessary drivers and sets everything up for you automatically (including OpenGL support).

You can get info on it here... [http://lunapark6.com/?p=2717.]("http://lunapark6.com/?p=2717.")

It's not perfect - it has been known to select slightly incorrect settings, but it worked fine for myself and a lot of my friends with similar cards. 

Oh, and for the record - before running it I found it best to run the inbuilt uninstaller - "Uninstall all nvidia drivers" before installing fresh. It caused issues when I installed over my previous manual install attempts!

---

### Post by Bachstelze on 2007-03-26
What is you current running kernel ?

```
uname -r
```

---

### Post by smith.norton on 2007-03-26
2.6.15-23-amd64-generic

---

### Post by Bachstelze on 2007-03-26
That 2.6.15-23 kernel is outdated. Get a 2.6.15-28 from [http://packages.ubuntu.com](http://packages.ubuntu.com).

---

