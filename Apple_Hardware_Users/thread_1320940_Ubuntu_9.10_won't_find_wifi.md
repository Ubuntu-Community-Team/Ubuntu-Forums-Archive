---
title: "Ubuntu 9.10 won't find wifi"
date: 2009-11-09
forum: Apple Hardware Users
---

### Post by eaglehacker on 2009-11-09
Hi,

I am really new to Ubuntu, but a long time user of Mac OSX. This past weekend, I successfully tried to dual boot Karmic Koala 32 bit onto my system. While at first everything seemed normal, I noticed that I wasn't connected to wifi, so I opened network preferences, but didn't find any wifi nearby although on my wifes mac right next to me had more than 10 networks, with 3 having "full bars" signal. I am confused on what I did wrong if anything and what I can do to fix it.

Cheers,
--Eaglehacker

---

### Post by jamesey on 2009-11-09
it's a really dumb and lame embarrassing issue. look here. I had to physically go find a network cable and hook it up to my wireless router. 

[http://ubuntuforums.org/showthread.php?t=1286763](http://ubuntuforums.org/showthread.php?t=1286763)

---

### Post by Geocron on 2009-11-09
[COLOR=Red]TRY THIS BEFORE ANY OTHER METHOD [/COLOR]
i have a broadcom wifi card 
i find that the wifi does not work with a fresh install EVEN if the card is RECOGNIZED 
to fix this this all i do is pug in a Ethernet cable (with internet on it) and up date
then go to the System>administration>Hardware drivers 
and activate the b43 driver (if it does not show b43 u probably don't have a broadcom)
then update again (by going to  System>administration>Update manager)
after that i can see wifi points and get on them 

[COLOR=Red]i recommend that you TRY THIS BEFORE ANY OTHER METHOD [/COLOR]

---

### Post by pcrussell50 on 2009-11-10
> **Geocron said:**
> [COLOR=Red]TRY THIS BEFORE ANY OTHER METHOD [/COLOR]
i have a broadcom wifi card 
i find that the wifi does not work with a fresh install EVEN if the card is RECOGNIZED 
to fix this this all i do is pug in a Ethernet cable (with internet on it) and up date
then go to the System>administration>Hardware drivers 
and activate the b43 driver (if it does not show b43 u probably don't have a broadcom)
then update again (by going to  System>administration>Update manager)
after that i can see wifi points and get on them 

[COLOR=Red]i recommend that you TRY THIS BEFORE ANY OTHER METHOD [/COLOR]

This procedure worked like a champ for jaunty on my MB3,1, and now it's worked like a champ for karmic on the same machine.  Thanks for the reminder!

Peter
Santa Barbara, CA

---

### Post by Zakariyya on 2009-11-11
> **Geocron said:**
> [COLOR=Red]TRY THIS BEFORE ANY OTHER METHOD [/COLOR]
i have a broadcom wifi card 
i find that the wifi does not work with a fresh install EVEN if the card is RECOGNIZED 
to fix this this all i do is pug in a Ethernet cable (with internet on it) and up date
then go to the System>administration>Hardware drivers 
and activate the b43 driver (if it does not show b43 u probably don't have a broadcom)
then update again (by going to  System>administration>Update manager)
after that i can see wifi points and get on them 

[COLOR=Red]i recommend that you TRY THIS BEFORE ANY OTHER METHOD [/COLOR]

Wow! I have been reading articles for hours today because I couldn't figure out how to get my wireless working. I'm new to Ubuntu and most of the stuff that I read had to do with stuff on the command line. I just happened to find this thread after what seemed to be endless googling. After following your simple and quick instructions... Presto! I am now surfing the net wirelessly with my iBook G4. Thank you Geocron!

---

### Post by pcrussell50 on 2009-11-11
IMHO, this procedure ought to be a "sticky".  back in July I had the same issue, and I was either ignored or barraged with well meaning folks asking for the outputs of certain terminal commands.  all the while, this procedure sat right under all of our noses. 

that said, I -think- and I could be wrong, that broadcom support only just began with jaunty. 

-Peter

---

### Post by WuIsMe on 2009-11-12
!support sticky
I stumbled upon this method after searching around for ages, with ndiswrapper, packages, the lot! Came to post solution but got beaten!

What I'd really like to know however,is if there's a purely command line method too. 
That way you could get wireless on Ubuntu Server without having to install the gui.

---

### Post by linuxopjemac on 2009-11-12
I would read this:

[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

---

