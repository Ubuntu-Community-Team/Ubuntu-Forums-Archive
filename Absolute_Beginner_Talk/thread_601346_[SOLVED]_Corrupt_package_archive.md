---
title: "[SOLVED] Corrupt package archive?"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by kexodusc on 2007-11-03
Tried downloading and installing an update in the Update Manager this morning on my Gutsy 64-bit Ubuntu install, but it seems to have generated an error:

E: /var/cache/apt/archives/kdelibs4c2a_4%3a3.5.8-0ubuntu3.1_amd64.deb: corrupted filesystem tarfile - corrupted package archive

That's a first for me.  Any ideas how to proceed?

---

### Post by overdrank on 2007-11-03
> **kexodusc said:**
> Tried downloading and installing an update in the Update Manager this morning on my Gutsy 64-bit Ubuntu install, but it seems to have generated an error:

E: /var/cache/apt/archives/kdelibs4c2a_4%3a3.5.8-0ubuntu3.1_amd64.deb: corrupted filesystem tarfile - corrupted package archive

That's a first for me.  Any ideas how to proceed?
You may try from the command line

```
cd /var/cache/apt/archives
```
Then type:

```
sudo rm kdelibs4c2a_4%3a3.5.8-0ubuntu3.1_amd64.deb
```
Then try to update with 
```
sudo apt-get update
sudo apt-get upgrade
```
Hope this helps good luck!

Edit thanks to Jaco Du Toit :)

---

### Post by kexodusc on 2007-11-03
> **overdrank said:**
> You may try from the command line

```
cd /var/cache/apt/archives
```
Then type:

```
sudo rm kdelibs4c2a_4%3a3.5.8-0ubuntu3.1_amd64.deb
```
Then try to update with 
```
sudo apt-get update
sudo apt-get upgrade
```
Hope this helps good luck!

Edit thanks to Jaco Du Toit :)

Hi overdrank -
I removed the package as you suggested, tried updating and upgrading again and lo and behold it seems to have worked!

So, for educational purposes, what specifically did I do there?  Delete the package that was bad, and download and install again?  

Thanks for the help!

---

### Post by overdrank on 2007-11-03
Yes that is my understanding of the commands. I learned that from this thread [http://ubuntuforums.org/showthread.php?t=600989](http://ubuntuforums.org/showthread.php?t=600989)
That is why the edit
Edit thanks to Jaco Du Toit

---

### Post by kexodusc on 2007-11-03
> **overdrank said:**
> Yes that is my understanding of the commands. I learned that from this thread [http://ubuntuforums.org/showthread.php?t=600989](http://ubuntuforums.org/showthread.php?t=600989)
That is why the edit
Edit thanks to Jaco Du Toit

Well, thanks again for your help!

---

