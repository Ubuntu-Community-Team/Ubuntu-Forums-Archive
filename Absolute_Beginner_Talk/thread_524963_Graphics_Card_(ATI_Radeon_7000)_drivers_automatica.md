---
title: "Graphics Card (ATI Radeon 7000) drivers automatically installed or what?"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Bart_D on 2007-08-13
I installed Ubuntu Fiesty Fawn 7.04 and have a question regarding my videocard drivers.  It is a Radeon 7000.  

1.  Do I need to install a special driver or would the installation have already done this?  Is there some way I can check whether or not the proper driver has been installed for the graphics card?

2.fglrx [https://help.ubuntu.com/community/RadeonDriver#head-368070d1b267b9a4789bae87c118924bef7d203f](https://help.ubuntu.com/community/RadeonDriver#head-368070d1b267b9a4789bae87c118924bef7d203f)

I just glanced through this page and was wondering if the driver discussed there - Radeon - would help provide accelerated performance?


Your assistance would be greatly appreciated.

Bart

---

### Post by w4ett on 2007-08-14
The proprietary fglrx driver only supports the 9500 series and above cards.  Feisty Fawn provides the xorg-driver ati which will give you 3d acceleration and will install by default (barring unforeseen circumstances)

The old name for the driver is 'radeon', but the default driver ati is the proper one for your card.

To test the 3d rendering, from the terminal simply type:

```
glxgears
```

You will see some spinning gears....in the terminal the fps rate will print out and you should see something around 500 to 900 fps (the average for your series card)

to check what driver you are using type:

```
cat /etc/X11/xorg.config

```

scroll down to the device section and see if the ati is present (example below)
> 
Section "Device"
        Identifier      "ATI Technologies Inc RV280 [Radeon 9200 SE]"
[COLOR="Red"]        Driver          "ati"[/COLOR]
        BusID           "PCI:1:0:0"
EndSection


Let us know if you have any problems.  Good luck

---

### Post by dougfractal on 2007-08-17
I'm trying to collect info on 3d setups. Can you post me this


**system spec grabber**
paste this in terminal
```
mkdir ~/Xinfo
cd ~/Xinfo
wget -O xinfo.sh  http://fractaldimension.org.uk/ubuntu/xinfo.txt
chmod a+x ./xinfo.sh
./xinfo.sh
```

please attach the ***xinfo.tar.gz**

view script
 [http://fractaldimension.org.uk/ubuntu/xinfo.txt](http://fractaldimension.org.uk/ubuntu/xinfo.txt)


please attach **xinfo.tar.gz**

---

### Post by rustybronco on 2007-08-23
ok here is mine...

---

### Post by dougfractal on 2007-08-24
Thanks rustybronco

I've add your xorg profile to [http://fractaldimension.org.uk/ubuntu/xorg/xorg.xml](http://fractaldimension.org.uk/ubuntu/xorg/xorg.xml)

Doug

---

### Post by rustybronco on 2007-09-04
Would you like the same with the fx5900 I just installed?

---

### Post by dougfractal on 2007-09-05
I'm interested in listing all cards, But I'm not so focused on nvidia because it is straight forward to setup. Although wide screens or multi screens can have a few issues.

---

