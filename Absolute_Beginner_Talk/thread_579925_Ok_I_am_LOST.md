---
title: "Ok I am LOST"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by wyattsmoma on 2007-10-18
Ok I attempted to post this once but it was so screwed up I am just re writing the whole thing. Anyways, I am on an HP laptop that has wireless capabilities built in, and therefore have clue as to what card etc. i am using in it. I also have a belkin wireless g router that the internet is usually detected from. I have tried everythign i can think of and most the suggestions given to me by the site ( the ones I even remotly understood at least) I am truely hoping there is someone out there who can help walk me through this process before I give up and revert back to Windows... Whih I hate by the way. Please if anyone can help me out let me know!

---

### Post by overdrank on 2007-10-18
> **wyattsmoma said:**
> I have to say wow i am glad i put this on my lap top not my main computer to begin with... but still... I need my Internet!!! P laptop with wireless built in. Therfore No clue what card it is, So i dont even know if it is compatible ( should be though right?) then I have a belkin wireless router. I dont even know where to begin I have tried alot and am concerned that I am going to cause more dammage than help. Is there someone online who can walk me through this? Currently I have the router plugged into this computer instead of the desktop so I could make sure the internet worked at all. So Yeah... anyone really good at this and wanna walk the NOOB through?

Hi and welcome, please post the output of the command ```
lspci
``` 
In the terminal located under applications, accessories, terminal and this will identify your hardware and we may be able to help.

---

### Post by Technoviking on 2007-10-18
Goto System-> Administration -> Restricted Driver Manager and see if your wireless card needs a driver that is not included in the Ubuntu kernel by default.

---

### Post by wyattsmoma on 2007-10-19
Ok theres ALOT in there but what i think is usefull is 
network controller: Intel Corporation Dell Wireless 1390 WLAN Mini P-I Card ( rev 01)

and

Ethernet Controller: Intel Corporation Pro/100 VE Netwrok Connection ( RV02)

Dont know if you need anything else to help me... I am still completly lost... let me know.

---

