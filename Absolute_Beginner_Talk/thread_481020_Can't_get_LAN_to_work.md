---
title: "Can't get LAN to work"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by pandorazboxx on 2007-06-22
hey,

I was trying to get my wireless to work using ndiswrapper, then i finally was able to install the driver, but network manager didn't even recognize that i had a wireless signal. So i figured i would reinstall network manager. So i removed it in the add/remove applications tool. unfortunately, it will not let me add the program back i get the following error:

> Network Manager cannot be installed on your computer type(i386)

Either the application requires special hardware features or the vendor decided not to support your computer type.

It won't let me install anything else either i get the same type of error message. So i decided to plug in the LAN line and download all the updates in add/remove applications to see if that would let me do it. But it's not even recognizing that i'm plugged in. 

I'm guessing that i need network manager to let me get on the internet, but i need the internet to install network manager :( ....

i tried to find the newest version of network manager to install but i'm very confused because i went to their website and they have a very large amount of files in their ftp and they don't say which one is the right one to use or how to install it

any help is appreciated...

---

### Post by pandorazboxx on 2007-06-22
should i just totally reinstall ubuntu because it was up there when i first installed it. 

and if i should, how do i go about doing that??

---

### Post by gcos7 on 2007-06-22
First, I would reboot just to get things back at a clean state.  Then I would see if the Synaptic Package Manager works - if so, look for network-manager-gnome.  I use it.    By the way, I have found that if I mistype any portion of the load command for ndiswrapper to install my driver, it will say the driver is installed but it actually isn't.  I would also try removing your driver from ndiswrapper via sudo ndiswrapper -e xxxxxx  where xxxxxx is your driver name that shows when you do a ndiswrapper -l (that's a lower case "L").  Then reload your driver, double checking all of your spelling and all of the path before you press return/enter.

This entire process can get very frustrating - just check the topic in the forum we are using.  If things don't work, please reply and people will see if they can help you.;)

---

### Post by pandorazboxx on 2007-06-22
how do i uninstall ubuntu??

---

### Post by oilchangeguy on 2007-06-22
> **pandorazboxx said:**
> hey,

I was trying to get my wireless to work using ndiswrapper, then i finally was able to install the driver, but network manager didn't even recognize that i had a wireless signal. So i figured i would reinstall network manager. So i removed it in the add/remove applications tool. unfortunately, it will not let me add the program back i get the following error:



It won't let me install anything else either i get the same type of error message. So i decided to plug in the LAN line and download all the updates in add/remove applications to see if that would let me do it. But it's not even recognizing that i'm plugged in. 

I'm guessing that i need network manager to let me get on the internet, but i need the internet to install network manager :( ....

i tried to find the newest version of network manager to install but i'm very confused because i went to their website and they have a very large amount of files in their ftp and they don't say which one is the right one to use or how to install it

any help is appreciated...


i'd suggest doing a complete reinstall of ubuntu. and then don't remove vital system packages.
it's things like this that make people complain that windows sucks, or ubuntu sucks, or whatever os you're using. don't screw with it, if you don't know what you're doing.

---

### Post by r4ik on 2007-06-22
> **pandorazboxx said:**
> how do i uninstall ubuntu??


[http://ubuntuforums.org/showthread.php?t=480342&highlight=uninstall+ubuntu](http://ubuntuforums.org/showthread.php?t=480342&highlight=uninstall+ubuntu)

Try Taurus option.

Good luck !

---

### Post by pandorazboxx on 2007-06-22
> **oilchangeguy said:**
> i'd suggest doing a complete reinstall of ubuntu. and then don't remove vital system packages.
it's things like this that make people complain that windows sucks, or ubuntu sucks, or whatever os you're using. don't screw with it, if you don't know what you're doing.

thats a little harsh for this being an "absolute beginners" forum. i messed up and i'm trying to fix it. i'm not bashing anyone's OS. i like ubuntu and i just want to get it to work. sometimes this is more complicated for some people than others. But i'll try not to remove any vital system packages this time :D

thanks r4ik

---

### Post by gigaferz on 2007-06-27
it might be too late,but you could add your livecd as source for software.

sudo apt-cdrom add

sudo apt-get update

then try installing the program you need

if it was when you installed ubuntu,it should be there

---

