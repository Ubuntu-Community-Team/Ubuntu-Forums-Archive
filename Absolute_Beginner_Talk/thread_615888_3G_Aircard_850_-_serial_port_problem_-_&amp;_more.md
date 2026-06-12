---
title: "3G Aircard 850 - serial port problem - &amp; more"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by FrankIOM on 2007-11-17
Hi

I am new to Linux and am running Ubuntu 7.10 on my HP Laptop. At present I am busy trying to learn how to use the OS. My current only problem is trying to get my [COLOR="Red"]3G Sierra Aircard 850 PCMCIA card[/COLOR] working with KPPP. They system is recognising the card and the light if flashing when I follow the instructions from Sierrawireless and type pccardctl info in the terminal window the information comes up. 

My problem is that I need to set the card up as a serial device, the instructions tell me to locate file "[COLOR="Red"]serial_cs.c[/COLOR]" and then edit it with the supplied information. I cannot find a file with this name.  So I thought never mind if a run "dmesg | grep tty" as instructed it would tell me with serial port is in use etc. this did not work. the next step was to use "[COLOR="Red"]wvdialconf create[/COLOR]" it did not find the modem but asked if I would like to allocate one using (if I remember) setserial with the warning if you set the wrong one the system may clash and lock up . This is were I stopped. my thought is this, How can I find out which serial ports are in use so that I can safely allocate a spare one to my modem ? then is there a nice easy way of setting up this port or is the setserial the easy way, could I have some instructions on this. I think that once this is done my modem will work as I have done the settings in KPPP, at present all I get is an error message saying the modem is busy on every serial port, I have interpreted this as an error - can't find the modem

Thanks in advance for the help. Once all has settled I will feed back to Ubuntu about my laptop so they can add it to the list of working PC's

---

### Post by Brautigam on 2007-11-17
i am not familiar with that card but try using another one to see if it is your machine or the card. do you understand me?

---

### Post by FrankIOM on 2007-11-17
Thanks for the quick reply, The card works fine when used on the same laptop under windows XP, as a result I know it is a Linux OS problem not a hardware problem

---

