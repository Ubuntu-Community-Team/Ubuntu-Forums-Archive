---
title: "trouble installing p2p"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by jpates20 on 2008-02-20
i try to run the set up, and it keeps saying dependency not satisfied python-cairo witch in install already. could some halp? thanks.....john

---

### Post by ghanthar on 2008-02-20
Can you please give more info... about what program more specifically what package are we talking about. And what do you mean by "running the setup"? do you mean apt-get or is this a program with custom setup utility?

---

### Post by jpates20 on 2008-02-20
> **jpates20 said:**
> i try to run the set up, and it keeps saying dependency not satisfied python-cairo witch i install already. could use some halp? thanks.....john


gnome -bt downled 0.032-1 all.deb/ packege installer

---

### Post by ghanthar on 2008-02-20
An earlier version of **gnome-btdownload** (0.028-1) package is preinstalled with Ubuntu Gutsy. So the** python-cairo **(1.4.0-2) package is also installed.
But the version that you are trying to install  is higher (0.032-1) than the pre installed one and this package probably requires a higher version of **python-cairo** which is not present on the repositories.This is why you are getting error messages.
Installing this required version of **python-cairo** will be extremely difficult because you have to figure out and manually manage all the dependencies and you should probably install it from source code.Even if you succeed this has a great chance to will broke your system so unless you know exactly what you are doing don't do this.
Also, I do not think that **gnome-btdownload** upgrade will give you new features.In fact **gnome-btdownload**  is just designed to pop up when a torrent file is opened.(look at [http://gnome-bt.sourceforge.net/ ]("http://gnome-bt.sourceforge.net/")
for more info) 

 If you want a more advanced Torrent client like  uTorrent , take a look at **_[deluge]("http://deluge-torrent.org/")_**. To install just open a terminal and type 
```
sudo apt-get deluge-torrent
```or if you want a simplier one you can use _[COLOR=Red][**transmission**]("http://www.transmissionbt.com/")[/COLOR]_ which is the pre installed client for Ubuntu 8.04.
```
sudo apt-get transmission
```

---

### Post by jpates20 on 2008-02-20
i'm using ubuntu 6.06 LTS , what the best one to use.....thanks

---

### Post by ghanthar on 2008-02-21
If you want a feature rich client you can use **azureus** with dapper. You have also **bittorrent**,** bittornado **and** gnome-btdownload**in the official repositories but azureus is better if you do not intend to use a lighter client.
for **azureus** just
```
sudo apt-get install azureus
```
for** bittorrent ** 
```
sudo apt-get install bittorrent-gui
```
and for** bit tornado **
```
sudo apt-get install bittornado-gui
```

I'm not sure but think that **bittorrent**,**bittornado** and **gnome-btdownload** are similar in terms of functionality.

---

### Post by hyper_ch on 2008-02-21
and you can also use rTorrent - which is cli based

```

sudo apt-get install rtorrent

```

---

