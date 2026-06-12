---
title: "Broadcom BCM94306MP wireless help!"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by campbuds on 2007-10-08
I have a broadcom wireless card BCM94306MP in my Presario 2500 laptop (using a MB from a HP ZE5185)

Ubunutu is saying it is sending a receiving packets, and has a IP address but I cannot get on the internet. What do I need to do?

---

### Post by jfinkels on 2007-10-09
> **campbuds said:**
> I have a broadcom wireless card BCM94306MP in my Presario 2500 laptop (using a MB from a HP ZE5185)

Ubunutu is saying it is sending a receiving packets, and has a IP address but I cannot get on the internet. What do I need to do?

Can you ping google.com? Type the following in the terminal: ```
ping google.com
```

Have you installed the bcm43xx drivers?

---

### Post by campbuds on 2007-10-09
I have not tried pinging google, just tried going to the web site.

I have not installed any drivers. I saw the install directions for the 43xx but realized mine was a different one and didn't want to mess anything up. Those directions are a bit over my head also.

---

### Post by jfinkels on 2007-10-09
> **campbuds said:**
> I have not tried pinging google, just tried going to the web site.

I have not installed any drivers. I saw the install directions for the 43xx but realized mine was a different one and didn't want to mess anything up. Those directions are a bit over my head also.

Post the output of the command:```
ping google.com
```

Post the output of this command:```
ifconfig -a
```

Post the output of this command:```
iwconfig
```

Have you looked at this thread: [http://ubuntuforums.org/showthread.php?t=185174&highlight=BCM](http://ubuntuforums.org/showthread.php?t=185174&highlight=BCM)

You may have to install the program 'ndiswrapper', and then use that to install the Windows drivers for your card. Do you have a disk with drivers? If not, you will have to find the drivers for your card on the internet (maybe at the website for your Compaq Presario).

---

### Post by campbuds on 2007-10-16
ok, i had a friend look at it who knows what he is doing.

he said that the wireless card is recognized and I am in a local loop. He said I needed to connect to the net with a wire so I can download packets. what next? what packets is he referring to?

Also will the newer release 7.something help me?

---

### Post by jfinkels on 2007-10-16
> **campbuds said:**
> ok, i had a friend look at it who knows what he is doing.Hahaha, are you implying that I don't know what I'm doing over here? :D
> 
he said that the wireless card is recognized and I am in a local loop. He said I needed to connect to the net with a wire so I can download packets. what next? what packets is he referring to?

He probably said something like, "Use an ethernet cable to connect your computer to a wired network connection which will give you access to the internet. Then, you will be able to download packages from Ubuntu's repositories."
> 
Also will the newer release 7.something help me?

Perhaps, but probably not (Ubuntu 7.10 Gutsy Gibbon comes out on October 18 ). Have you read my previous post? I may be able to offer some insight if I can get some more information from you!

---

### Post by campbuds on 2007-10-16
ok, then i have a question. do i do this while I am plugged into the internet or while the wirless is working?

PS. i know more than it sounds like, I am just too lazy to type out a dumb description of a network cable and a ethernet port.

---

### Post by jfinkels on 2007-10-16
Make sure your wireless ethernet connection is unplugged, then try to connect using the wireless network card. After that, type the following commands in the terminal:```
ping google.com
``` (you may have to manually interrupt this one if you get no output by pressing <Ctrl>+<C>) ```
ifconfig -a
``````
iwconfig
``` and post the output here.

Again, have you looked at this thread? [http://ubuntuforums.org/showthread.php?t=185174&highlight=BCM](http://ubuntuforums.org/showthread.php?t=185174&highlight=BCM) 

Also again, you may have to install ndiswrapper and the Windows driver if you can't get the wireless network card to work.

---

### Post by runemaste644 on 2007-10-20
This will do everything for you: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

