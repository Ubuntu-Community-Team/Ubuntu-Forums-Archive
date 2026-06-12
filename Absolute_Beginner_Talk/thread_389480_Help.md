---
title: "Help"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by zeroo on 2007-03-20
**Okay Please Explain what I am supposed to do here**


Step 2

Now install ndiswrapper 1.8. I'm not sure whether the default ndiswrapper provided in the cd works. I think it should. You can give it a try. Here's the link for ndiswrapper 1.8

[http://prdownloads.sourceforge.net/n...ar.gz?download](http://prdownloads.sourceforge.net/n...ar.gz?download)

Then extract the archive files


Code:
$tar zxvf ndiswrapper-version.tar.gzGo to the directory created and type the following


Code:
$sudo make uninstall

$sudo make

$sudo make installIf you encounter problem with make command not recognised. It means that development tools are not installed properly. Pop in your cd and install

- build-essentials
- kernel headers

via synaptic. This should enable make.

Now ndiswrapper is installed



**I dont know where to type all the make uninstall and make into, can someone help?**

---

### Post by steve101101 on 2007-03-20
the terminal which is at applications>accessories>terminal in the menu system.

---

### Post by steve101101 on 2007-03-20
send me a private message if you have any other questions

---

### Post by bwingbob on 2007-03-20
What exactlly are you trying to do?

---

### Post by steve101101 on 2007-03-20
type
```

tar zxvf ndiswrapper-version.tar.gz
cd /location_of_the_folder_just_made/
sudo make uninstall
sudo make
sudo make install

```

this location may be something like this /home/steve/ndiswrapper/

---

### Post by zeroo on 2007-03-20
wow thank you. Worked perfectly.

---

### Post by steve101101 on 2007-03-20
your welcome. glad i could help.

---

