---
title: "[SOLVED] How do I connect to my wireless WEP network from the command line?"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by anewguy on 2008-03-22
I am trying to use Envy to install the video driver for a "new" video card.  The only thing I can get to with that card installed is the command line.  Envy needs net access.  I did sudo ifconfig but didn't see wan0, so I tried dhclient on eth1 with no success and then the same on eth0.

I assume somewhere I must need to create/edit something that tells it the sessionid I want to connect to, the security (WEP open) and the password.  Only thing is I don't have a clue.  I've searched "ubuntu connect internet from command line" on the search engines and haven't gotten anything that tells me how to do this.  HELP!!!  :):)

Any help would be greatly appreciated!  :)

---

### Post by Sam Lars on 2008-03-22
I think you're looking for iwconfig.
```
sudo iwconfig
```
Look for your card there.  If you see it:
```
sudo iwconfig eth0 key 00000000000000000000000000 rate 54M ap auto essid name
```
eth0 = your interface, what you saw in the plain iwconfig
00000000000000... = your key (in hex, numbers and letters)
54M = your speed... this is full speed for wireless G, 24M is B...
auto = you can type in your router's... it will be like 00:0F and so on... but auto should work
name = the name of your access point

---

### Post by which_chick on 2008-03-22
Hopefully you know what goes in for "mynet" (should be the name of the network you want) and you have a key for this.

```

sudo iwconfig eth2 essid MyNet
sudo iwconfig eth2 key xxxxxxxxxx
sudo ifconfig eth2 up
sudo dhclient3 eth2

```


(Source:  [http://mediakey.dk/~cc/howto-use-wep-encryption-with-ubuntu-linux/](http://mediakey.dk/~cc/howto-use-wep-encryption-with-ubuntu-linux/))

---

### Post by anewguy on 2008-03-22
Thank you both SO MUCH!!!!  I'm going to give those a try in a few minutes.

:)

---

### Post by anewguy on 2008-03-23
While more typing, I went with which_chicks' instruction only because I wanted to be sure I got each option in right.  Worked like a champ - thanks you guys!  :)

---

