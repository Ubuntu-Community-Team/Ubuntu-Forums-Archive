---
title: "Using terminal to install HPLIP"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by scyowner on 2008-03-06
I apologize for such a basic question, but I am not at all familiar with using terminal. I am trying to install the latest HPLIP drivers following the directions from the sourceforge website. In the directions they state "cd to the download directory." I downloaded the file to my desktop, what do they mean by the above statement and how do I do it?

---

### Post by taurus on 2008-03-06
Do you know the name of that file?

Applications -> Accessories -> Terminal
```
ls -la ~/Desktop
```

---

### Post by kellemes on 2008-03-06
> **scyowner said:**
> I apologize for such a basic question, but I am not at all familiar with using terminal. I am trying to install the latest HPLIP drivers following the directions from the sourceforge website. In the directions they state "cd to the download directory." I downloaded the file to my desktop, what do they mean by the above statement and how do I do it?

This should brink you to the desktop..
```
cd ~/Desktop
```

Still, you can install (this is prefered) hplip using your package-manager like so..
```
sudo apt-get install hplip
```
Or startup "synaptic" from the menu's and search for "hplip"

---

### Post by milton1 on 2008-03-06
hplip is pre-packaged for ubuntu. Access the terminal as taurus instructed and try this:

```
sudo apt-get install hplip
```

---

### Post by gvhg on 2008-03-06
I am assuming you are following instructions from [http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)
They are asking you to change the directory to the one in which your file was downloaded in (in this case Desktop)
```

cd ~/Desktop

```
thereafter, you might want to move the file to your /opt directory
```

sudo mv hplip-2.8.2 /opt

```
then change directory to the one you moved the file in and extract,
```

cd /opt
sudo sh hplip-2.8.2.run

```
Proceed as mentioned in the instructions and you should be ok

---

### Post by scyowner on 2008-03-06
Thanks everyone. That got me going and I learned a little more about Ubuntu!! Got everything to install up to the point where it searches for the printer and the program can't find it. The printer is connected to a computer on the network running windows xp. Even when I enter the host name in a manual search, hplip can't find the printer. Any suggestions here??

---

### Post by m@ra on 2008-03-12
Hi... Now first you should do couple of checks.

1) Can you Ping that Windows computer with hostname?
2) Do you know if you are in same subnet? (Behind NAT)
3) Is that printer shared from Windows

Remember that access to Windows print server goes as a Samba (smb/cifs) protocol.

Verify these first.

---

