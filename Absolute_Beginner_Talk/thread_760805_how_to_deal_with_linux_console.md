---
title: "how to deal with linux console"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by ezikiel on 2008-04-20
I'm new to ubuntu and to linux,
:confused:

 so I wonder if anyone can help me in dealing with the install of an wi fi hardware, ra link rt 2500, 
I was following the steps suggested on an internet site and i had to stop when I was asked to ener as root..
I wrote "su+enter" but i need the root password, and I don't know how to purchase it
thanks for your patience

---

### Post by tvtech on 2008-04-20
you should be able to open a root terminal if your in 7.10  

**Applications>System Tools>Root Terminal**  enter your user password and this will give you a terminal with root privledges for the temporary time you need to use them to install this device.

---

### Post by SunnyRabbiera on 2008-04-20
in ubuntu the command is sudo in a terminal, as root is disabled by default.
sudo works like a root user though so its essentially the same.

---

### Post by Delkster on 2008-04-20
> I wrote "su+enter" but i need the root password, and I don't know how to purchase it

Could you provide a direct link to those instructions, so we could take a look and perhaps tell you how to adapt them for Ubuntu?

Also, which version of Ubuntu are you using? If you don't know, try going to "System > About Ubuntu".

---

### Post by Wilfred on 2008-04-20
Although it will be a good experience to learn how to deal with the console, just make sure you're really need this knowledge right now....

I also have a wifi card with ralink RT2500 chipset, and it works without any tinkering in the console.
This is in 7.10 release.

In previous releases the card was not out-of-the-box supported, so I used the following guideline:
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

Good luck!

---

