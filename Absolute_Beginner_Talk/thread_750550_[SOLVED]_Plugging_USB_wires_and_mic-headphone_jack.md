---
title: "[SOLVED] Plugging USB wires and mic-headphone jack wires to the motherboard"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by hanzj on 2008-04-09
Plugging USB wires and [mic-headphone jacks wires] to the motherboard.

Hello, I have a desktop computer. There are several 6 USB ports on the back. They seem to work just fine. There are sound ports (round sound jacks) on the back, too. And they seem to work fine.

  But, on the front of the computer-box,  there are also 2 USB ports and  there are sound-in and sound-out jacks that I would like to use. (See attached pics). I opened up the computer's casing and found that the wires from the front are not connected to the motherboard.   

I have taken several pictures of the motherboard. (See attached pics)

There are 3 bundles of wires that are coming from the front of the computer. (See attached pics) The 3 bundles are:


**Bundle 1**)
L-OUT
R-OUT
GROUND
MIC-IN
R-RET
L-RET
MIC-POWER

-------------
[B]
Bundle 2[/B])

UCC1
USB1-
USB1+

UCC2
USB2-
USB2+

(1)GROUND
(2)GROUND



[B]---------

Bundle 3[/B] 

TPA-
TPA+
TPB-
TPB+
SHIELD
UG
UG
UP
UP

(I think this bundle is for the "firewire" port. I don't need firewire so I don't need to connect this.)


--------------

Could someone guide me in connecting the "sound-wires" and the "usb-wires" to the motherboard? Does my motherboard still have some space/ports to accomodate these wires?

If you need some more pictures, or pictures of a different angle, please let me know.

More relevant pics in posts below.


Thank you.

---

### Post by hanzj on 2008-04-09
More pics in this post.

---

### Post by hanzj on 2008-04-09
Even more pics in this 3rd post.

Thank you for your help.

---

### Post by hanzj on 2008-04-10
bump

---

### Post by AndrewEsther on 2008-04-10
hey hanz :-) I will try to help you out as best I can, but first let me say that, as frustrating as this must be for you, it's not system critical, and it's polite to at least wait 24 hours before bumping your own thread. (not nagging, just throwing that out there)

okay, well it looks like you've got a pretty basic problem. there are usually only very few spots that these jacks can fit in to your motherboard. first, let's start by getting a picture that's a little more close-up of the general area around your pci slots (**making sure the camera is focused** is the key here, I'm trying to read some fine print on your motherboard) and if you can, follow the wires that come from your power switch and snap me a picture of where those wires (with the same sort of jacks only smaller) plug into your mobo. also, see if there is a sound-control wire running from the back of your cdrom drive, and if there is, does it plug into your motherboard or into a pci card? also, for the sake of my poor eyes, and so I can get a general sense of where I'm at on this motherboard, could you get a picture that shows which way the motherboard is oriented relative to the case?

if you have any questions about anything I've said that's confusing (or if I'm using terminology that doesn't make sense to you) let me know

---

### Post by hanzj on 2008-04-10
hey andrew 8-). I'll wait 24 hours next time before bumping my own thread. Sorry about that. Didn't mean to be impolite.

> 
also, for the sake of my poor eyes, and so I can get a general sense of where I'm at on this motherboard, could you get a picture that shows which way the motherboard is oriented relative to the case?All the pics that have been posted in the first 3 posts in this thread are in the correct orientation. This means that the "bottom" of every pic is really "lower".You can see in some pics ([http://ubuntuforums.org/attachment.php?attachmentid=65446&d=1207775126](http://ubuntuforums.org/attachment.php?attachmentid=65446&d=1207775126) and [http://ubuntuforums.org/attachment.php?attachmentid=65447&d=1207775197](http://ubuntuforums.org/attachment.php?attachmentid=65447&d=1207775197)) the case's wheels on the carpeted floor. In these 2 pics (and maybe others), you will find the words "Antec" and "LanParty" upside down. This is still the right-side up. 8-)


I don't quite understand what perspectives you want a close-up and/or crisper shot of. So maybe if you can download a few and using gimp, make a red circle in those desired areas and re-upload the edited pics.
Would this be okay with you? Thanks.

---

### Post by Junglizer on 2008-04-10
Do you have the manual for the motherboard? It should list where the connections are and give the correct pin layout. If not can you post what make/model the board is? We can probably find an online pdf of the manual.

---

### Post by dnairb on 2008-04-10
On the motherboard, the 2 yellow pin-blocks by the battery at top **left** are USB headers.
The second picture of your first post shows a block with 9 holes and one blocked out - that is a USB connector. (The blocked hole is to ensure that it is connected the correct way) Each header provides 2 USB ports.

---

### Post by hanzj on 2008-04-10
Sorry, I have no manual for motherboard. As can be seen in [http://ubuntuforums.org/attachment.php?attachmentid=65447&d=1207775197](http://ubuntuforums.org/attachment.php?attachmentid=65447&d=1207775197), this is an NF4 LanParty.
I am not sure which in the NF4 LanParty series my motherboard is, but I found a page with some pdf manuals for the series.

[http://www.dfi.com.tw/Support/Download/manual_download_us.jsp?PRODUCT_ID=3449&CATEGORY_TYPE=LP&SITE=NA](http://www.dfi.com.tw/Support/Download/manual_download_us.jsp?PRODUCT_ID=3449&CATEGORY_TYPE=LP&SITE=NA)

One specific manual link is: [http://www.dfi.com.tw/Upload/Manual/847505314.pdf](http://www.dfi.com.tw/Upload/Manual/847505314.pdf)


Thank you.

---

### Post by hanzj on 2008-04-10
dnairb,
ok. I see the 2 yellow rectangles of 9 pin (2 rows by 4 columns) on the motherboard. I can connect the USB wire to that. But what about the other "wires" in the USB-Bundle ("Bundle 2" in First Post on this thread)?

Here they are again:
**Bundle 2**)

UCC1
USB1-
USB1+

UCC2
USB2-
USB2+

(1)GROUND
(2)GROUND


-------------

Please see 3rd pic in 1st post and 2nd pic in 2nd post.

Thanks.

---

### Post by heartburnkid on 2008-04-10
Looking at that manual, it looks like the front ports are supported through an optional add-in board (a Karajan board?).  If you don't have that, your front sound ports aren't going to be supported.

Your USB ports should be easy to hook up, though.  Look at Page 12 of the manual; that will show you where to plug them in.

---

### Post by heartburnkid on 2008-04-10
OK, to get more detailed, if we assume that your connector looks like this:

```

  X X X X
X X X X X
```

Then you should plug in your connectors like this:

```

  GROUND1 USB1+ USB1- VCC1
X GROUND2 USB2+ USB2- VCC2

```

Where X represents a bare pin.

Make sense?

---

### Post by hanzj on 2008-04-10
heartburnkid, i don't know what you're saying about the front-sound ports issue.

---

### Post by hanzj on 2008-04-10
ok. i think that makes sense, but if we do your directions, what do we do with the one thing with 2 x 4?
Bundle 2 all together has more than 9 holes.

---

### Post by heartburnkid on 2008-04-10
That's for your front sound ports, which as I mentioned before, your motherboard isn't going to support without an add-in board.

---

### Post by hanzj on 2008-04-11
heartburnkid, thanks for clarifying on the soundport issue. What about the usb port issue? (pls see [http://ubuntuforums.org/showpost.php?p=4691275&postcount=14](http://ubuntuforums.org/showpost.php?p=4691275&postcount=14))

---

### Post by heartburnkid on 2008-04-14
Bundle 2 has 8 wires, according to what you posted before.  The 8 wires correspond to 8 of the 9 pins in exactly the manner I posted before.

If there are more than 2 front USB ports, and you have similar sets of wires labeled USB3, USB4, etc., those are for the additional USB ports, and should be connected to the other USB header on your motherboard in exactly the same manner.

---

