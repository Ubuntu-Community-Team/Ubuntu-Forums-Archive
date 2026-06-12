---
title: "Braodcom wireless driver????"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by 1coyote on 2007-09-25
when I loaded 7.04 all went great....but it did not recognize my broadcom wireless card....what can I do in the future when I add new hardware......finding drivers...thanks for your help.

---

### Post by bobplano on 2007-09-25
which card is it? generally you are going to need ndiswrapper and the windows drivers for the card.

---

### Post by wormser on 2007-09-25
Run the following command to get the details of your card.  Then search the forum for the model number.  It should look something like this BCM4309.  Most the Broadcom cards have a howto written.  

```
lspci | grep Broadcom
```

---

### Post by 1coyote on 2007-09-25
i am new to ubuntu.....how is the driver added once the OS is installed?

---

### Post by bobplano on 2007-09-25
linux's wireless support is less than desirable, although ubuntu's is usually a bit better. there aren't many real wireless drivers for linux, so we need to know what your card is to really help you. run the command posted by wormser and post output here

---

### Post by anewguy on 2007-09-25
If you do the lscpi given above (in a termnial window - applications/accessories/terminal) it will tell you the model of the Broadcom card installed.  If that returns a card in the 43xx series, please see the first section of this how-to - it will get you running in no time!

[http://ubuntuforums.org/showthread.php?t=507505&highlight=gateway+mx3215+how+to]("http://ubuntuforums.org/showthread.php?t=507505&highlight=gateway+mx3215+how+to")

Good luck!:)

---

### Post by 1coyote on 2007-09-25
thank you all for all of your help...have a great night

---

### Post by masingerz on 2007-09-25
this one solved it for me and I had a generic wireless pci board

[http://ubuntuforums.org/showthread.php?t=25683&highlight=HOW+TO%3A+Configure+wireless+cards+with+Broadcom+chipsets](http://ubuntuforums.org/showthread.php?t=25683&highlight=HOW+TO%3A+Configure+wireless+cards+with+Broadcom+chipsets)

---

### Post by giox on 2007-09-26
Use this how to to setup your wireless card with ndiswrapper.

---

### Post by Circus-Killer on 2007-09-26
As you can see there are many howto's on how to get the broadcom wireless working.

**[This howto]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)")** is the one that did it for me.

---

