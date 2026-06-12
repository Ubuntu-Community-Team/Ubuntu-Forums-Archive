---
title: "How to install .tar.gz?"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by nzk on 2006-08-21
I know tar zxvf untars it but I havent the slighest clue how to install it

Also programs that I download from Synaptic are never installed for some reason :\

---

### Post by ironfistchamp on 2006-08-21
Once you have used the command

```

tar -xvzf thetarfile

```

there will be a folder of the same name. That has the contents of the tar. To install it depends on what was actually in it. If it was source then you will need to start off by typing

```

sudo apt-get install build-essential

```

That will get you what you need for compiling from source. Next you need to type

```


cd nameofnewdir
./config
(if you get no errors type this)
make
sudo make install

```

As for the Synaptic apps not being installed can you be a little more specific. Do you mean they don't show up on the menu or they really aren't there or there are erros.

Hope this helped.

Ironfistchamp

---

### Post by nzk on 2006-08-21
The synaptic apps are just...not...there

---

### Post by MaximB on 2006-08-21
they are there
they are usually at your .bin folder.

---

### Post by taurus on 2006-08-21
> **nzk said:**
> The synaptic apps are just...not...there

What apps are you talking about?  When you use synaptic, you normally install the binaries of your apps and they are usually in /bin, /usr/bin, /sbin, /usr/sbin, etc.

---

### Post by nzk on 2006-08-21
Also when I try to untar it keeps returning:

tar: yam-linux.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by taurus on 2006-08-21
Make sure you are in the directory where you've downloaded it, usually in ~/Desktop!!!  Also, you need to download it in binary mode, not ASCII mode...

```
cd ~/Desktop
```

---

### Post by nzk on 2006-08-21
E: Invalid operation make
or 
bash: make: command not found


Is what happens when i try to install

---

### Post by taurus on 2006-08-21
You need to install build-essential first before you can compile anything!!!

```
sudo aptitude install build-essential
```

---

### Post by nzk on 2006-08-21
EVerything I use is already compiled

---

### Post by taurus on 2006-08-21
If everything is already compiled, then just run it!!!

---

