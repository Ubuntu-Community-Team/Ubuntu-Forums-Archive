---
title: "Full Palm Functionality"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2006-05-30
I use a Palm T3 and can get it to synch Calendar, Contacts, ToDo...basic stuff but I don't see how to use more advanced functions like adding photos, mp3, documents (open office type or pdf) via gpilot.  Anyone know or have a link?  (this is one reason I keep WinXP available)
Thanks.

---

### Post by popkid on 2006-05-30
[QUOTE=flyingsolo]I use a Palm T3 and can get it to synch Calendar, Contacts, ToDo...basic stuff but I don't see how to use more advanced functions like adding photos, mp3, documents (open office type or pdf) via gpilot.  Anyone know or have a link?  (this is one reason I keep WinXP available)
Thanks.[/QUOTE]

Hi, strictly this isn't an answer to your question, but it may be an alternative solution. I have a tungsten T2 and have a program on it called 'card export' available through palmgear (from memory it costs about $10) normally I wouldn't pay for palm software as there is usually a free alternative. But this was so indispensable to me that I had to buy it (no I'm not related to the seller!) All it does is allow your palm to work as a USB pen drive (basically works like a card reader for your SD or MMC card) I got it because I use a SatNav program on my T2 and transferring the 200MB+ maps across using hotsync took hours, by using the palm as a card reader they go across in minutes.

pK

EDIT: This would be no use to you if you store pictures/documents in palm memory... only allows you to see the card contents via USB...

---

### Post by flyingsolo on 2006-05-30
Is this 'card export' a windows or linux application?

---

### Post by popkid on 2006-05-30
[QUOTE=flyingsolo]Is this 'card export' a windows or linux application?[/QUOTE]

Neither, its a palm application, you just launch the app on your palm, press an on screen button, and hey presto, your palm appears as an external storage device (on either windows or linux)

Check out the palmgear site for it

[http://www.palmgear.com/index.cfm?fuseaction=software.showsoftware&PartnerREF=&siteid=1&prodID=62947]("http://www.palmgear.com/index.cfm?fuseaction=software.showsoftware&PartnerREF=&siteid=1&prodID=62947")

pK

---

### Post by Sgood1971 on 2006-05-30
popkid is right, this is a great app. I couldn't use my Tungsten|C without it.

---

### Post by Carnwaj on 2006-05-30
Popkid - 

Slightly off topic but you mentioned satnav with a Tungsten T2. What is your system. I'm looking for a cheap way into satnav and the T2s are very cheap second hand.

Thanks,

John

Happy for the post to be removed if it's going off topic.

---

### Post by popkid on 2006-05-30
I've got a navman gps500 cradle (you still see them on e-bay occasionally, they are usually advertised as being compatible with m series palms) the software that comes with them is useless though (doesn't even work on tungstens) so I have via michelin mapping software, this is good, but all in you are probably still looking at the thick end of £200 minimum for the cradle plus software (plus the software requires windows to get it onto your palm which could be a problem if ubuntu is your only os) you can buy a brand new palm gps setup including palm tungsten e or 5 I think, + cradle and software for not too much more and tom toms and stuff are cheaper than that...

pK

---

### Post by Carnwaj on 2006-05-30
Thanks pK

As I thought about £200 is the cheapest.

Cheers

---

### Post by stevieb on 2006-08-03
I tried this with a Tungsten E.  It works on XP but not on Dapper. I've done the MMC update as suggested.  I get a message on the Palm that reads ```
"SlotCardRead:(Sys0501)"
``` after connecting.  The drive shows up in the list on the desktop, but won't mount.

Any ideas?
-steve

---

### Post by popkid on 2006-08-03
Hi... not sure, works just fine with my T2, is the MMC update for Cardexport 2?

Does the message appear only when you hit connect?

The version of card export I'm on is 2.00.579 (not updated it since installation)

pK

---

### Post by stevieb on 2006-08-03
After I hit connect, there's a pause of a few seconds, then I can see on the Palm that the "read" light is on, then the error shows up.  on the ubuntu desktop, the palm shows up under Computer>File Browser as "Softick Card Export."  Double-clicking this brings up "Unable to mount the volume.  There is probably no media in the device." (this is not the case, however).  Clicking "show more details" reveals:
```

mount: /dev/sda is not a valid block device
mount: /dev/sda is not a valid block device
error: could not execute pmount
```

Attempting to drag a file over to the Softick yields the following "Error 'Invalid URI' while copying"

side question: if I change the language to UK english, would it say "Error 'Invalid URI' *whilst* copying."? :-k 

-steve

---

### Post by popkid on 2006-08-03
Hmmm... just retried this (haven't used it for a while with ubuntu as cradle is attached to my windows desktop machine) and I now get nothing apart from a lock up on the palm side (needs soft reset to recover) my palm doesn't show up in ubuntu at all... (so you are actually ahead of me there) tried another usb key I had lying around and that works fine so doesn't seem to be a usb issue with my machine. And the card export definitely works with XP, so there is obviously a compatibility problem. This used to work so something has changed somewhere.

Sorry can't be more help.

pK

---

### Post by popkid on 2006-08-03
Had a hunt around and someone else has reported the same issue as you at the softick forums... [See Here]("http://softick-forum.com/viewtopic.php?t=35&sid=a100bf227592aedf78ece31e24932bb4")

My problem is unrelated I think, I am getting completely different error messages, (usb 1-1: device descriptor read/64, error -110) in dmesg

pK

---

### Post by popkid on 2006-08-03
Ok... I've just updated my ancient version of Card Export 2 to the latest 2.23 release, and it now works perfectly again with Dapper and XP...

Reading their FAQ however, seems they believe there to be a general problem with Tungsten E slot driver?

pK

---

### Post by stevieb on 2006-08-04
thanks for the help; but nothing has worked as of yet.  i checked out the softick forum, and even translated the russian in babelfish, but these did not help.

i saw the thing about the tungsten E problem, but it works ok in windows.

what's the HAL thing all about?  that sounds like the way to go.

thanks again,
-steve

---

