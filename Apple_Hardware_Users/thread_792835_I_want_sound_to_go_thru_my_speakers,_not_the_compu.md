---
title: "I want sound to go thru my speakers, not the computer's"
date: 2008-05-13
forum: Apple Hardware Users
---

### Post by Brightbelt on 2008-05-13
Hi,
I'm on Hardy 8.04 on a 24" intel iMac. I've got most everything set and audio works just fine coming through the computer's speakers....

However, I happen to have Bose computer speakers hooked up through the headphone jack so that in Mac OX S at least, sounds comes out through the Bose speakers and it's much higher quality as one might imagine. 

I can't seem to get the sound to go through my speakers in Ubuntu. I've played with different settings in the System/Preferences/Sound interface.... Maybe I haven't tried enough settings.

I appreciate anyone who could help me gain some clarity on this matter. Many Thanks, Frank B.

---

### Post by cyberdork33 on 2008-05-13
> **Brightbelt said:**
> Hi,
I'm on Hardy 8.04 on a 24" intel iMac. I've got most everything set and audio works just fine coming through the computer's speakers....

However, I happen to have Bose computer speakers hooked up through the headphone jack so that in Mac OX S at least, sounds comes out through the Bose speakers and it's much higher quality as one might imagine. 

I can't seem to get the sound to go through my speakers in Ubuntu. I've played with different settings in the System/Preferences/Sound interface.... Maybe I haven't tried enough settings.

I appreciate anyone who could help me gain some clarity on this matter. Many Thanks, Frank B. I think a patch was needed for this on your iMac...
search the archives for posts by a user named nicfagn.

---

### Post by Brightbelt on 2008-05-13
Thanks Cyber...I did try a fix in the archives that involved installing a newer version of libasound2, but I can't say it was authored by your guy. 

Maybe your fellow's fix will be better. Many Thanks,
Frank B.

---

### Post by Brightbelt on 2008-05-13
I installed the recent Alsa firmware in Synaptic - reason being that looking at the date of Nicfagn's post, it was April of '07 and I could not find his number of Alsa in Synaptic; it seemed old.

So I have a Gui of Alsa and btw, it helps to know the tip for working the new iMac keyboard in Hardy: hit F6 twice or do what it takes to disable the numberpad.  

The channels with my Bose computer speakers I think each have a white dot, one over each side L/R. I don't know if that means they won't work or what. 

If I click the white dot, it turns red but it doesn't change anything,,,Remember my issue: My computer audio WORKS FINE but I have Bose speakers plugged in to the headphone jack and they do not work at all in Hardy. They play perfectly in Mac OS X.

As always, Many Thanks for your follow up assistance,...Frank B.

---

### Post by cyberdork33 on 2008-05-13
Yea the problem is that t doesn't recognize that there is something plugged into the jack, and if it does, it doesn't turn off the system speakers... or something like that. Either way, I am pretty sure you need a  patch. You might try to PM nicfagn. He has made several patches before.

---

### Post by Brightbelt on 2008-05-14
Thanks Cyber!!

---

### Post by acelin on 2008-05-14
> **Brightbelt said:**
> Thanks Cyber!!

Hey make sure to post if you got this working, as I am looking to buy a new iMac.

---

### Post by Brightbelt on 2008-05-14
As of yet, I still haven't gotten the external speakers working, I looked into Nicfahn's posts but so far I haven't achieved success. 

I'll give a shout if I do,....Thanks, Frank B.

---

### Post by NightwishFan on 2008-05-15
Perhaps play around in alsa mixer as well, although I am sure you have done that.

---

### Post by Brightbelt on 2008-05-15
Yes, Nightwishfan, I have played with the Alsa Gui. Right now I'm on the road with my Macbook Air and not at home with the iMac, so I can't troubleshoot this directly right now (although ideas are always welcomed and can be applied later). 

The channel which I think showed the speakers had 2 dots over it (one each over L/R) and I could click them and they turned to red but nothing came of it. I couldn't get the volume for that channel to respond either. 

Cyber suggested that a patch here is most likely needed and that Ubuntu is somehow not detecting the speaker jack that is plugged in - I tend to think he's right on that. He suggested to check out Nicfagn's posts on this issue. 

And Nicfagn maybe has the answer - just be careful: I started to apply his suggestions only to see that his posts were pretty dated (April 2007) and that newer alsa packages were available. 

Many Thanks, Frank B.

---

### Post by cyberdork33 on 2008-05-15
> **Brightbelt said:**
> And Nicfagn maybe has the answer - just be careful: I started to apply his suggestions only to see that his posts were pretty dated (April 2007) and that newer alsa packages were available.
yea that is true.. you could just try to compile a newer version of ALSA if you haven't already.

---

