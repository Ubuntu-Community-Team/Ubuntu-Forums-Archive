---
title: "fatal error when trying to sort out my adsl usb"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by wadetuple on 2006-08-24
hello

i've been trying to configure my sagem fast800 usb adsl modem, on various linux distros and after trying mandriva and suse i am now giving it a go with ubuntu. I felt like i was actually getting somewhere by following the usbadslmodem/ueagle guide, everything seemed to be going fine until i got to the part where i tried to load the driver with:

"sudo modprobe ueagle-atm"

i got the message:

"FATAL: Error inserting ueagle_atm (/lib/modules/2.6.15-23-386/extra/ueagle-atm.ko) : Unknown symbol in module, or unknown parameter (see dmesg)"

can anyone help?

i tried to make sense of "dmesg" but i'm an absolute beginner (although one who can follow instructions!) - if you want me to post the results of "dmesg" tell me which lines, 'cos theres loads of them and i have to write them down and type them into my work pc before i can post them...

also, i tried to skip forward to "configuring the connection" but when i typed "sudo gedit /etc/ppp/peers" i got the message that that file could not be opened, even though i can see it...

i hope someone can help me sort this out, i am patient and will persevere, and theres no way i'm forking 200 quid out for XP.](*,)

---

### Post by aces21 on 2006-08-24
If to try:

```
dmesg|grep eagle
```

you'll only get lines from dmesg which include the word 'eagle', i.e. the ones of interest.

---

### Post by wadetuple on 2006-08-25
hello aces, thanks for replying... I've made some progress from before, but i still can't get online.

I started from scratch, re-installed ubuntu and followed the procedure that you described on the dapper forum that there was a link to from the guide. There were some slight differences, and your way worked better for me - i didn't get the fatal error message, my modem flashed and lit up. I still had some problems with "sudo gedit" but i managed to open the files after a few trys and put the configuration information.

however, after runninig "sudo modprobe pppoatm" and "sudo pppd call ueagle-atm" i did ifconfig and instead of getting "ppp0 Link encap:Point-to-Point Protocol"  it said something like "local loop" haven't got the rest of it written down. 

i'll try and configure it again in case i've made a typo, i was probably too excited at getting the modem to light up, but any advice gratefully received....

---

### Post by aces21 on 2006-08-25
> **wadetuple said:**
> hello aces, thanks for replying... I've made some progress from before, but i still can't get online.

I started from scratch, re-installed ubuntu and followed the procedure that you described on the dapper forum that there was a link to from the guide. There were some slight differences, and your way worked better for me - i didn't get the fatal error message, my modem flashed and lit up. I still had some problems with "sudo gedit" but i managed to open the files after a few trys and put the configuration information.

however, after runninig "sudo modprobe pppoatm" and "sudo pppd call ueagle-atm" i did ifconfig and instead of getting "ppp0 Link encap:Point-to-Point Protocol"  it said something like "local loop" haven't got the rest of it written down. 

i'll try and configure it again in case i've made a typo, i was probably too excited at getting the modem to light up, but any advice gratefully received....

Sounds like to modem is working o.k. Instead of "sudo pppd call ueagle-atm" try "pon ueagle-atm", then assuming that goes o.k. just type "plog". What do you get back?

---

### Post by wadetuple on 2006-08-26
Hello Aces, many many thanks for your help, and the guide you wrote in the forums, i am now online!!:D  What was stopping me before was that: 1) i did not have quotation marks round my username in my confguration file. 2) i had accidentally put an extra character in my password and 3) i had not deleted the bit that says " # Secrets for authentication using CHAP
# client	server	secret			IP addresses" from my chap-secrets file.
if any other newcomer to linux reads this, my advice would be to pay attention to the details, it's easy to become frustrated trying to get your head around what looks like a foreign language if you are used to just pointing and clicking, in my case the final hurdle was some bleedin' obvious typos..

A couple of further requests for advice: firstly, is there a way of automating the "pon ueagle-atm" and plog bits, so my girlfriend can use the internet when she turns the computer on without having to open up a terminal?
secondly, is there a way of making sure any updates or other packages i install don't mess with my settings so that i can't get online?

One other thought that occurs to me, is that a useful thing would be to include a comprehensive guide to getting online with the dvd or cd, maybe as a pdf or something, including the advice from these forums.. i was fortunate this week that my boss was on leave, so i could surf at work but i would have been completely stuck if i couldn't...

thanks again

---

### Post by divali on 2006-08-27
I had the same trouble with the drivers for my sagem modem, given to me by Tiscali, and found the chaps at:  [http://atm.eagle-usb.org/wakka.php?wiki=PagePrincipaleEn](http://atm.eagle-usb.org/wakka.php?wiki=PagePrincipaleEn)

to be very useful. BUT, And here's the rub, the usb modem drivers are often very hard and time consuming to configure, I know I've been there.My reccomendation is use an ethernet modem. good luck.

---

### Post by aces21 on 2006-08-29
> **wadetuple said:**
> Hello Aces, many many thanks for your help, and the guide you wrote in the forums, i am now online!!:D  What was stopping me before was that: 1) i did not have quotation marks round my username in my confguration file. 2) i had accidentally put an extra character in my password and 3) i had not deleted the bit that says " # Secrets for authentication using CHAP
# client	server	secret			IP addresses" from my chap-secrets file.
if any other newcomer to linux reads this, my advice would be to pay attention to the details, it's easy to become frustrated trying to get your head around what looks like a foreign language if you are used to just pointing and clicking, in my case the final hurdle was some bleedin' obvious typos..

A couple of further requests for advice: firstly, is there a way of automating the "pon ueagle-atm" and plog bits, so my girlfriend can use the internet when she turns the computer on without having to open up a terminal?
secondly, is there a way of making sure any updates or other packages i install don't mess with my settings so that i can't get online?

One other thought that occurs to me, is that a useful thing would be to include a comprehensive guide to getting online with the dvd or cd, maybe as a pdf or something, including the advice from these forums.. i was fortunate this week that my boss was on leave, so i could surf at work but i would have been completely stuck if i couldn't...

thanks again

I'm not at my machine now so doing this from memory, but if you go to SYSTEM - PREFERENCES - SESSIONS, then STARTUP PROGRAMS, you can add the command "pon ueagle-atm" there so it will startup when you log in. If your GF has a separate profile, you'll need to add it in there as well. You don't need to run plog, that just gives you the pppd log output.

As fr updates, the only thing that should mess with ueagle is if you install a new kernel. You can either tell Ubuntu to not install new kernels, which I can't remember how to do off hand, or else install it then rebuild ueagle for the new kernel. There are instructions in the howto.

Have fun.

---

