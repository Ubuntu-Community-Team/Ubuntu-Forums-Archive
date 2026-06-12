---
title: "How do i install a game called Think Tanks?"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Repent on 2007-02-06
Hi I'm a Linux noob I have been trying to install a game called Think Tanks  [http://www.garagegames.com/pg/product/view.php?id=12](http://www.garagegames.com/pg/product/view.php?id=12)  It downloads it to my desktop where should I put it and how do I install it. 

Please Help.

Thanks Repent.

---

### Post by taurus on 2007-02-06
What format is it in?  What's the output of this command from a terminal?

```
ls -la ~/Desktop
```

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Wikzo on 2007-02-06
I tried to download the demo as well. I get this file:

ThinkTanksDemo_v1.1.sh.bin

Can't open it (Ubuntu 6.10) :)

---

### Post by taurus on 2007-02-06
> **Wikzo said:**
> I tried to download the demo as well. I get this file:

ThinkTanksDemo_v1.1.sh.bin

Can't open it (Ubuntu 6.10) :)

```
chmod 755 ThinkTanksDemo_v1.1.sh.bin
./ThinkTanksDemo_v1.1.sh.bin
```

---

### Post by Wikzo on 2007-02-06
Dunno what the code did, but now I get the installer from. Great!

But the things are really hard to read, the text is very strange. I do not want to install the game, but now we know, it works :)

---

### Post by Repent on 2007-02-06
Wow thanks taurus, Now all have have to do is install my nvidia drivers and I'm set. Will this command work on all game installs? :guitar:

lol....and while I'm at it how do I install my drivers.

Thank you.

---

### Post by taurus on 2007-02-06
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by Repent on 2007-02-07
This is the code that came with the game :  cd(spc)/home(spc)joe203 sh(spc)/home/joe203/ThinkTanks_v1.1.sh.bin'  Can someone please tell me why it will not work.](*,)

---

### Post by taurus on 2007-02-07
> **Repent said:**
> This is the code that came with the game :  cd(spc)/home(spc)joe203 sh(spc)/home/joe203/ThinkTanks_v1.1.sh.bin'  Can someone please tell me why it will not work.](*,)

How come you asked the same question three times, in two new threads?  

You have ThinkTanks_v1.1.sh.bin in /home/joe203!

```
cd ~
chmod 755 ThinkTanks_v1.1.sh.bin
./ThinkTanks_v1.1.sh.bin
```

---

