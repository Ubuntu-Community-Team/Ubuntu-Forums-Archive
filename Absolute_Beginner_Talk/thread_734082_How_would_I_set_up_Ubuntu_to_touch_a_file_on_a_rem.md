---
title: "How would I set up Ubuntu to touch a file on a remote server on boot."
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by bitterbug on 2008-03-24
I'm sure some of you have seen the story this week on Digg and Reddit about the "Xbox Moron" who stole an Xbox, TV, and Laptop from a guy and then made the mistake of bragging about it on Live, as well as getting himself on camera at a pawn shop.

What I'd like to do with all my machines is set them up so that when they are booted they touch a file on a remote web server and I can review the logs on that server to see the IP should any of them ever be taken.

Since there's a decent chance a thief may have the computer on a network connection at power-up, and not wipe the drive first, I'd want to be able to run the script before it even gets to the login screen. There would likely only be that single first boot before the person realizes it's not Windows and tries to format the drive.

Any tips, tricks, or recommendations? :)

---

### Post by very_japi on 2008-03-24
You could mount a network dive in a folder like /mnt/ntDrive or something at boot using rc.local and then use te touch command.

¿reasonable?

---

### Post by phr0ze on 2008-03-24
Sounds like a good idea. some kind of request on a obscure port might be all you need. No actual web server or anything to serve a file, just an open port that logs access attempts.

If you want to get fancy, use the web server and the file it downloads could tell the machine it's been stolen and wipe some of the personal data. This file could normally remain empty when the system is not stolen.

---

### Post by very_japi on 2008-03-24
You could also do something lke this:

> #get a file from al server
wget [http://www.eljapi.com/emergencyscript.sh](http://www.eljapi.com/emergencyscript.sh)
#give t execution rights
chmod ugoa+x emergencyscript.sh
#and execute it
./emergencyscript.sh

if your computer gets stolen you could modify that emergency sript to be deadly
like rm / -R

I dont know if there is someway to block all acces to a computer (meaning disable booting from anything other than Hard Drive and making GRUB ask for a password before booting)

---

### Post by phr0ze on 2008-03-24
Great suggestion Japi. I'd call the file updates.sh or something less eye catching. But this is it. 

Now Japi, where do we place this bit of script so it will execute before the system login prompt and will it have enough privilege to run?

---

### Post by Dr Small on 2008-03-24
Place it in /etc/rc.local

---

### Post by phr0ze on 2008-03-24
Here is a catch. Can we encourage this machine to find any open wifi and connect to try to get this file, then disconnect. The downside would be a delay as the script waits for a wifi connection to be established or timeout.

---

### Post by very_japi on 2008-03-24
Actually it doesnt take a lot of time.

iwlist wlan0 scan

will give you all accesspoints available, thenuse iwconfig to actually conect and disconect. But i do beleave that is going a bit to far.

---

