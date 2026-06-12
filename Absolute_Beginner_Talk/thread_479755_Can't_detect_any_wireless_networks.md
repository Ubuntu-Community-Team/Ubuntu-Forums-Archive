---
title: "Can't detect any wireless networks"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by llamaaway on 2007-06-20
Got Ubuntu to work again and now its not detecting any wireless networks. Help!

---

### Post by gustavocm on 2007-06-20
what wireless driver do you have?

---

### Post by wil313 on 2007-06-20
Are you trying to use a broadcom card?

---

### Post by llamaaway on 2007-06-20
sorry i didnt give nearly enough info... Broadcom Airforce One... it has the word airforce in  it.

---

### Post by llamaaway on 2007-06-20
bumpity bump

---

### Post by Mostlyharmless42 on 2007-06-20
I'd like to second that bump.  

I just installed Dapper Drake from an old cd i had lying around.  I have a Belkin wireless net work card and it isn't being detected.  I've had problems w/ the same card in windows, so i'm planning on getting a new card

What card should i get that would be 100% linux compatible.  Plus how do i get the drivers to intstall it???

---

### Post by Papi-KB7VGW on 2007-06-20
This link will take you to the Linux Hardware compatibility guide.  Follow the wireless link.

[http://doc.gwos.org/index.php/HCL](http://doc.gwos.org/index.php/HCL)

---

### Post by llamaaway on 2007-06-21
linux can see my wireless card theres just no access points

---

### Post by digital_sabotage on 2007-06-21
there is a program i've used before in gnome  ...just can't remember what it's called and couldn't find it in synaptic pkg manager  

...one way to go if you are looking to connect to unsecured networks is to type "any" (minus quotes) as your essid and leave the network password blank

...i'll see if i can find the program that detects wireless access points

....hope this helps:-)

---

### Post by digital_sabotage on 2007-06-21
...well i did find one way for you to go ...from terminal
```
iwlist ath0 scan
```
where "ath0" is my network connection

this will list info on all access points in range

---

### Post by gcos7 on 2007-06-21
Do you have one of the network managers installed?  I have Broadcom wireless in my laptop, and after getting the driver working via ndisdriver, I couldn't see any wireless networks until I installed either network-manager or network-manager-gnome.

Hope that helps!

---

### Post by gustavocm on 2007-06-22
> linux can see my wireless card theres just no access points

have you tried ndiswrapper?
i had the same problem here with a broadcom card and solved it using ndiswrapper

---

### Post by diatribe on 2007-06-22
another option is wicd, it works on my broadcom card

wicd.sourceforge.net

---

