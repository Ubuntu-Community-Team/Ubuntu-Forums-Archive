---
title: "Best Wireless Cards"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by timmahhny on 2006-06-30
I am currently trying to get the Belkin FD56020 ver 2 to run but as with many, it will see the network but not connect.
 As I have spent countless hours pouring over posts, tutorials, and searching the internet for any type of information, I have finally broken down and am going to purchase a new card. 

 I do have a Linksy Wireless G version 3 but have not found any drivers for that, so my question is what is the best "out of the box" wireless G or b card that I can plug into the laptop.

Any help and suggestions are helpful.
Thank once again for everyones input.
Tim

---

### Post by kop316 on 2006-06-30
I would say a lucent WaveLAN/IEEE would be a good choice, as it worked for me right away. If you are willing to spend a bit of time however, I know that the Linksys speedbooster wireless device works under ndiswrapper.

Other then that I would say be aware of the Netgear WG511. THey say it works out of the box, but if it is v2, you probably have a lot of trouble with it.

---

### Post by richbarna on 2006-06-30
[QUOTE=timmahhny]I am currently trying to get the Belkin FD56020 ver 2 to run but as with many, it will see the network but not connect.
 As I have spent countless hours pouring over posts, tutorials, and searching the internet for any type of information, I have finally broken down and am going to purchase a new card. 

 I do have a Linksy Wireless G version 3 but have not found any drivers for that, so my question is what is the best "out of the box" wireless G or b card that I can plug into the laptop.

Any help and suggestions are helpful.
Thank once again for everyones input.
Tim[/QUOTE]

Have a look at my "sig" for MadWifi.
|
|
v

---

### Post by joshrobinson on 2006-06-30
linksys and d-link have worked for me in the past.. i have a pcmia linksys that works when i plug it in.. ndiswrapper is always something to try.. or madwifi like what was posted above me

---

### Post by timmahhny on 2006-06-30
I am still messing with the Belkin right now, as I just need to install the kde in order to run the wlassistant that I just downloaded. So if that doesn't work, then I will try the lucent WaveLan/IEEE as long as it is a PCMCIA.

 I do have a Linksys Wire-less G Model  WPC54G ver.3 and am running into the same problems as no real driver. 

 I  am going to start to learn how to compile this stuff so I can start to build drivers for these things.

Thank you much for your input. I am going to try to get some sleep as I have been up for over 30 hours trying to figure this thing out.
Tim

[QUOTE=kop316]I would say a lucent WaveLAN/IEEE would be a good choice, as it worked for me right away. If you are willing to spend a bit of time however, I know that the Linksys speedbooster wireless device works under ndiswrapper.

Other then that I would say be aware of the Netgear WG511. THey say it works out of the box, but if it is v2, you probably have a lot of trouble with it.[/QUOTE]

---

### Post by timmahhny on 2006-06-30
I just booked marked it for later on today. I need to try and get some sleep; I have been up too long and my brain is fried. I will try that and get back to you. 
Thank you very much for your input and quick reply to my question.
Tim

---

### Post by richbarna on 2006-06-30
Madwifi have Belkin :-
[http://madwifi.org/wiki/Compatibility#Belkin]("http://madwifi.org/wiki/Compatibility#Belkin")

---

### Post by oscar on 2006-06-30
My internal intel ipw2200 works out of the box as does my netgear rangemax wireless pci card.

---

### Post by xtacocorex on 2006-06-30
[QUOTE=kop316]Other then that I would say be aware of the Netgear WG511. THey say it works out of the box, but if it is v2, you probably have a lot of trouble with it.[/QUOTE]

The WG511's that are made in Taiwan work out of the box, but they are very hard to find nowadays. I have one and it works perfectly. 

I have read that the newer versions and the old ones made in China don't work. I think the old China ones might work with ndiswrapper, but I can't confirm this.

---

### Post by Kobalt on 2006-06-30
Hi in there,

I actually have a Linksys WPC54G ver.2, and it works like a charm with Dapper... and without Ndiswrapper. I admit, there's a bit of work to do with acx, but it's really nothing big, and the card is just working great. 

Thank you Lynksys ! 
Cheers !

---

### Post by timmahhny on 2006-07-02
Thanks to all who gave advice on the card.
I have tried everything so far and I believe that because I am a newbie to Linux, I am just missing something. 
What I have tried with both cards.

 NDISWRAPPER with both cards and failed.
 wlassistant,can't seem to get that to work.
 I have tried dapper, but am not sure if I am doing it right.
I have downloaded and installed the drivers that people say work, and they
probably do as I can see the network but still can't connect.
Wifi Radar which sees the network but can't connect.

 I am going to "give up" as I have been doing this now for about a week more or less with Mandriva and Ubuntu, and Red Hat going back three  weeks ago. I will continue to try but will attend the next monthly meeting next week and I am sure those guys will know what I am doing wrong.

 Unless, dare I ask, someone who reads this is on skype and doesn't mind trying to talk me through some of this. I realize that is a great deal to ask, but I am very much up to the top of my head and need a life line. 

 Thanks again to all and if I can't get one or both of these cards to work, I will try getting another one.

Tim

---

