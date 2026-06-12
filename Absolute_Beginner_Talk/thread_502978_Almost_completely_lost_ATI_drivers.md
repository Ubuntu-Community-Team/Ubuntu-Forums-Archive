---
title: "Almost completely lost: ATI drivers"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by Dysan on 2007-07-17
I've been following the guide [[COLOR="blue"]here[/color]](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide), but get stuck at the first part.

Method 1 tells me to do:
```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) # (Okay if it is already installed)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
```
I do it, but nothing happens after ```
sudo depmod -a
```It just idles for a second, and then drops down to another line, ready for another input. Is that supposed to happen?

I'm following method 2 now, and it tells me to "[color=red]make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list[/color]" Ok... What? How do I get there? I'm thinking that I've already done that part when I did the whole "Disable Composite Extension" thing.

Am I on the right track? Is it alright for me to continue on with method 2?

Thanks in advance.

---

### Post by Dysan on 2007-07-17
Also, when I try to run the ATI driver installer from the desktop, I get this: [img]http://img361.imageshack.us/img361/3047/problemew4.jpg[/img]

Again, thanks.

---

### Post by bren on 2007-07-17
to check universe and multiverse do the following command in a terminal 
> 
sudo gedit /etc/apt/sources.list
now search the file for the lines with **feisty universe** and **feisty multiverse**

**there should be no # at the start of the line**

if there is a # then delete the # and save the file

i don't know about the method / wiki you are on but keep going :)

bren

---

### Post by jvc26 on 2007-07-17
To run the installer you'd have to right click the file, go to permissions and allow executing the file as a program - otherwise you're just trying to open it as a file.

My advice would be to follow one of the guides from the community documentation:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) (for fglrx)
or
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) (for the open source driver)

Il

---

### Post by Dysan on 2007-07-17
> **bren said:**
> to check universe and multiverse do the following command in a terminal 

now search the file for the lines with **feisty universe** and **feisty multiverse**

**there should be no # at the start of the line**

if there is a # then delete the # and save the file

i don't know about the method / wiki you are on but keep going :)

bren
There are no #s in front of any of those lines, but I have ran into another problem.

> ***Create .deb packages:***```
sudo bash ati-driver-installer-8.38.7*.run --buildpkg Ubuntu/feisty
```
This line here returns "ati-driver-installer-8.38.7*.run: No such file or directory".
Here, I thought it was because the filenames were different. I changed it, hit enter, and recieved the same error.

? :/

---

### Post by Dysan on 2007-07-17
Awesome! Well, right-click the file and doing all that has gotten it up and running, but I still can't continue and install the .deb packages.

---

### Post by Majorix on 2007-07-17
That line should read:

```
sudo bash ati-driver-installer-8.38.6-x86.x86_64.run --buildpkg Ubuntu/feisty
```

I am not sure if placing an asterisk(*) would work. Therefore I typed in the full name.

Reply back if any error occurs.

---

### Post by Dysan on 2007-07-17
> **Majorix said:**
> That line should read:

```
sudo bash ati-driver-installer-8.38.6-x86.x86_64.run --buildpkg Ubuntu/feisty
```

I am not sure if placing an asterisk(*) would work. Therefore I typed in the full name.

Reply back if any error occurs.

Same error. :/

If it means anything, GTA2 runs really slowly on Wine. It also doesn't have sound.

---

### Post by stchman on 2007-07-17
> **Dysan said:**
> I've been following the guide [[COLOR="blue"]here[/color]](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide), but get stuck at the first part.

Method 1 tells me to do:
```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) # (Okay if it is already installed)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
```
I do it, but nothing happens after ```
sudo depmod -a
```It just idles for a second, and then drops down to another line, ready for another input. Is that supposed to happen?

I'm following method 2 now, and it tells me to "[color=red]make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list[/color]" Ok... What? How do I get there? I'm thinking that I've already done that part when I did the whole "Disable Composite Extension" thing.

Am I on the right track? Is it alright for me to continue on with method 2?

Thanks in advance.

If you are running Feisty then just enable the restricted drivers.  They work.

---

### Post by Dysan on 2007-07-23
> **stchman said:**
> If you are running Feisty then just enable the restricted drivers.  They work.

I think I've enable them, but they seem to only half-work. What else do I need to do before I can play games?

---

### Post by Dysan on 2007-07-29
Bump.

---

