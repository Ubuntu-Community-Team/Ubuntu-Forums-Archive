---
title: "No Desktop since upgrade"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by jdway on 2007-02-24
I recently upgraded to Dapper from Breezy using apt-get. When I restarted my computer it took me to a terminal prompt. I tried startx and that did not work. I also tried to upgrade xserver but it cannot be installed due to dependency problems. It cannot install the x11-common and lbc something dependencies. When I ran sudo apt-get dist upgrade in the terminal prompt it said that some packages (including xserver and xinit) were held back. Can anyone help me with this?

---

### Post by shareMenaPeace on 2007-02-24
Maybe try 

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by jdway on 2007-02-24
I tried that but unfortunately it still does not work.

---

### Post by aysiu on 2007-02-24
Can you try this and see if it makes a difference? ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.original
wget -c http://psychocats.net/ubuntu/dapper.list
sudo mv dapper.list /etc/apt/sources.list
sudo chown root:root /etc/apt/sources.list
sudo aptitude update
sudo aptitude dist-upgrade
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```

---

### Post by jdway on 2007-02-24
Here is my sources list

deb cdrom:[Ubuntu 6.06.1_Dapper Drake_-Release i386 (20060806.1)]/dapper main restricted

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe

Also, when I after I log in it gives me the following errors

configuration error - unkown item 'QUOTES_ENUB' Contact Admin
configuration error - unkown item 'NOLOGIN_STR' Contact Admin
configuration error - unkown item 'ENV_HZ' Contact Admin
configuration error - unkown item 'CHFN_AVTH' Contact Admin
configuration error - unkown item 'CLOSE_SESSION' Contact Admin

I also tried sudo mv /etc/apt/sources.list/etc/apt/sources.lit.original
and it gave me an error. Something about mv not being used correctly.

---

### Post by aysiu on 2007-02-24
> **jdway said:**
> 
I also tried sudo mv /etc/apt/sources.list/etc/apt/sources.lit.original
and it gave me an error. Something about mv not being used correctly. You're missing a space.

What you typed: ```
sudo mv /etc/apt/sources.list/etc/apt/sources.lit.original
``` What I typed ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.original
``` See the difference?

---

### Post by jdway on 2007-02-24
Yes I see the difference I will reboot now and try it out thanks.

---

### Post by aysiu on 2007-02-24
Ordinarily, if you had a graphical user interface (GUI), I'd say just copy and paste the commands instead of retyping them.

But since you are retyping them, be extra careful to type them exactly as you see them--spaces where you see spaces, slashes where you see slashes. This doesn't really apply so much to this scenario, but also keep in mind that the terminal is case-sensitive.

---

### Post by jdway on 2007-02-24
Ok. So I followed the instructions you gave me and I upgraded to Dapper. Unfortunately when I tried to load it I still go back to terminal screen. I still get the errors I mentioned earlier when I log in as well. When I start my computer it gives me the option to boot breezy dapper and windows but neither breezy or dapper will load the desktop.

---

### Post by jdway on 2007-02-24
Now htat I have done everything I can run xserver but there is a slight problem. It boots straight to the terminal and when I run startx I only get a grey background. In this background there is a blue window titled mtw that contains a 3x3 grid of white squares.

---

