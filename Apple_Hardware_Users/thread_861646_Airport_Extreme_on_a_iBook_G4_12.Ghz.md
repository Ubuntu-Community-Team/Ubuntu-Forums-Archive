---
title: "Airport Extreme on a iBook G4 12.Ghz"
date: 2008-07-16
forum: Apple Hardware Users
---

### Post by lukerz8 on 2008-07-16
I have been trying to get the wireless to work on this iBook with very little luck (feisty distro). the seemingly best source for getting this card to work that i have found has been [this post]("http://ubuntuforums.org/showthread.php?t=142727").

i have seen this code elsewhere, also, all refering to the same svn site.


```
svn checkout svn://svn.berlios.de/bcm43xx/trunk/fwcutter
cd fwcutter
make
wget [http://www.ghostcorp.net/AppleAirPort2](http://www.ghostcorp.net/AppleAirPort2)
./bcm43xx-fwcutter AppleAirPort2
sudo make installfw
```


first of all, i dont really know what an svn is, but i assume it is simular to an ftp? anyway, terminal says it doesnt exist. this is the output:

```
svn checkout svn://svn.berlios.de/bcm43xx/trunk/fwcutter
svn: URL 'svn://svn.berlios.de/bcm43xx/trunk/fwcutter' doesn't exist
```

is there another source that i could get whatever this is from? or better yet, an easier-ish way to install this stupid wireless card. any help would be much appreciated.

---

### Post by pxwpxw on 2008-07-17
There is an attachment at the foot of this post
[http://ubuntuforums.org/showpost.php?p=3461818&postcount=88](http://ubuntuforums.org/showpost.php?p=3461818&postcount=88)

should do the job for a BCM4306 airport express on ppc ibookg4.

It is a .deb package, just install with
```

sudo dpkg -i bcm43xx_compwiz18.1-all.deb

```
(check the name is correct)

---

