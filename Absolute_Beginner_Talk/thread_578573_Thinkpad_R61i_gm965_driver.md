---
title: "Thinkpad R61i gm965 driver"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by obesus_puer on 2007-10-17
Hello I have just installed Gutsy 64bit on my Thinkpad R61i. Everything installed correctly excluding the sound. A few hours of googling led me to a guide to install the latest alsa driver. Sound is now working perfectly. My final issue (I hope) is that I cannot enable desktop effects. I assume I need to install the driver from Intel but I'm not really sure how.

I made it to this site.
[http://www.intellinuxgraphics.org/download.html]("http://www.intellinuxgraphics.org/download.html")

But I'm not sure what to do with it. Can anyone give me a step by step semi idiot proof guide to doing this?
Thanks.

Chip is an Intel GMA X3100 GM965

Edit: My Issue is VIDEO not audio.

---

### Post by LaRoza on 2007-10-17
I just got a ThinkPad R61i also, but have not tried to use sound so I can not offer specific advice, but I'll look into it.

By the way, have got the DVD drive working?

The site says the drivers should be in the repositories, so I would look there first.

---

### Post by obesus_puer on 2007-10-17
> **LaRoza said:**
> I just got a ThinkPad R61i also, but have not tried to use sound so I can not offer specific advice, but I'll look into it.

By the way, have got the DVD drive working?
Yes my DVD drive is working fine as far as i know. Mine is a CDRW/DVD combo. It red transformers movie fine I think i just need codecs. I have the sound working. The issue is now just video

---

### Post by cwhitehouse on 2007-10-17
Check this post, [http://thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Tribe_on_a_ThinkPad_R61](http://thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Tribe_on_a_ThinkPad_R61)

There is an audio script which may resolve your issue.

---

### Post by obesus_puer on 2007-10-17
> **cwhitehouse said:**
> Check this post, [http://thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Tribe_on_a_ThinkPad_R61](http://thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Tribe_on_a_ThinkPad_R61)

There is an audio script which may resolve your issue.

Thank you for the link but the issue is VIDEO not audio.:)

---

### Post by obesus_puer on 2007-10-17
bump

---

### Post by SebMKd on 2007-10-17
Planning on installing Gusty 64bits this weekend once released on Dell Laptop Latitude D630 (with Intel GM 965 / GMA X3100). 
I have no idea what to do with the "Git repository" on intellinuxgraphics.org as well. Even though, I would agree it seems to be the right place to get those GM965 drivers. 
So ... should I wait before installing? Or is it manageable to work without those Intel video drivers anyway? What are those not functioning "desktop effects"?

Seb

---

### Post by obesus_puer on 2007-10-17
> **SebMKd said:**
> Planning on installing Gusty 64bits this weekend once released on Dell Laptop Latitude D630 (with Intel GM 965 / GMA X3100). 
I have no idea what to do with the "Git repository" on intellinuxgraphics.org as well. Even though, I would agree it seems to be the right place to get those GM965 drivers. 
So ... should I wait before installing? Or is it manageable to work without those Intel video drivers anyway? What are those not functioning "desktop effects"?

Seb

Using the computer is perfectly fine. I just can't enable the eye candy like the cube. Its not deal breaking but that was one of the things that got me interested in linux again.

---

### Post by sasquatch74 on 2007-10-17
My apologies if you have already seen this, but [this]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Release_Candidate_on_a_ThinkPad_T61") post on ThinkWiki got my Desktop Effects working.  I have a r61 with the same chipset, but I have the 32 bit version installed, not the 64 bit.  I don't know if it makes a difference in this case, I hope it works for you!

---

### Post by obesus_puer on 2007-10-18
> **sasquatch74 said:**
> My apologies if you have already seen this, but [this]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Release_Candidate_on_a_ThinkPad_T61") post on ThinkWiki got my Desktop Effects working.  I have a r61 with the same chipset, but I have the 32 bit version installed, not the 64 bit.  I don't know if it makes a difference in this case, I hope it works for you!

WOW it worked!!!! Thank you so much. It seems to be a tad touchy in 64bit. Occationally switches back from having it enabled after running the script aside from that its running perfect.

---

