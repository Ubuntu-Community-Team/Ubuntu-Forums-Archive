---
title: "Frostwire"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by julie_lebou on 2007-03-21
I tried this to install Frostwire... but after i'm done... (see ***)

1. Remove frostwire

Code:
sudo apt-get remove frostwire

2. we download it and install it

Code:
wget [http://peercommons.com/frostwire/4.13.1/frostwire-4.13.1.i586.deb](http://peercommons.com/frostwire/4.13.1/frostwire-4.13.1.i586.deb)
sudo dpkg -i frostwire-4.13.1.i586.deb

3. ok, now, we install jre1.5 (no matter if it is already installed)
download link: [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)
next we copy the new file to /usr/java, if the directory does not exist, create it.

NOTE: this is the second file on the list: Linux (self-extracting file)(filesize: 16.27 MB)

Code:
sudo mkdir /usr/java
sudo cp jre-1_5_0_11-linux-i586.bin /usr/java

ok,now

Code:
sudo chmod a+x /usr/java/jre-1_5_0_11-linux-i586.bin
sudo /usr/java/jre-1_5_0_11-linux-i586.bin

type yes when it asks and you're done.

Code:
frostwire


***Ok, i did everything, and it all went fine... but after i write yes, and im ''done''

what do I do to install/start Frostwire? It just says

code: frostwire.. and that dosent work

---

### Post by adam.tropics on 2007-03-21
You installed it already. It should be in your Applications-->Internet menu.

---

### Post by julie_lebou on 2007-03-21
its not there... do i need to reboot?

---

### Post by julie_lebou on 2007-03-21
the only thing new i see in applications - Internet is java

---

### Post by adam.tropics on 2007-03-21
Just looking at the format of your first post, did you type in terminal 
```
frostwire
```or
```
code:frostwire
```

You want the first one. If something is wrong then you should see error messages in the terminal you entered that into..

---

### Post by julie_lebou on 2007-03-21
yes i did write only frostwire... this came up:

julie@julie:~$ frostwire
bash: frostwire: command not found

---

### Post by adam.tropics on 2007-03-21
redo step 2 of your list then (at least the second part if you have already downloaded it). That would seem to indicate it isn't installed.

---

### Post by julie_lebou on 2007-03-21
thanks... its weird cause i did that part... but i did it again and it worked! thanks a lot!

---

### Post by adam.tropics on 2007-03-21
Welcome.

---

