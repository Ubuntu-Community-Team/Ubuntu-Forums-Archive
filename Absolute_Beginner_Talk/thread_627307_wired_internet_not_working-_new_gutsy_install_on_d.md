---
title: "wired internet not working- new gutsy install on dell latitude d505"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by mrufino1 on 2007-11-29
Hi, I installed gutsy tonight on my dell latitude d505. For some reason, I cannot get my wired connection working (therefore no wireless yet). I have gutsy installed on my emachines laptop, and although I needed a friend to get my wireless working there (I was BRAND new to linux that time- now I'm just new...), I remember the wired connection working right out of the box. Anyway, I searched here and haven't found anything- how do I fix this? In network tools, eth1 shows no info and the configure box is greyed out, on the network settings tab, eth 1 shows dhcp enabled but network manager doesn't seem to connect. What am I missing? I can't move forward with this at all without any net.Thanks-Mark

---

### Post by Ek0nomik on 2007-11-29
If you're wired Internet isn't working out of the box, the best idea is to probably narrow down what kind of NIC (Network Interface Card) you have since most work after a fresh Ubuntu install.  Do you know off the top of your head?

If not, typing this command should give you a listing of some goodies:

```
lspci
```

Copy and paste the output if you don't remember.

---

### Post by mrufino1 on 2007-11-30
I think the ethernet port may be physically broken- didn't work on windows when I booted into that either. The laptop was repaired (by dell) about 6 weeks ago- I bet they broke some connection when they replaced the screen, Is there a way to get the wireless working without having wireless internet?

---

### Post by Partyboi2 on 2007-11-30
Have you tried usb connecting your internet? You could try that and see if that works. I use to have a faulty ethernet plug and usb got around that problem. Check you ethernet cable, if you have a spare one try that. 
Can you see the NIC card green light on? You could see if your Nic is detected

```
sudo lshw -C network
```
But like you said its probably is the ethernet plug

---

### Post by mrufino1 on 2007-11-30
yes, using that command, it does see it. However, no light. Also, I have fios, so no usb connection for internet

---

### Post by chemtut on 2007-11-30
do you have any unused card  slots? if so , buy an ethernet card----they are about £10 in the UK
I use one of these

---

### Post by mrufino1 on 2007-11-30
If I am hooked up via a wired connection will the wireless set itself up now under gutsy? On my feisty install I know it didn't but I thought I heard gutsy now takes care of this. I installed ndis wrapper from the cd and got the driver from the internet- the card lists the driver when I got to the folder specified in my book (ubuntu for beginners, but it is not updated for gutsy), so I am not sure what else to do to get the wireless working. I may try a card if that will work.

---

