---
title: "Wireless question"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by zubala on 2007-07-04
Hi all.  I know nothing about computers and I bought a Dell laptop off ebay and on a whim and installed Feisty to see what's all  the fuss with linux.  After installation the wireless device didn't work.  After a day of Google searches(on my other comp) and copying, pasting command lines i've no clue about  and installing programs, I somehow managed get the wireless card to work (don't ask me how) but no internet.  After another day of Google searches I typed in dhclient in the terminal and now my wifi connection works!

But  if I restart my laptop, I have to type in dhclient in the terminal first to get a connection. Is there a way fo my wifi connection to connect automatically when I start up my laptop?

 I'm using one of those wifi connection where you have to type in a password in the browser to get a connection.

Thanks!

---

### Post by dmfield on 2007-07-10
> **zubala said:**
> Hi all.  I know nothing about computers and I bought a Dell laptop off ebay and on a whim and installed Feisty to see what's all  the fuss with linux.  

Good for you, its a steep learning curve, but one which i'm sure you will appreciate. Now, which dell did you buy? does it have a model number? that way i can tell which Wifi card you have.


> **zubala said:**
> After installation the wireless device didn't work.  After a day of Google searches(on my other comp) and copying, pasting command lines i've no clue about  and installing programs, I somehow managed get the wireless card to work (don't ask me how) but no internet.  After another day of Google searches I typed in dhclient in the terminal and now my wifi connection works!

You'd be suprised how many people don't use google, so full respect for getting this far. Again, the Dell model number, i think you can use ndiswrapper..

> **zubala said:**
>  But  if I restart my laptop, I have to type in dhclient in the terminal first to get a connection. Is there a way fo my wifi connection to connect automatically when I start up my laptop?

We can use Gnome's network Manager, to do this for you..

> **zubala said:**
>   I'm using one of those wifi connection where you have to type in a password in the browser to get a connection.


? Public Wifi?

anyway, get back, with the PC model number, and i'll do my best to get you working...

---

### Post by zubala on 2007-07-15
Hi, sorry for the late reply. 

I bought a Dell D600.   I spent a whole day trying to figure out  ndiswrapper until my wireless card finally worked.  Still no clue how I did that. But now, I can connect to the internet just fine.  However, I  have to type in sudo dhclient in the terminal (for some reason I have to do it twice now for my internet connection to work). after I reboot my laptop. I was just wondering why it doesn't do this automatically.

I'm using a wayport access since i only have this wireless service at my place.

Thanks!

---

