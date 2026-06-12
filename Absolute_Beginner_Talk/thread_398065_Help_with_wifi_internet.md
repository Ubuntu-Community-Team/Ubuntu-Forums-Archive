---
title: "Help with wifi internet?"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by SamTyson92 on 2007-03-31
I have just installed Ubuntu 6.10 successfully and its working fine but ive got something like 164 updates!

Anyway its my first time in Linux and Im currently using the ethernet cable downstairs to connect to the internet but I need the wifi card to work when Im upstairs but when I used the live cd it said that it wasn't working and said some error. So do I need a driver?
Its a Atheros AR5006EG Wireless Network Adapter.

I really need this ASAP and im completly new to linux and ubuntu so step by step guide please.

---

### Post by dfreer on 2007-03-31
Do you have the restricted modules for your kernel installed? Try entering this command in Terminal:
```
sudo apt-get install linux-restricted-modules-`uname -r`
```
You will then need to reboot.


These may help (if you do compile the MadWifi drivers, you will need to install the build-essential package)
```
sudo apt-get install build-essential
```
[http://ubuntuforums.org/showthread.php?t=212600](http://ubuntuforums.org/showthread.php?t=212600)
    -> [http://ubuntuforums.org/showpost.php?p=2108625&postcount=16](http://ubuntuforums.org/showpost.php?p=2108625&postcount=16)

---

### Post by chili555 on 2007-03-31
While you are downstairs, let the 164 updates run, reboot and open a terminal and type:```
sudo apt-get install linux-restricted-modules
```Then see if your wireless jumps to life. Post back if you need more help.

---

### Post by SamTyson92 on 2007-03-31
It wont let me type my password and in firefox it dosent type very fast in the address bar and google search and then keeps on typing the same letter.

---

### Post by annda on 2007-03-31
you don't see your password. just type it slowly and correctly and press RETURN.

---

### Post by Maestro23 on 2007-03-31
> **SamTyson92 said:**
> It wont let me type my password and in firefox it dosent type very fast in the address bar and google search and then keeps on typing the same letter.

In a terminal, you will not see the cursor move for security reasons.  Just type your password in and hit ENTER.

---

### Post by SamTyson92 on 2007-03-31
> **chili555 said:**
> While you are downstairs, let the 164 updates run, reboot and open a terminal and type:```
sudo apt-get install linux-restricted-modules
```Then see if your wireless jumps to life. Post back if you need more help.

It said it couldnt find packahe linux restricted modules.

---

### Post by dfreer on 2007-03-31
Use this command instead:
```
sudo apt-get install linux-restricted-modules-`uname -r`
```

---

### Post by SamTyson92 on 2007-03-31
> **dfreer said:**
> Use this command instead:
```
sudo apt-get install linux-restricted-modules-`uname -r`
```

Ive done that and it said 0 upgrades 0 install etc. so it must be something else.

---

### Post by dfreer on 2007-03-31
Could you post the output of:
```
iwconfig
```
and:
```
sudo lshw -class network
```
Also, make sure you completely update/upgrade the PC as above post stated, that may help.

---

### Post by Maestro23 on 2007-03-31
> **SamTyson92 said:**
> Ive done that and it said 0 upgrades 0 install etc. so it must be something else.

Do you have all your Repositories enabled?

Synaptic(GUI): [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Command line: [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by Lonthong on 2007-04-03
See this following link to get atheros ar5006eg working:
[http://ubuntuforums.org/showthread.php?t=212600&page=3&highlight=atheros+ar5006eg](http://ubuntuforums.org/showthread.php?t=212600&page=3&highlight=atheros+ar5006eg)

---

