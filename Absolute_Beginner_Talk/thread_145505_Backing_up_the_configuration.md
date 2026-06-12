---
title: "Backing up the configuration?"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by gonde on 2006-03-16
Hi all, I have one question. I got my laptop with Ubuntu 5.10 installed on it. So eventually I will reinstall it, or install UbunuLite. 
Now the question is :-k : 
cause I didn't installed it and I don't know what was configured on the laptop, is there a way to capture in some log all the settings that I'll need for reinstall. 
For example: WLAN, Sound, Graphic etc. Thanks a lot!

---

### Post by Brunellus on 2006-03-16
not sure about backing up the whole config, but you will NOT need to reinstall cleanly, unless you really want to.

Simply change all references to "breezy" to "dapper" in /etc/apt/sources.list

then

sudo apt-get update
sudo apt-get dist-upgrade

WARNING WARNING WARNING

Dapper is not yet ready for primetime.  But if in the future you want to upgrade, you don't need to clean-install.

---

### Post by towsonu2003 on 2006-03-16
I backup my settings by ```

cd
sudo -i
tar -cvf etc.tar /etc
exit

```

but this is part of a system backup: I'm not sure how useful it would be to search tru the backed up files afterwords...

PS. wait for a while before typing those commands. Someone may come up with a better solution...

---

