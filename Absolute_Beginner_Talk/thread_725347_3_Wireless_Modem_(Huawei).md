---
title: "3 Wireless Modem (Huawei)"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by DylanD on 2008-03-15
I have no network available under my linux setup.

How do I install (via Windows) the driver/app needed to get my Huawei wireless modem working so that I can get internet access in linux.

Many thanks in advance for your help.

Dylan

---

### Post by dstew on 2008-03-15
What Huawei product do you have, exactly? (Model number).

---

### Post by DylanD on 2008-03-19
Hi,

It's the Huawei E220 HSDPA USB Modem provided by 3.

I've searched these and other forums but everything I try within Ubuntu doesn't seem to work. It refuses to recognise it as a USB modem (just a storage device that it can not mount).

Thanks

Dylan

---

### Post by gn2 on 2008-03-19
I believe that these modems work with the standard OS on the Asus Eee, which is Xandros.

Maybe a switch of distro would be worth a try?

---

### Post by Circus-Killer on 2008-03-19
the device should work out of the box.
however, to make use of the device you will need something like the [Vodafone Mobile Connect driver for Linux]("http://www.vodafonebetavine.net/web/linux_drivers"). however, to install that you will need to fetch its dependencies.

first step:
```
sudo dpkg -i vodafone.deb
```

then:
```
sudo apt-get install -f --print-uris > ~/Desktop/files.txt
```

then go to files.txt on your dekstop and view it. there you will see a list of all the dependencies you need to download manually. once you have downloaded all the dependencies, you can simply install the dependencies using dpkg, followed by the installation of the vodafone software.

this should hopefully give you some good starting advice, however it will take a little bit of playing around to get it right. for more info check out [http://ubuntuforums.org/showthread.php?t=687243]("http://ubuntuforums.org/showthread.php?t=687243").

---

