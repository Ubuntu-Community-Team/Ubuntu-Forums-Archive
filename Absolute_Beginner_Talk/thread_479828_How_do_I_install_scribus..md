---
title: "How do I install scribus."
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by clipse on 2007-06-20
I have the file 'Scribus.Aqua-1.3.3.7.rc1.tar.bz2' downloaded but I don't know what to do from here. 


Thanks, 

clipse

---

### Post by clipse on 2007-06-20
Edit.....oops a tar file is a compressed file. I'm untarring it now. I'll see if there is instructions. Sorry for the inconvinience.

---

### Post by Golyadkin on 2007-06-20
Start with opening a terminal through the "Applications" menu at the top and issue these commands:
> 
cd <directoryYouPutTheFileIn>
bunzip2 Scribus.Aqua-1.3.3.7.rc1.tar.bz2
tar -xvf Scribus.Aqua-1.3.3.7.rc1.tar
cd <directoryJustCreated>

Then read the README or INSTALL file. 
> 
less README or INSTALL


---

### Post by Golyadkin on 2007-06-20
Aww :) I already typed it all :) hehe, doesn't matter, good luck!

---

### Post by Golyadkin on 2007-06-20
You could also have done it all in one command btw:
> 
sudo apt-get install scribus


---

### Post by wormser on 2007-06-20
It is better if you install from the repositories.  There is thousands of different software in them.

```
sudo apt-get install scribus
```

You can also use the gui method - System> Administration> Synaptic Package Manager.  Then just search for what you want.

---

### Post by christhemonkey on 2007-06-20
You can just type:
```
sudo apt-get install scribus 
```


Or open up synaptic package manager from "System > Administration >  Synaptic Package Manager" then you can choose one of many many pieces of software to install.

---

### Post by Golyadkin on 2007-06-20
Three times is a charm :lolflag:

---

### Post by clipse on 2007-06-20
Ha, you guys are awesome. :D thanks.

---

