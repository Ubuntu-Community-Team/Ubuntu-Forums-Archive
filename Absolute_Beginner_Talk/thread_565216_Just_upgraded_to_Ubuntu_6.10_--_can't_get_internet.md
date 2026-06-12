---
title: "Just upgraded to Ubuntu 6.10 -- can't get internet connection working anymore"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by christinanilsen on 2007-10-02
hiya

my sidekick just decided to upgrade ubuntu, solo, to 6.10.  now it won't connect to the internet.  (not wireless, just basic modem connection).  we followed the regular instructions here: 

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#internet-basic-procedure](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#internet-basic-procedure)

but still aren't connected.  tried to ping the modem.  no network connection.

help..... please help ...

tkx
christina

---

### Post by sirgogo on 2007-10-02
Sidekick? Like the phone?

If not (meaning you are using a computer), try updating to the current version : Feisty Fawn 7.04 because you will get a lot better support.

First be able to edit your source list:

```
sudo sed -e ’s/\edgy/feisty/g’ -i /etc/apt/sources.list
```

Now update your source list:
```

sudo apt-get update
```

Now upgrade!:

```
sudo apt-get dist-upgrade
```

Then:

```
sudo apt-get -f install
```

Now restart and enjoy. (If you are using a computer, not a sidekick cellphone, that is). Good luck! :)

---

### Post by christinanilsen on 2007-10-02
uh ... will this upgrade work without an internet connection?  i assume no ... and must thus return to my original question .

please help

---

### Post by christinanilsen on 2007-10-02
please respond

---

### Post by philinux on 2007-10-02
when the grub menu shows up can you boot to the version that worked?

---

### Post by meborc on 2007-10-02
if the cable is correctly connected to the modem/router... and you HAVE reseted (take off the power for 10 sec) the modem/router AND waited it to repower itself... then open the terminal... and type **sudo dhclient**

give us the output... if it ends with something resembling an ip address, you are now connected... if not, we'll continue troubleshooting :D

---

### Post by christinanilsen on 2007-10-03
thanks!  we're up and running.

---

