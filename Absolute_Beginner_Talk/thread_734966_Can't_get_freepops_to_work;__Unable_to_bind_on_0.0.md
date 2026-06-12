---
title: "Can't get freepops to work;  Unable to bind on 0.0.0.0:2000"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2008-03-25
Hi,

I have a hotmail of which i want to forward my messaged to my gmail account. I used izymail but that now says "Your registration has now expired."

So i downloaded freepops from [here]("http://cybertech.altervista.org/en/freepops.php") and installed it (including all those packages they say you need). 

When I now want to run freepops by simply typing "freepopsd" into it says "Unable to bind on 0.0.0.0:2000"

This doesn't tell me anything. I am not so well with command line etc. I normally just paste what it says.. :-?

Can anybody help me to get this working? I need to get rid of MS hotmail!

---

### Post by Black_Nautilus on 2008-03-25
Looks to me like its trying to use a loopback but its not responding 
 
if you have a firewall running i would turn it off then try running the program.
 
Also i looked at [this]("http://freepops.diludovico.it/forumdisplay.php?f=13") and saw an issue pertaining to hotmail that might have a few answers , hopefully this helps.

---

### Post by kramer65 on 2008-03-25
I don't know of any firewall running..

How would i know whether there is a firewall runing?

---

### Post by Black_Nautilus on 2008-03-26
For a firewall i am not for sure where to look but if you are running a default install and not purposly installing and running a firewall you probubly dont have one running. 

Another thing it could be is that if you have more than one network card and its pulling and ip from the wrong one since its getting the 0.0.0.0 so if you have an onboard wired and a wireless card you might want to disable the onboard in the BIOS.

---

