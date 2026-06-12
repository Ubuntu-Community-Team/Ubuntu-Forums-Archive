---
title: "[SOLVED] Firefox 3 Beta 2"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by S3loth on 2007-12-21
I'm trying to install the Beta 2 of Firefox 3. I downloaded firefox-3.0b2.tar.bz2, and extracted it to my desktop. I don't know what to do after this. There is no readme that came with it.

---

### Post by spiderbatdad on 2007-12-21
```
cd Desktop
```
```
tar -xjvf name.of.package
```
just start the name and use the tab key to auto complete the name for you.

```
cd new.directory
```after untarring a new directory of the same name should be on your desktop. Again just start the name and use tab key.```
./configure
make
sudo make install
```

---

### Post by skymera on 2007-12-21
i dont remember clearly.

but i sdont think you need to install that.

is there a Firefox fiel you xcan just double click?

i dont recoomend installing FF3, nearly no add ons work and no themes.
and it over writes your rpevious FF2 install

---

### Post by Vadi on 2007-12-21
Do not install! This is just a beta, not a stable/working version.

After you extracted the folder, go into it, make sure you shut down all firefox windows, and then start either firebox-bin or the firefox file from the folder.

---

### Post by Moop on 2007-12-21
I used this guide and just changed the version from 3.0b1 to 3.0b2. 

[http://phorolinux.com/installing-firefox-30-beta-1-on-ubuntu-710-gutsy-gibbon.html]("http://phorolinux.com/installing-firefox-30-beta-1-on-ubuntu-710-gutsy-gibbon.html")

---

### Post by shifty2 on 2007-12-21
Close any firefox windows that you may have running then:
change to the directory where the file is located (desktop in my case)
```
cd ~/Desktop
```
extract the file to your "opt" directory:
```
sudo tar jxvf firefox-3.0b2.tar.bz2 -C /opt/
```
change owner and access permissions:
```
sudo chown -R root:root /opt/firefox/
sudo chmod -R 755 /opt/firefox/
```
open firefox et voila!

---

### Post by S3loth on 2007-12-21
Okay, I got it working. When I tried to run it from the folder, it was Firefox 2 because I had that one open, but with it closed it runs Firefox 3.

---

### Post by Old Pink on 2007-12-23
This should be of some help: 

[http://www.topicalmatt.com/23-12-2007/firefox-3-beta-2-in-ubuntu-710](http://www.topicalmatt.com/23-12-2007/firefox-3-beta-2-in-ubuntu-710)

:)

---

