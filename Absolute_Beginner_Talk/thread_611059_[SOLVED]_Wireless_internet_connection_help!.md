---
title: "[SOLVED] Wireless internet connection help!"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by Nermin on 2007-11-12
Hi guys,

my first post:). Just installed Ubuntu 7.10:):):)

But...:S haven't got a clue...:(

I can't create a wireless internet connection, better to say, don't know how...:(

My card is AirLive Turbo-G, if you need to know anything else just ask.

Could someone help me??? Explain me what to do, and how? and i mean really step by step...

I read a few guides, but can't find a lot of things they want me to do and most are for earlier versions of Ubuntu. The images aren't up to date...

Any help is appreciated:) 

Thanks

---

### Post by poudin on 2007-11-12
if no native linux driver available...you  may be able to use WIN XP driver...only used as a last resort...
check the URL below and the other posts..the answer may be ndiswrapper for you.


ndiswrapper -i <location_of_your_driver>/<the_driver>.inf
ndiswrapper -l

it was pretty good for the HP pavillion 1000 we used it on...just had to make sure we had the right *.inf
for the laptop..we grabbed the XP version

we used lspci to confirm the model of the wireless network controller (ours was BG2200 Intel)


From this website
[http://www.linlap.com/wiki/Configuri...+Linux+drivers](http://www.linlap.com/wiki/Configuri...+Linux+drivers)

---

### Post by Nermin on 2007-11-12
ok, i think linux can find the drivers.

there is a wireless connection present on Networks

i check the box in front it, but it's not working...

and i can't add anything! at add/remove it says that it needs to reload the list.

I guess it needs an internet connection...

And today is my first day with linux, btw. proud of it:), so i don't really know what you said, and how to install the program you mentioned...
Can you be a bit more specific?:S

---

### Post by poudin on 2007-11-12
question...

are we taking about a laptop or a desktop..

and do u mean you see SSID broadcasts for Wireless networks but can't connect to them...need some more information

---

### Post by Nermin on 2007-11-13
desktop

i don't know how to connect... it goes without problems on windows xp, it finds the card automatically and i install drivers from a cd. Now, i would like to know did ubuntu take over these drivers, i have dual boot...
And i'm not sure what you are asking... I have an outdoor antene with which i connect to the one from the provider...

Please be patient... What else do you need to know?

---

### Post by Nermin on 2007-11-13
Not really sure what happened, but the connection works now:) it appeared out of nowhere:S

Thank you

---

