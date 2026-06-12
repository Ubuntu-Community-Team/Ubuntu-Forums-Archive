---
title: "[SOLVED] Shortcut to ISP connection in ubuntu, Need guidance"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by onlytanmoy on 2007-11-26
Dear All, I am using Ubuntu 7.10 Gutsy Gibbon.
I have a PPPoE connection. I searched in google & got some basic inputs as to how to config PPPoE.
In konsole, i issued the command sudo pppoeconf & configured my PPPoE & internet worked fine after that. wat i want is like in windows i have a shortcut to my connection where login id/pwd for my ISP are saved, i just double click n connect to net via that..is such a shortcut thing possible in ubuntu also?
Thanks.

---

### Post by ukripper on 2007-11-26
you can add you network settings in /etc/network/interfaces to automatiocally connect to network.

```
sudo gedit /etc/network/interfaces
```

also network-admin saves your settings. open network admin by folowing:```
sudo network-admin
```

---

### Post by onlytanmoy on 2007-11-26
sorry, but am still not able to figure out how to add a shortcut to my pppoe conn on desktop :( 
i am a newbie to linux m8, plzz guide me step by step..thanks.

---

### Post by deadgobby on 2007-11-26
[http://ubuntuforums.org/showthread.php?t=497782](http://ubuntuforums.org/showthread.php?t=497782)

 There is a GUI setup for your type of internet. Please read through them and see which one will work for you. 

Gobby

---

### Post by onlytanmoy on 2007-11-26
thanks again Gobby...my problem is solved :)
Mine is an USB ADSL modem & i configured it with the help of the below thread
[http://ubuntuforums.org/showthread.php?p=3182052](http://ubuntuforums.org/showthread.php?p=3182052)

which i got via the link u provided...thanks again bro..God bless.

---

