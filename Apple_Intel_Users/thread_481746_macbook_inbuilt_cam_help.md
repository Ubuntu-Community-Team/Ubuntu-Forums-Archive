---
title: "macbook inbuilt cam help"
date: 2007-06-22
forum: Apple Intel Users
---

### Post by dragonwings on 2007-06-22
does anyone know how to get cam on my macbook to work drivers/programe to use built in cam

the only o.s on this laptop is ubuntu at moment

---

### Post by ivesjd on 2007-06-22
There are quite a few threads on this already, just do a search for iSight and it should come up.

---

### Post by dragonwings on 2007-06-23
still no luck can anyone confirm that isight cam will work on my  !! ubuntu  only macbook  !!

---

### Post by ivesjd on 2007-06-23
Okay, did you try using the search tool? When I did it The third (behind this thread and one other unrealted) was this [http://ubuntuforums.org/showthread.php?t=225621&highlight=iSight](http://ubuntuforums.org/showthread.php?t=225621&highlight=iSight)
which is what I used to get mine working.

---

### Post by xerosis on 2007-06-24
I think the point they were trying to make was that you need the mac drivers for that howto, and like myself we don't have access to them.

---

### Post by ivesjd on 2007-06-24
You dont need them, if you read the first part, there is a newer way to do it and it works without getting the mac drivers. I know because I did it.

---

### Post by dragonwings on 2007-06-25
ok that sounds good ill keep trying

---

### Post by ivesjd on 2007-06-25
```
New Quick Install:
* uvcvideo is now prebuilt in Feisty. Problem is that it doesn't work with iSight. https://bugs.launchpad.net/ubuntu/+s...20/+bug/105638
Hopefully this will change with a future kernel update and this guide will become mute. For now, we will disable it and build our own module.
$ sudo modprobe -r uvcvideo
$ sudo mv /lib/modules/$(uname -r)/kernel/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules/$(uname -r)/kernel/ubuntu/media/usbvideo/uvcvideo.ko.original

* Install prerequisites, libusb-dev, you might need kernel headers that match your kernel ( I already had them )
$ sudo apt-get install libusb-0.1-4 libusb-dev linux-headers-$(uname -r)

* Download the new all-in-one bundle, with firmware autoloader as provided by Ivan N. Zlatev ( see http://i-nz.net/projects/linux-kernel/ )
$ wget http://files.i-nz.net/projects/linux...-isight.tar.gz
$ tar -xzvf uvcvideo-isight.tar.gz

* Build and Install the uvcvideo module
$ cd against-revision-100
$ sudo make
$ sudo make install

* Load the module
$ sudo modprobe uvcvideo
```
There are the instructions that I used. They worked for me.

---

