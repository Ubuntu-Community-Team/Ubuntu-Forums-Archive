---
title: "Opera and flash - again..."
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by lodravah on 2006-12-10
Again about Opera in Ubuntu. I installed flash 9 beta, and then learned there was a problem concerning opera 9. Fair enough, I think. They say they're working toghether with Opera to fix it, so I'll wait until maybe the right fix is here. In the meantime, the flash 9 keeps crashing my beloved opera. When there is flash about, the browser locks up, casting my Ubuntu/Xfce/686 - box into a severe CPU - usage problem. The usage spikes and stays there until I have to kill the process. So I was thinking of installing flash7 again, until 9 works with opera. I downloaded the flash7 - tar.gz, but how to install it correctly? 

Help wanted :)

---

### Post by jpkotta on 2006-12-10
But you can install flash from the repos:
```
sudo aptitude install flashplugin-nonfree
```
If you want to keep flash 9 and use flash 7 with Opera, then install one of the flashes to $HOME; I think this is the default for the installer in the tarball.  Then set Opera's plugin search path to not look in the place where flash 9 is.

---

### Post by igknighted on 2006-12-10
If you extract the flash7 tarball there should be a flashplayer.so file (or something close).  Just put that file in the /usr/lib/opera/plugins folder (overwriting any file with the same name already there, and it should be fine

---

### Post by lodravah on 2006-12-10
Okay, I see.. But now I have a new problem. I'm not allowed to write to the files in /usr! Apparently I don't have permission, which I don't understand why. I only have my own profile on the pc, and it always worked before. Anyone?

---

### Post by igknighted on 2006-12-10
You need to use 'sudo' to act as root user for dealing with any files outside of /home/username/.  You have two options.  You can use the CLI to do it all, or you can launch nautilus (the file browser) as root. The cli method goes as follows:
```
sudo cp /path/to/flash/file.so /usr/lib/opera/plugins/
```

or to launch nautilus as root so you can drag and drop:
```
sudo nautilus
```
then navigate to the /usr/lib/opera/plugins/ folder and drag and drop there.

---

### Post by KedDeK on 2006-12-10
I am having the same crashes with Opera and Flash 9 (from the repos). I hope Opera devs can fix this ASAP.

---

### Post by brn on 2006-12-10
Regarding flashplayer:  I have been wondering about this for some time. As described in another thread, I have been trying for awhile.  I have done everything suggested to install it (for Firefox and Opera).  It seems to be in place but I have no way to be certain that it works.  Can anyone suggest a way it can be tested?

---

### Post by jpkotta on 2006-12-11
Copy libflashplayer.so (for flash 7) to ~/.opera/plugins, you don't need to be root then.  Then you can tell opera to look there for plugins, but not whereever flash 9 is, thus you can continue to use it (flash 9) with Firefox.

---

### Post by banished_one on 2008-02-10
> **igknighted said:**
> If you extract the flash7 tarball there should be a flashplayer.so file (or something close).  Just put that file in the /usr/lib/opera/plugins folder (overwriting any file with the same name already there, and it should be fine

this worked for me many thanks (im using opera 9.50b and latest flash)

---

