---
title: "need help connecting wireless while running from dvd"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by frazbox on 2008-03-24
this is the first time im using ubuntu, so please bare with me.....

i wanted to try out linux, so i downloaded ultimate edition 1.7 dvd. i was liking the gui, but when i tried to connect to my wireless router, it kept asking for my passkey. i typed it in like a 100 times but it didnt connect. i tried to do it manually, and it change to a wireless strength bar, but it said 0%. when i was trying to connect by roaming, i didnt notice any activity from the router. 

i have a toshiba laptop, with a integrated wireless card intel 2200bg, netgear router wgr614, and wep security enabled. 

is there a way to get it working without all the codes??

if, not.... can i get a guide to try and enable with the codes??

thanks

---

### Post by ichbinesderelch on 2008-03-24
you could try this doing with iwconfig/ifconfig, if you are running on dhcp just type in console:
ifconfig <networkinterface> dhcp start
than you gotta set your essid with iwconfig:
iwconfig <networkinterface> essid <nameofwlannetwork>
and finally set your wep key:
iwconfig <networkinterface> key <key>
hope this works!

---

### Post by frazbox on 2008-03-24
ok.... i so new to linux..... i have no clue what that means!!!
first... where do i find iwconfig??
what do you mean by <networkinterface>??
i got the key part

---

### Post by jan quark on 2008-03-24
ok first open the terminal it can be found here

applications > accessories > terminal

and type these commands into it to get a picture of your current network status
please post the output here using the code brackets # to make it more readable

```
iwconfig
```
```
sudo iwlist scan
```
```
sudo lshw -C network
```
```
cat /etc/network/interfaces
```

---

### Post by MONODA on 2008-03-24
I know what your problem is. When you choose to connect to a network and it asks for your passkey, enter it in the box, but dont press connect yet. Select a type of encryption that your network has, if you dont know, just try them all.
EDIT: dont do what the others said unless my way does not work.

---

### Post by frazbox on 2008-03-24
> **MONODA said:**
> I know what your problem is. When you choose to connect to a network and it asks for your passkey, enter it in the box, but dont press connect yet. Select a type of encryption that your network has, if you dont know, just try them all.
EDIT: dont do what the others said unless my way does not work.

i tried that, but the box keeps coming back up. i checked the router and it set to automatic, ans i even changed it to the two options that it gives...

thanks for the advice!!!
i went back into it and figured out that i was using the passphrase. i had to change the option to use the key and voila, it connect!!!!

---

### Post by frazbox on 2008-03-24
> **jan quark said:**
> ok first open the terminal it can be found here

applications > accessories > terminal

and type these commands into it to get a picture of your current network status
please post the output here using the code brackets # to make it more readable

```
iwconfig
```
```
sudo iwlist scan
```
```
sudo lshw -C network
```
```
cat /etc/network/interfaces
```

code brackets #??

---

### Post by ichbinesderelch on 2008-03-24
those code brackets would be the important ones :P

---

