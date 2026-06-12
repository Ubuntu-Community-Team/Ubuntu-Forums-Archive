---
title: "talk about lost"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by rebel17761 on 2008-04-16
O.K. let me start out by saying I'll take the title of duffus when it comes to puters with unbuntu,,I have never run a linux program EVER..
 That being said, I have managed to install it on an empty HD and turn it on,lol.
 Here's the deal, I want to go online and update the programs and do all that, online stuff people do, problem is I can't seem to get online at all.
 I have tried a pctel modem and a dsl modem but I dunno how to set up the connection,it's not like setting up an XP connection,no wizard duh...
 Anyone wanna take a minute to explain something like this to a newb??:confused:

---

### Post by jameswillmer on 2008-04-16
post the manufacturer name and model name for your dsl modem

also indicate if dsl works in windows

post approx specs for your computer

say whether the dsl modem is connected to your comp by ethernet (good) or USB (harder)

people will then know how to help (learn to post better q next time=friendly hint for the future)

JW

---

### Post by rebel17761 on 2008-04-16
simple enough yes the dsl modem works in windows, it is a westel "wirespeed" running at 10 mbps
 I have it running to an ethernet card 
 The puter is a 1.6 gig pent 4 running 512 mg of mem, also the ethernet card is a pci slot (like it matters,but hey)
 the modem I tried to set up (for dial up, just to see) is a pctel pci card..
 Did I forget anything??

---

### Post by prshah on 2008-04-16
> **rebel17761 said:**
> 
 I have tried a pctel modem and a dsl modem but I dunno how to set up the connection,it's not like setting up an XP connection,no wizard duh...
 Anyone wanna take a minute to explain something like this to a newb??:confused:

OK assuming that you are posting from Windows now; Open Start->Run, then give the command ```
ipconfig /all
```, and copy and paste the results.

Then type ```
start devmgmt.msc
```, then follow instructions from [http://support.microsoft.com/default.aspx?scid=kb;en-us;308579](http://support.microsoft.com/default.aspx?scid=kb;en-us;308579) on how to print device information and system summary to a file. Then attach that file here.

This information will get us started on your system.

(Aside to spectators; really missing "lspci")

---

### Post by rebel17761 on 2008-04-16
different puter,,the other puter has 2 hd's 1 has xp one has untuntu

---

### Post by prshah on 2008-04-17
> **rebel17761 said:**
> different puter,,the other puter has 2 hd's 1 has xp one has untuntu

On that other computer, the output of lspci will be helpful; do```

lspci > devices.txt

```

Then copy the "devices.txt" file to your XP drive, and post it here, please.

---

### Post by rebel17761 on 2008-04-18
ok I wasn't clear, in order to run xp I have to unplug one hd and plug in the other,,they are incompatible and to plug them both in at once developes hardware issues,indevidually they work fine, so what you want me to do is plug in the hd with windows on it then carry on the comand prompt above?,Sorry if this is a pain but I said "duffus",,lol

---

### Post by rebel17761 on 2008-04-25
I guess I cernfuzzed him an he quit me, any one else got any ideas? I did find my root comand box lol

---

