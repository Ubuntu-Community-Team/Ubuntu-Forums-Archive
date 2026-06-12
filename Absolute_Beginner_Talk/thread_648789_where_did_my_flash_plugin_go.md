---
title: "where did my flash plugin go???"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by faraz_k86 on 2007-12-24
i downloaded the flash plugin, i was notified that it is an installer, after it was downloaded i was notified that  ./unstall_flash_9_linux.tar.gz is downloaded but not installed???


what now how do i get to that installer?

---

### Post by forestpixie on 2007-12-24
./ means it's hidden - check in your home folder for it

---

### Post by faraz_k86 on 2007-12-24
it is not there. even after i enabled the hidden folders

---

### Post by forestpixie on 2007-12-24
what did you use to download it - firefox? If you used firefox it downlods to desktop unless you've changed it - have a look there

also try to locate it -
```
locate ./install_flash_9_linux.tar.gz
```

Edit - if it doesn't find it try to update dbase first
```
sudo updatedb
```

---

### Post by faraz_k86 on 2007-12-24
its not there and the locate command does not work either

---

### Post by forestpixie on 2007-12-24
try to update dbase - ```
sudo updatedb
```

and I assumed 'unstall' to be a typo so changed it in locate command 

are you sure it actually downloaded, if you can download it again - check where it's going to be downloaded to

---

### Post by faraz_k86 on 2007-12-24
yes it was downloaded to the location i specified, im sure of that.


and i updated the db and then located but even then it was not located??


isnt there any search tool for ubuntu that finds files in the entire disk, just like windows has

---

### Post by forestpixie on 2007-12-24
if you know what location you specified - are you sure it's not hidden there.

there is a search in nautilus - but I've never had much luck with it and prefer to search in terminal

if the download location was another hdd I'm not usre that locate would find it without changing to the hdd

not much else I can do to help

---

### Post by ~LoKe on 2007-12-24
```
sudo apt-get install flashplugin-nonfree
```
Or if you prefer to do it manually...
```
cd ~/ && wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz && tar xvf *linux.tar.gz && cd install_flash* && ./flashplayer-installer
```

---

### Post by faraz_k86 on 2007-12-24
~Loke you are asking me to download the app again, which i have already done, i have downloaded it and now i cant find the installer.


i only have 1 hdd.

isnt there any way to find all the .tar.gz files in the disk?

---

### Post by ~LoKe on 2007-12-24
```
sudo updatedb
locate 9_linux.tar.gz
```

If that doesn't output anything it means it's no longer on your system.  You may have downloaded it into a temporary directory (/var/cache or /tmp)

---

### Post by forestpixie on 2007-12-24
would this work

```
cd /
```
```
sudo find . -name "*.tar.gz" -print
```

we've tried updatedb and locate

---

### Post by ~LoKe on 2007-12-24
Well, if locate didn't find it, it probably doesn't exist.  However, no reason not to try.

```
cd / && sudo find . -name "*linux.tar.gz" -print
```

---

### Post by forestpixie on 2007-12-24
aaah - does the && make it do any second command after the first?

---

### Post by ~LoKe on 2007-12-24
> **forestpixie said:**
> aaah - does the && make it do any second command after the first?

Yep!  && means that if the first command was successful, proceed to the second.

---

### Post by chewit on 2007-12-24
I got the exact same problem. I thought I had install Flash, but it hadn't worked. I think, it was due to my lack of knowledge of installing apps (this was my 1st day using Ubuntu).

In the end, I tried installing using the terminal, and it worked.

---

### Post by faraz_k86 on 2007-12-24
thx a lot guys that did it.

> faraz@faraz-laptop:/$ sudo find . -name "*linux.tar.gz" -print
./var/cache/flashplugin-nonfree/install_flash_player_9_linux.tar.gz



now can anyone please explain to me what the command means.

i understand cd / and the && but what is the . -name and the -print commands?

---

### Post by ~LoKe on 2007-12-24
> **faraz_k86 said:**
> now can anyone please explain to me what the command means.

i understand cd / and the && but what is the . -name and the -print commands?

Those are just parameters for the find command.  Anything following a hyphen (**-**) is a parameter.  It's like...do **this** when running a command, line enabling an extra feature.

An example...
```
ls
```
That on its own will list the contents of a directory.  Adding a parameter would be like...
```
ls -la
```
-la means -list all.  It will list the entire contents of a directory, including hidden files.

---

