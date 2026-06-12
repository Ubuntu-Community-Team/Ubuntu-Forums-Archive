---
title: "Where is hal-applesmc?"
date: 2011-01-25
forum: Apple Hardware Users
---

### Post by SullivanL on 2011-01-25
I just installed Ubuntu 10.10 on my 1st generation macbook air. Everything works pretty good. But I just wanted to get the keyboard backlight to work as well. So I have googled for solutions. Then I found this page: [https://help.ubuntu.com/community/MacBookAir1-1/Intrepid?action=show&redirect=MacBook+Air](https://help.ubuntu.com/community/MacBookAir1-1/Intrepid?action=show&redirect=MacBook+Air)

Basically it says that I should install hal-applesmc from mactel support.

I followed the link and added the repository but when I try to install the package it says unable to locate the package. Anybody knows if they have change the location of the package or where can I find the package? Thanks!

---

### Post by Kirboosy on 2011-01-25
try this...

```
sudo apt-get update
```
updates your repository

```
sudo apt-get install hal-applesmc
```
installs the package


If that doesn't work it might be because the package is older and no longer supported by newer versions of Ubuntu

---

### Post by SullivanL on 2011-01-25
> **Caboose885 said:**
> try this...

```
sudo apt-get update
```
updates your repository

```
sudo apt-get install hal-applesmc
```
installs the package


If that doesn't work it might be because the package is older and no longer supported by newer versions of Ubuntu

Yup, already done that. It said unable to.locate package. But it is shown on mactel's website that there is such package exists. 
 
My solution for now is just that I have wrote a shell script called "kbl":

```

#!/bin/bash

if [[ $# -lt 1 || $# -gt 1 ]]
then
	echo ""${0}": need exactly one argument" >&2
	exit 1
elif [[ "$1" -lt "0" || "$1" -gt "255" ]]
then
	echo ""${0}": please give a value between 0 and 255" >&2
	exit 1
fi

echo "The brightness of the keyboard backlight is set to the following value succesfully."
echo $1 | sudo tee -a /sys/class/leds/smc\:\:kbd_backlight/brightness


```

put it into /usr/bin/ so that I can use this command to change the back light of the keyboard. It works but kinda weird.

It's gonna be great if somebody knows about hal-applesmc.

---

