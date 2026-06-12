---
title: "UBUNTUSTUDIO 7 AMD 64--ADSL can use FTP but FIREFOX won't work"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by kzman on 2008-02-13
I used "sudo pppoeconf" and was able to set up for ADSL

I did "pon dsl-provider"

I tried FIREFOX but no success.

So I tried using FTP to a server at work.
FTP worked.

I tried FIREFOX again and it still won't work.

Is there anything that I can do to get FIREFOX to work?

My brother mentioned about having to install a driver to get his internet connection working.  I do not know what type of card the computer has.

I am sending this message from a Windows machine.

---

### Post by ashmew2 on 2008-02-15
How do you connect to the internet ? 
And have you tried giving any other browser ( Konqueror , Epiphany or any other) a try ?

---

### Post by jrharvey on 2008-02-15
YA? do you use wireless?

---

### Post by ashmew2 on 2008-02-15
I dont think he uses wireless because he's running "ADSL"

---

### Post by kzman on 2008-02-16
> **ashmew2 said:**
> How do you connect to the internet ? 
And have you tried giving any other browser ( Konqueror , Epiphany or any other) a try ?

I connect to the internet through an ADSL modem -- COMTREND.

As mentioned, I am able to establish an FTP connection and to connect.

I do not know that I have the other browsers that you mentioned.  I was able to get FIREFIX from the install cd.  

I cannot download to that computer from the internet because I don't have the ability to connect with firfox or it appears also from command line (except FTP).

My brother mentioned that I might need drivers for my ethernet connection.

But he has not been well lately and was not able to give more information.

How would I find what my computer has and what drivers I need?

I do recall just now that he also indicated that he had at one point installed a PCI lot etherneet card before he was able to get the pre-installed one on his computer working.  I think I will try that and let you know.

Thank you.

---

### Post by kzman on 2008-02-16
> **jrharvey said:**
> YA? do you use wireless?

I do not use wireless.

---

### Post by ashmew2 on 2008-02-17
Try opening up the terminal (Applications > Accessories > Terminal) , and type in there :
```

sudo apt-get update
```

If that works , do a 
```

sudo apt-get install epiphany
```

And post back what happened.

And by any chance , are you using a Static IP ? Like do you have to tell your computer to use the IP address "192.168.1.5" and Gateway "192.168.1.1" etc ?

---

