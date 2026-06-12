---
title: "Wireless Network Help Needed - 1st day on ubuntu"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by zmuth734 on 2007-01-02
Hello everyone,

Today is my first day using ubuntu / any linux distribution.  I feel dumb now because I was an expert at windows and now I am really bad at this.

I need help setting up my wireless connection.  I am using an Intel 2200B/G.  So far I have opened up a terminal and did this:

sudo iwconfig eth1 mode Managed
sudo iwconfig eth1 essid dlink
sudo iwconfig eth1 key restricted MyWPAkey
sudo iwconfig
sudo ifconfig eth1 up
sudo dhclient eth1

I then realized Ubuntu has a network manager so I also typed in my details there.  Now under connection properties it says Name: eth1, Signal Strength: 100%, yet I cannot access any websites.

And I have another question, I go to college and how would I be able to use their wireless internet (vpn client was required with windows).  How do I access any network of which I do not know the SSID?

Thanks everyone for your help and I hope I can use ubuntu more often than windows... :-?

EDIT:  Dang I just checked and I CAN access websites but only google and ubuntuforums... so confused?

---

### Post by MkfIbK7a on 2007-01-02
install the attached wifi radar package on your computer go **Applications > internet > wifi-radar**
im sure you can find your way from there:D

---

### Post by oilchangeguy on 2007-01-02
under the network manager you should see three things listed, your nic card, your wireless card, and your modem (probably not working, but that's another thread). you've got to enable the wlan connection. at the top of the screen see the 2 monitors icon to the left of the clock? if wlan is not listed, from the network manager, highlight the wlan connection, click properties , place a check to enable the connection and enter your network security code if you use one.

---

### Post by zmuth734 on 2007-01-02
> **wert613 said:**
> install the attached wifi radar package on your computer go **Applications > internet > wifi-radar**
im sure you can find your way from there:D

Thanks, it is a very nice program, I like it.  However, I can still only access google and ubuntuforums over the wireless network.  I can't get on any other sites?  I can get on any website while wired.

---

### Post by MkfIbK7a on 2007-01-02
you mean you cant get on a website like ebay.com?
what happens when you try?

---

### Post by zmuth734 on 2007-01-02
> **wert613 said:**
> you mean you cant get on a website like ebay.com?
what happens when you try?

I'm using Firefox and I just typed in [www.ebay.com](www.ebay.com) and pushed enter.  On the status bar it says looking up [www.ebay.com](www.ebay.com)...  and it just stays like that, nothing loads.  I can get on google but I can't get on google mail (gmail.com)? This only happens on wireless.

---

### Post by MkfIbK7a on 2007-01-02
hmm myabe it has to do with firefox can you try to install opera?

---

### Post by zmuth734 on 2007-01-02
> **wert613 said:**
> hmm myabe it has to do with firefox can you try to install opera?

I just installed Opera and tried it but I have the same problem.  I just noticed if I close firefox after unhooking the wired connection I can't get on ANY websites with my wireless connection.

---

### Post by MkfIbK7a on 2007-01-02
i odnt know are you using your own wireless network or your colleges network?

---

### Post by zmuth734 on 2007-01-02
> **wert613 said:**
> i odnt know are you using your own wireless network or your colleges network?

I'm using my own at my house.  I can't even get onto my router's address:  192.168.0.1  until I hook directly up.  Maybe its a wpa problem or something, but I'm pretty sure I typed in the correct wpa code.  I'm using a dlink gamerlounge router ( DGL-4300 ).

---

### Post by MkfIbK7a on 2007-01-02
ok then go to synaptic package manager
**System > Administration > Synaptic package manager**
search "network"
scroll down find network-manager
install it 
try that

---

### Post by zmuth734 on 2007-01-02
Here are some screenshots of my wifi radar:

[http://img506.imageshack.us/img506/6758/screenshotqp8.png](http://img506.imageshack.us/img506/6758/screenshotqp8.png)

[http://img506.imageshack.us/img506/5629/screenshot1yc8.png](http://img506.imageshack.us/img506/5629/screenshot1yc8.png)

Thanks for all your help so far :)  I'm trying the network-manager.  I installed it but I don't know where it went. or how to open it.

---

### Post by MkfIbK7a on 2007-01-02
you are putting in the wep key correctly right

---

### Post by zmuth734 on 2007-01-02
> **wert613 said:**
> you are putting in the wep key correctly right

Yes and I just noticed it says WPA on the wifi radar but my router uses WEP, does the "key" form on the wifi radar mean WEP and the WPA below it is for something else?

---

### Post by MkfIbK7a on 2007-01-02
when it says key put in your WEP key the WPA drop down is for WPA

---

### Post by zmuth734 on 2007-01-02
I GOT IT TO WORK!  This is what I did:

1) I right clicked on the wireless network connection on the Panel and clicked properties.
2) I clicked configure.
3) I unchecked "Enable this connection"
4) I then went to wifi radar and connected using that, using the profile I set up for that specific network, with the WEP and all.
5) It worked!

I was thinking maybe I should take out all the settings I had in the network manager and just let wifi radar handle it.  It wasn't working with both applications trying to do it, and it wasn't working with just network manager by itself either.

Thanks for all your help wert613.  Goodbye Windows :)

---

### Post by MkfIbK7a on 2007-01-02
good for you:D and well come to the light side:D

take the Gates off the hinges and break the Windows

---

### Post by zmuth734 on 2007-01-02
On a side note.. how do I uninstall Opera now?  I can't find it under Applications>Add/Remove :-|

---

### Post by MkfIbK7a on 2007-01-02
how did you install it?
if by synaptic go back to it in synaptic and right click on the check box choose completely remove

---

### Post by zmuth734 on 2007-01-02
> **wert613 said:**
> how did you install it?
if by synaptic go back to it in synaptic and right click on the check box choose completely remove

Thanks, you're the best. :D   I didn't know there was a difference between that and applications>add/remove (the words of a dumb windows user)

---

### Post by MkfIbK7a on 2007-01-02
no prob im going to add you to my buddy list if thats ok with you

---

### Post by zmuth734 on 2007-01-02
> **wert613 said:**
> no prob im going to add you to my buddy list if thats ok with you

Okay, that's cool.  I added you to mine, I don't know what it does but I'll find out I guess.

---

### Post by MkfIbK7a on 2007-01-02
doesnt acctually do anything mostly just keeps me from forgeting your name:D

---

