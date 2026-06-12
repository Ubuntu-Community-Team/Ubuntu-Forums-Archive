---
title: "Hello"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by o-q on 2006-10-25
Hello everyone:) 
I currently run a Sony Vaio PCG-K115M laptop.
I have just installed Ubuntu, all went nice and smooth:D .
The winmodem dosn't have any drivers, well wasn't expecting any to be honest!
But I would like to connect to the net whilst using Ubuntu for updates and to load up a few new programmes. 

I'm a comand line / Linux virgin, what is my best bet to get my adsl up and working. I will do my utmost to try and supply any info to those willing to help!

---

### Post by nickpaton on 2006-10-25
Hi O-Q and welcome to the forums and the World of Ubuntu.

From your post you want to simply connect via ADSL; is this wirelessly or using a cable from the laptop to the router?

If it's a cable, is this a USB cable or a LAN Ethernet cable?

If you are using a LAN cable, then it should work straight away.  Try plugging the cable in, and reboot the laptop and router and see if you can then access the Internet.

Get back to us with your results and answers to my questions.

---

### Post by Bachstelze on 2006-10-25
Hi and welcome to Ubuntu ?

USB or Ethernet modem ? Do you have a router ?

---

### Post by nickpaton on 2006-10-25
O-Q - to save a bit of time, since we may well need to know this, can you send me the outputs of the following commands.

To do this open a Terminal - Applications>Accessories>Terminal

To idenfify all Ethernet ports type

```
ifconfig
```

Copy the result into your reply between Quotes (picked from the choices above the message window).

To identify all components in the laptop type

```
lspci
``` (where first letter is lower case L)

and post the results

If you want to connect wirelessly so as we can identify the wireless chip, please post the results of

```
iwconfig
```

Saves asking the questions in later posts

Good luck and get back if you don't understand what we're asking.

*[SIZE="1"]Modified for spelling and correction thanks Po0f[/SIZE]*

---

### Post by po0f on 2006-10-25
> **nickpaton said:**
> To identify all components in the laptop type

```
lspce
``` (where first letter is lower case L)

and post the results

The above command should be **lspci**.

---

