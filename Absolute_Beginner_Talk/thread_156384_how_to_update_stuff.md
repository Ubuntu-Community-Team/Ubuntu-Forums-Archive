---
title: "how to update stuff?"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by x5452 on 2006-04-06
I was using gdesklets but cant lose the background color and it looks lame, so I went to grkellm and downloaded the new version 2.29  I somehow, (using apt-get install gkrellm  managed to install 2.2.7, one that is apparantly pre packaged with ubuntu.  How can I upgrade what i inadvertantly installed to what I downloaded?

---

### Post by taurus on 2006-04-06
If you want to install an app from source, you need to remove the previous version with apt-get as
```

sudo apt-get remove gkrellm

```
Then, unpack, configure, build, and install the latest version.  BUT before you plan to build it, you first need to install build-essential or else it will fail right away...
```

sudo apt-get install build-essential

```

---

### Post by x5452 on 2006-04-06
crap ya lost me, i unpacked it, icon sittin on desktop right, how to i build and configure? are those terminal things to be done?  can i still apt-get remove the old version i installed?

---

### Post by joshrobinson on 2006-04-06
[QUOTE=x5452]crap ya lost me, i unpacked it, icon sittin on desktop right, how to i build and configure? are those terminal things to be done?  can i still apt-get remove the old version i installed?[/QUOTE]

go into the folder with a terminal, apt-get remove the package as said above

do the apt-get build-essential as said above as root

once thats installed do ./configure && make && make install
to install the new source code

---

### Post by taurus on 2006-04-06
I assume you download it to Desktop, right!  Then, open a terminal by clicking Applications -> Accessories -> Terminal.  Now type
```

cd ~/Desktop
sudo apt-get remove gkrellm
sudo apt-get install build-essential
tar xvzf gkrellm-2.29.tar.gz (or whatever the exact name is...)
cd gkrellm-2.29 (or whatever the exact name is...)

```
Now, read both README and INSTALL to see if it requires something special to install it but chances are you would do the following to install it...
```

more README <-- to read it
more INSTALL <-- to read it
./configure <-- to configure it
make <-- to build it
sudo make checkinstall <-- to install it as an deb so you can remove it with apt-get later if you wish...

```

---

