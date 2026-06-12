---
title: "Cant get Sound Juicer to encode mp3 so trying to use Grip"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by madds007 on 2007-04-01
Hi all

After a frustrating evening last night trying to get Sound juicer to rip mp3, using all advice of forums, I thought it try Grip, but now i'm having trouble config'ing it asks for encoder path with i put in as the suggested 

/usr/bin/lame but it doesnt work , where can i find out where the lame files have been put?

also it defaults to the cdrw id prefer to use the DVD drive and thus when it plays a cd there is no sound

Oh in Rhythumbox when i try to play a mp3 ripped via sound juicer i get a MIME error all mp3 files ripped on my mac and saved on my ex USB HD work fine



Help please if poss



Thanks guys


Andy

---

### Post by Gina on 2007-04-01
I think you are missing the MP3 codec - try installing **w32codecs** from Synaptic.  When I was setting up Ubuntu I installed all sorts of extra bits and have it working but not sure just wich extra bit did the trick .

Go into **Synaptic Packet Manager**, **Search** for **w32codecs** and tick the install box, **Apply,**  and follow the instructions.

---

### Post by kinematic on 2007-04-01
Lame is in the multiverse repository.
once you have it installed you can use [this](http://nostatic.org/grip/doc/ar01s04.html#mp3config) page to cinfigure grip.....especially take a look at the % switches at the bottom.
for the best setting for Lame take a look at [this](http://wiki.hydrogenaudio.org/index.php?title=LAME#Recommended_Encoder_Settings) page.

---

### Post by stchman on 2007-04-10
> **madds007 said:**
> Hi all

After a frustrating evening last night trying to get Sound juicer to rip mp3, using all advice of forums, I thought it try Grip, but now i'm having trouble config'ing it asks for encoder path with i put in as the suggested 

/usr/bin/lame but it doesnt work , where can i find out where the lame files have been put?

also it defaults to the cdrw id prefer to use the DVD drive and thus when it plays a cd there is no sound

Oh in Rhythumbox when i try to play a mp3 ripped via sound juicer i get a MIME error all mp3 files ripped on my mac and saved on my ex USB HD work fine



Help please if poss



Thanks guys


Andy

I have a procedure to allow Juicer to rip CDs to MP3s.  [http://www.stchman.com](http://www.stchman.com)

Works like a charm.

---

