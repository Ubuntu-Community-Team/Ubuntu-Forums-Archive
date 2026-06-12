---
title: "Problems with bluetooth"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by oberengu on 2008-02-03
Hi all!

I have a laptop with integrated bluetooth (asus Z53s), and I have installed ubuntu and all the programs to run it, but it does not work. 
I have installed gnome-blue, libbluetooth, bluezgnome, kbluetooth, bluetooth analyser, kbtoexclient.
Some help!

---

### Post by PmDematagoda on 2008-02-03
Could you please post your problem a little more specifically, what problems are you having with Bluetooth?

---

### Post by oberengu on 2008-02-03
The problem is that all rhe programs seems to be installed, but it is impossible to recognize my phone, and my phone does not recognize the laptop

---

### Post by PmDematagoda on 2008-02-03
Install Blueman by following the instructions given [here]("http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56").

The command to install it is:-
```
sudo apt-get install blueman
```

It can then be found in Applications>Accessories>Blueman Bluetooth Manager.

---

### Post by oberengu on 2008-02-03
I am sorry but after typing the instructions in a terminal it can not find blueman

---

### Post by PmDematagoda on 2008-02-03
Did you add the proper repositories as stated in the install guide?

Also did you reload the sources lists using:-
```
sudo apt-get update
```

---

### Post by oberengu on 2008-02-03
I have installed bluetooth manager 0.3, but it still does not recognize any bluetooth signal.
I am trying to restart the computer in case it is necessary.

---

### Post by PmDematagoda on 2008-02-03
Did you check to ensure that your phone was visible instead of being hidden?

---

### Post by oberengu on 2008-02-03
Of course, I usually use my bluetooth phone in the car

---

### Post by oberengu on 2008-02-03
It still does not work.
The program is OK but it says "No adapters found" and all the icons are off

---

