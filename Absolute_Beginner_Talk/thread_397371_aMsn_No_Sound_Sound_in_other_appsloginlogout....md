---
title: "aMsn No Sound? Sound in other apps/login/logout..."
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by keef247 on 2007-03-30
basically xmms and other media players,wine etc, when i login/out sound all works.
BUT with amsn...i hear nothing... what do i do to resolve this?
does amsn have an audio conversation option? mic chat you know?
cheers
used:aplay $sound but its quite quiet... any way to turn it up or an alternative?
FIXED!

---

### Post by psynyd on 2007-04-15
How'd u fix it?

---

### Post by hackyou on 2007-04-28
I'd like to know how did you fix it too

---

### Post by Devlin67 on 2007-05-02
If you go into Accounts/Preference/Others and then go to "sound server" and put "aplace $sound" (without quotations) there and then save and logout/exit and restart, you should then have sound. I worked for me on my Acer 5102WLMI. Hope it works for you guys too.

---

### Post by amr2205 on 2007-05-08
Nop, it didn't worked for me... is "aplace" a program or where can I get it?

---

### Post by wolfsta on 2007-06-01
aplay $sound 

think last person made a typo :)
and you should be away :)

Wolfy

---

### Post by mooha on 2007-07-20
I went to Account/Preferences/Others  in the sound server section I selected the first one which is Use the Snack library (Tcl internal). Loged Out & Quit Login back again ... and every thing worked fine.

Good Luck

---

### Post by LuisC-SM on 2007-08-22
> **mooha said:**
> I went to Account/Preferences/Others  in the sound server section I selected the first one which is Use the Snack library (Tcl internal). Loged Out & Quit Login back again ... and every thing worked fine.

Good Luck

In my case it always fails to load the snack library, which is the one that u need for voice conference.

If anyone knows how to fix this issue, I'll really appreciat it

TIA and Kind Regards

Luis

---

### Post by MaiPsy on 2007-08-24
> **LuisC-SM said:**
> In my case it always fails to load the snack library, which is the one that u need for voice conference.

If anyone knows how to fix this issue, I'll really appreciat it

TIA and Kind Regards

Luis

I think that you don't have snack installed so use the Synaptic Package Manager (if you don't have it install with Adept Manager) to find and install the package libsnack2. Then go to amsn and Account---->Preferences---->Sound Server----> use the snack library

---

### Post by LuisC-SM on 2007-08-24
> **MaiPsy said:**
> I think that you don't have snack installed so use the Synaptic Package Manager (if you don't have it install with Adept Manager) to find and install the package libsnack2. Then go to amsn and Account---->Preferences---->Sound Server----> use the snack library

Thanks so much for your reply.

I installed libsnack2 and still is doing exactly the same thing... probabily there shuld be some extra configuration with libsnack but I'm really an ingnorant at this point.

Thanks in advance and Kind Regards

Luis

---

### Post by Joeb454 on 2007-09-05
changing the setting from "play $sound" to "aplay $sound" (without quotes) worked for me.

---

### Post by LuisC-SM on 2007-09-05
> **Joeb454 said:**
> changing the setting from "play $sound" to "aplay $sound" (without quotes) worked for me.

Tnx a lot.

That did not worked for me. However, I still needed one more library I can't recall right now to solve this issue. 

I've seen that this issue is present when using tcl/tk 8.5xx, using 8.4 has no single problems with sound but you loose nicer fonts. So it becomes a matter of "taste", you can choose between having nicer fonts OR having sound. At least in my case.

Kind Regards

Luis.

PS. As soon as I remember which library I installed, I' update this post with its name

---

### Post by quinnten83 on 2007-09-05
WOW, 
I encountered this a coule of days ago, when my aMSN suddenly stopped playing sound (i thought at first it was because i installed akregator).
changing play $sound to aplay $sound worked instantly. I didn even have to log out.
How come this changed??

---

### Post by LuisC-SM on 2007-09-05
> **quinnten83 said:**
> WOW, 
I encountered this a coule of days ago, when my aMSN suddenly stopped playing sound (i thought at first it was because i installed akregator).
changing play $sound to aplay $sound worked instantly. I didn even have to log out.
How come this changed??

'cause aplay $sound is ALSA specific command.

cheers

Luis

---

### Post by Icarosaurus on 2007-10-07
I'm using OSS instead of ALSA.
I couldn't use sound in amsn after an upgrade.
Maybe the snack/tcl library has been compiled and packed for ALSA only.

I downloaded the snack binaries for linux from here:
[http://www.speech.kth.se/snack/download.html]("http://www.speech.kth.se/snack/download.html")
and I overwrote the files into /usr/lib/snack2.2
Everything works fine now using snack, including voice clips.
I hope this helps someone...

---

### Post by marcon00 on 2008-06-12
worked for me by adding " aplay "

---

### Post by Kaneda187 on 2008-07-07
Thanks guys that worked great!:) its a bug that had been buggin me for a while......eh eh!! :lolflag:

---

