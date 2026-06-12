---
title: "[SOLVED] No Sound... at all"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by TSRep13 on 2008-01-22
So I am about at N00b as it gets here.  I can't seem to figure out how to get the sound to work on my freshly installed Xubuntu 7.10 system.

I am doing one thing abnormal and I didn't know if it would be the issue, or if there is something else.  I am using my Insignia NS-LCD26 TV as my monitor/speakers.  I have used it in the past on a Windows XP system and it worked fine.

Any help here would be appreciated.  Thanks

---

### Post by forestpixie on 2008-01-22
might be quite simple - have you made sure all the ouputs are up and not muted, particularly PCM, try using the terminal

```
alsamixer
```

also if it's a creative sound card I know that there can be an analogue/digital switch, double click the vol icon - see if there any switches

to find out the card

```
lspci |grep Multimedia
```

---

### Post by TSRep13 on 2008-01-22
alsamixer netted this:

 Card: SBLive! Value [CT4780]                                                 &#9474;
&#9474; Chip: TriTech TR28602                                                        &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=-9.00, -9.00]                                      

Everything seemed to be hunky dory there :-\  And as for the creatice sound card, IDK what kind of card I have in there.  It is a second hand Dell Dimension 8200 that my buddy gave to me just a few days ago.  I haven't even cracked teh case on it yet to see the guts.

Does that give you any more clues as to what the problem could be?

---

### Post by forestpixie on 2008-01-22
creative it is - see if there is a switch - as I said try dbl clicking the vol icon - if there's a switch tab - open it if there's a analog/digital option - disable it 

if still a problem - have a look through some of these

[http://www.uboontu.com/results.htm?cof=FORID:11&cx=002072379199720138921:9m-bgfzutzq&q=sb+live+value#1340](http://www.uboontu.com/results.htm?cof=FORID:11&cx=002072379199720138921:9m-bgfzutzq&q=sb+live+value#1340)

---

### Post by TSRep13 on 2008-01-22
Your amazing.  Thank you!  It is fascinating how the simple things can be the best answers.  I have sound now and it is working great.  Thank you again.

---

### Post by rosegarden78 on 2008-01-22
I use xfce4-mixer package for my Xubuntu because it responds to the Fn-up and Fn-down and looks nice in the xfce system dock.  Are you sure it's not on mute?  Did you get the xfce4-mixer package from Synaptic because that's what I had to do.

---

