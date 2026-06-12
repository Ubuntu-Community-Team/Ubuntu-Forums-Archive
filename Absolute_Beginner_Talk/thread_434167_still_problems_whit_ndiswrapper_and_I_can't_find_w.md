---
title: "still problems whit ndiswrapper and I can't find what to do!"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2007-05-05
Can anybody help me installing the driver of my wireless card into my computer?

I read that I had to cabextract or something like that the Windows driver and install it via- ndriswrapper but I can't understand very well the guides and I don't konw how to do that.


my computer is a HP Compaq NX6325

my wireless card: Broadcom Corporation Dell Wireles 1390 WLAN Mini-PC

---

### Post by Jorge32 on 2007-05-05
why nobody answers me :( isn't this forums suposed to help?


I mean I don't lik to be writing this but... I have about 10 hours connected and only one person answered one of my posts..... and now he is disconnected!!!!!!!


I can't solve the problem, is it so difficult that someone that has solved the problem helps me?


Please!!!!!!

---

### Post by Acglaphotis on 2007-05-05
I have the same card as you do i think (i think because you wrote mini-pc and i have mini-pc**i**). If you are on feisty just do a:

```
sudo aptitude install bcm43xx-fwcutter
```

And in the installation it will ask something and then your wireless card will be set up. Oh one more thing, to manage wifi, you should install wifi-radar because i think feisty's default network manager doesnt handle well this card:

```
sudo aptitude install wifi-radar
```

Hope i helped.

-Acgla

PS:

> 
why nobody answers me isn't this forums suposed to help?


Remember, no one is paying the people who answer our questions, they do it because of the good will in their hearts, so dont expect this to be like Tech Support.

---

### Post by gigaferz on 2007-05-05
[http://ubuntuforums.org/showthread.php?t=367785](http://ubuntuforums.org/showthread.php?t=367785)

One thing you should try is to provide more information..what have you done so far?

Be more explicit.

Nobody ever answered me, but im ok, and I found a way out.

First try to update  ndiswrapper from the repositories, Go to system ,Administration, then Synaptic package manager.

Do a search for ndiswrapper, remove it completely and then install it again.

If there is an update via the update manager, get it.

if it does not work i posted a link that tells you step by step, how to get it to work.

get wifi radar to, this is like the windows wireless connection tool, 

I wish I could do all that on the command line, but I only can do things in gui.

---

### Post by Jorge32 on 2007-05-05
[QUOTE=Acglaphotis;2599896]I have the same card as you do i think (i think because you wrote mini-pc and i have mini-pc**i**). If you are on feisty just do a:

```
sudo aptitude install bcm43xx-fwcutter
```

And in the installation it will ask something and then your wireless card will be set up. Oh one more thing, to manage wifi, you should install wifi-radar because i think feisty's default network manager doesnt handle well this card:

```
sudo aptitude install wifi-radar
```

It says in both couldnt find any package whose name or description matched ... "wifi-radar" or  "bcm43xx-fcutter"

---

### Post by Acglaphotis on 2007-05-05
You'r on feisty? I just re-tried these commands and they worked (remember to use the terminal for this)

-Acgla

---

### Post by gigaferz on 2007-05-05
hey!!
copy and past for better accuracy, you have a typo

---

### Post by Jorge32 on 2007-05-05
yes, on feisty, on the terminal


It could be maybe that I am without internet ?

---

### Post by Acglaphotis on 2007-05-05
> It could be maybe that I am without internet ?

This is weird. From where are you typing this? You should hook up your ethernet/usb connection to your ubuntu machine and then run the commands.

-Acgla

---

### Post by Jorge32 on 2007-05-05
I am writing from another machine with very slow internet

---

### Post by Bachstelze on 2007-05-05
```
lspci -n | grep $(lspci | grep Network | awk '{print $1}') | awk '{print $3}'
```

and paste what you get.

---

### Post by Jorge32 on 2007-05-05
```
jorge@ubuntu:~$ lspci -n | grep $(lspci | grep Network | awk '{print $1}') | awk '{print $3}'
14e4:4311
```

---

### Post by Bachstelze on 2007-05-05
Your card is not listed on the list of cards known to work on the Ndiswrapper wiki, you'll have to find Windows drivers for it by yourself. Try to google for it and see if someone else managed to make it work.

---

### Post by MSDeath on 2007-08-25
I have the same problem. Can't connect to the internet so use a second machine. Copied in the fwcutter programme but can't get it to install.
Removed Network Manager to install Wcid which works fine. Just can't get the wireless to work at all. Followed numerous threads and typed in numerous commands. The Broadcom driver is there but.... Still working on it.
Any advice for installing fwcutter?
Cheers

---

### Post by kevdog on 2007-08-25
Try this post out:

[http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated](http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated)

---

