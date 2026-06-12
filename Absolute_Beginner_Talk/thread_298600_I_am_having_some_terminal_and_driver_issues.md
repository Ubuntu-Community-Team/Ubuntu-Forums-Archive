---
title: "I am having some terminal and driver issues"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by LEDZO on 2006-11-13
First of all, I am running wharty, I know it's obsolete,but i have dapper on the way.

Now, I have never had windows installed on this machine so i'm not sure if it's a Mobo problem. My usb doesn't work and neither does my sound plugs. My mouse and keyboard do though.

Also I am having trouble with the terminal. Even when i follow step by step instructions, i still can't do anything like take for example
./configure
make 
make install

when i out in ./configure
it gives me an error. I know i'm not messing up entering them but i can't think of anything else like i can't cd something on the desktop.It says it's not there even when i'm looking at the icon.

Note* My usb mouse lights up but doesn't do anything.

---

### Post by johnnymac on 2006-11-13
May help to post the error you get and the contents of /var/log/messages

---

### Post by LEDZO on 2006-11-13
./congigure
no such file or directory


cd /home/chris/cmpci-4.03.tar.gz
no such file or directory


Those are two different ones i had tried


And should ubuntu need something special installed for usb and sound on the MoBo?

---

### Post by bodhi.zazen on 2006-11-13
> **LEDZO said:**
> ./congigure
no such file or directory

Typo. Should be /.configure. You need to extract from the archive first.


> cd /home/chris/cmpci-4.03.tar.gz
no such file or directory

[list=number][*]Where did you download cmpci-4.03.tar.gz to? /home/chris/**Desktop**/cmpci-4.03.tar.gz perhpas?

[*]You need to extract first, then cd into cmpci-4.03
```
cd Desktop  ... Or wherever cmpci-4.03.tar.gz is located
tar xzf cmpci-4.03.tar.gz
```

[*]Now you likely need to install build-essentials. If that package does not exist, you will need to install make and gcc to start.

[*]Now you can```
cd cmpci-4.03 ..Or whatever the extracted directory is called.
/.configure
make
sudo make install
```[/list]

---

### Post by LEDZO on 2006-11-13
when i put in,


```
cd /desktop
no such file or directory

```

I can't get to the desktop.

I tried variants of cd /desktop like cd desktop and cd -desktop

I can't get on the internet with it yet because my usb wont work

---

### Post by bodhi.zazen on 2006-11-13
> **LEDZO said:**
> when i put in,


```
cd /desktop
no such file or directory

```

I can't get to the desktop.

I tried variants of cd /desktop like cd desktop and cd -desktop

I can't get on the internet with it yet because my usb wont work

Linux is **case sensative**. :lol:

All I am asking is where did you download cmpci-4.03.tar.gz ?

If you know, cd to that directory and then proceed with the "tar  xzf cmpci-4.03.tar.gz" .... If not, it is likely on your desktop.

The full path is /home/chris/Desktop, ~/Desktop for shorthand.

If you are already in your home directory you can "cd Desktop", otherwise "cd ~/Desktop" will do.

Watch that "D". in "D"esktop.

---

### Post by CatKiller on 2006-11-13
> **bodhi.zazen said:**
> Typo. Should be /.configure. 

Typo. Should be ./configure :)

---

### Post by b_martinez on 2006-11-13
> **CatKiller said:**
> Typo. Should be ./configure :)

CatKiller is correct. 
the ./ tells the system to stay in the current directory.

LEDZO, do you have the 'build-essential' package installed? You may need other -dev or -devel packages also, but I'm not sure about that.
Bill

---

### Post by LEDZO on 2006-11-13
Is build-essential in the packages or do i have to download it from the internet. 

I can't get on the internet with it.

cmpci is off a cd that i dragged onto the desktop

---

### Post by CatKiller on 2006-11-13
Build-essential should be on the cd you installed Ubuntu with.

---

### Post by LEDZO on 2006-11-13
Ya, i had build-essential installed.

How do i find these dev files

---

