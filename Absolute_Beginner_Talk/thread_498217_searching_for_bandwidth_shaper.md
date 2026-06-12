---
title: "searching for bandwidth shaper"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by snake444 on 2007-07-11
i need an app that is bandwidth shaper like NetLimiter in windows
because programs using alot of bandwidth and i cant surf in firefox
i need to limit the upload
and i didnt found in the 'add\remove programs' any bandwidth shaper
so can you give me link for one and how-to install it?

---

### Post by ~~Tito~~ on 2007-07-11
Windows uses more bandwidth on its own (20%) plus yours, Linux doesn't use any (I think) untill you use the updater or add one using the one under applications. I don't know how much you download so just limit downloading. I personally don't know of any but try using that program with wine.

---

### Post by vineethbs on 2007-07-11
hi snake444,

check out these programs

[http://www.freenet.org.nz/python/pyshaper/](http://www.freenet.org.nz/python/pyshaper/)
[http://monkey.org/~marius/pages/?page=trickle](http://monkey.org/~marius/pages/?page=trickle)

[note : searching started out from freshmeat, you can also try :)

as for pyshaper, its available as a gzipped tar archive, (not as a deb file)
download that from the link given (1)

tar jxf pyshaper-0.1.3.tar.gz // I have downloaded this version for illustration

read INSTALL

python would be most probably installed, if not
sudo apt-get install python

iproute can be installed in the same way as 
sudo apt-get install iproute

(if you read the INSTALL, you will find that the kernel needs to have certain options configured)
also, you need to install Tk for the GUI

after this, you would probably want to install pyshaper by
// change into the pyshaper directory

python setup.py install

---

