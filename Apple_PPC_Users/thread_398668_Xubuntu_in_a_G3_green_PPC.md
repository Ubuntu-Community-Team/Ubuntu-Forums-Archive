---
title: "Xubuntu in a G3 green PPC"
date: 2007-04-01
forum: Apple PPC Users
---

### Post by McHunuter on 2007-04-01
Hi... 

I realize that my power PC wasn't power enough to run the traditional xubuntu, so I downloaded the Alternate version...
 Burn the CD but when I try to boot form the cd presing "c" the mac doesn't take it... 

i don't want it to dual boot, i just want to make only linux boot...

Any help??

---

### Post by DaDave on 2007-04-01
I had the same problem with the Desktop CD so I used Nortons Wipe Disk and started with a clean drive. After that it booted fine from the CD. Of course, that's only good if you want a Xubuntu only computer :lolflag:

---

### Post by ssam on 2007-04-01
a common mistake is to but the iso file on the cd rather than use it as an image for the cd. there are instructions at
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

another thing that you could try is resetting the PRAM see
[http://docs.info.apple.com/article.html?artnum=2238](http://docs.info.apple.com/article.html?artnum=2238)

---

### Post by lcafiero on 2007-04-01
I'm relatively new to Xubuntu, so what I say is just my experience and not to be taken with any authority (although I do know my way around Macs). 

I'm not sure what you mean by a G3 green PPC -- a Lime iMac? a Blue and White G3 tower (which looks kind of green)? -- but in the case of the iMac, I'm running Xubuntu (only) on an Indigo G3 iMac with no problems.

I wiped the disk first (as suggested in another post) and then installed Xubuntu choosing the partitioning option to reformat the disk completely (or words to that effect) which went pretty quickly. You don't have to wipe the disk first, but for some reason beyond my knowledge, it seems to help (anyone want to help me out as to why that might be?).

Xubuntu works great on iMacs, and I recommend it highly to anyone with an iMac wanting to make the change to GNU/Linux. Bear in mind that OS X Leopard (10.5?) and later is slated NOT to work on G3 iMacs, so the boat from Cupertino is leaving without us -- all the more reason for using Xubuntu!

---

### Post by McHunuter on 2007-04-01
> **lcafiero said:**
> 
I'm not sure what you mean by a G3 green PPC -- a Lime iMac? a Blue and White G3 tower (which looks kind of green)? -- but in the case of the iMac, I'm running Xubuntu (only) on an Indigo G3 iMac with no problems.



It's green, men only see 16 colors..... Lime is a Fruit... sorry :lolflag: 


> **ssam said:**
> a common mistake is to but the iso file on the cd rather than use it as an image for the cd. there are instructions at
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

another thing that you could try is resetting the PRAM see
[http://docs.info.apple.com/article.html?artnum=2238](http://docs.info.apple.com/article.html?artnum=2238)

I burnt the image not the ISO.. thats no problem... 

I've with the second trick, but it still doesn't work, I read a somewhere that it may be better to burn the image veeeery slooooowww... i'm not sure.. i'll try..


Thanks to every one... waiting for more help....:)

---

### Post by lcafiero on 2007-04-02
Well, I guess you showed me, McHunuter.

Anyone who knows anything about Macs knows that iMacs came in colors described mostly in fruit-oriented colors -- lime, tangerine, strawberry as opposed to green, orange and red -- and to describe your machine as a "G3 green PPC" doesn't really give people who want to help you much to work with.

Hope you find out what you need to know.

---

### Post by pxwpxw on 2007-04-02
If you get into Open Firmware (Command Option o f  at startup )
```

0> boot cd:,install\:tbxi

```
Does it on an ibookG4,  just tried for Alternate ubuntu ppc CD.
I dont now if the open firmware version on that imac will work, cant do any harm.

---

### Post by ssam on 2007-04-02
the next thing to check is that it downloaded ok. the best method is to calculate the md5sum. there seems to be something called md5app for mac os x.

this will give you a long string of numbers and letters. compare this to the md5sum listed where you downloaded the iso file. if there is a difference then the download failed.

---

