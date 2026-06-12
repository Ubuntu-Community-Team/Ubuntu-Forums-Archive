---
title: "Sound problem iMac 233"
date: 2004-12-29
forum: Apple PPC Users
---

### Post by jerker on 2004-12-29
Hello

I have just started to use Ubuntu on my iMac 233. (I´m not a regular Linux user jet :D )
My problem is that the sound is only working then i use headfones. But if i plugs in a cable in line connection in the side, then the sounds comes from the internal speackers. So it sems that the sound is wrongly setup.
How to fix this?

I have tested i mac os 9 and there the sound works as expected.

Regards
Jerker Drottenmyr

---

### Post by redneckr1 on 2005-01-05
i had a similar problem, with my 233 trayloading green "ixmac" ;)
you have to fiddle around with the volume control and put your speaker out (headphone jack) into the bottom front port to get sound. i know its a bit backward but it works. also you can enable the front speakers to get nearly surround. 

hope this helps

Red

---

### Post by jerker on 2005-01-06
I did noties it yesterday.

Her is a  summery of my last test:
1. Started the Volymkontroll (swedish) the sound controll under Gnome menu. Auto mute checked.
2. Puted a CD in.
3. The sound comes from the internal speakers, this time.

The controlls that effects the sound in ALSA is:
Master, Headphone, CD.

In oss
Volym, CD, PCM-2

Ok, lets plugin headphone in the top frontside jack.
The sound comes in the internalspeakers and headphone.

ALSA:
Master, Headphone (only internal speaker), CD, PC-speaker (only in headphone)
Check headphone and internal speakers goes silent.

OSS:
Volym, H (only headphone), CD, PCM-2 (only speaker)
If you check PCM-2 then the sound in speakers is silent. H affects headphone but the sound is only geting lower.

Ok, lets plugin headphone in bottom frontside jack.
The sound comes in the internalspeakers and headphone.

ALSA:
Master, Headphone (only internal speaker), CD, PC-speaker (only in headphone)
Check headphone and internal speakers goes silent.

OSS:
Volym, H (only headphone), CD, PCM-2 (only speaker)
If you check PCM-2 then the sound in speakers is silent. H affects headphone but the sound is only get lower.


ok, side jack:
ASA:
Master, Headphone (only speaker) CD
Check headphone and the internal speaker goes silent.

OSS
Volym, CD, PCM-2 (only speaker)
Check PCM-2 and the internasl speaker goes silent.

Mute all unchecked:
Headphonne in top jack or bottom.
Only sound in headphone.
ASA
Master, CD, PC speaker

If i pluggout, thers no sound until a check and unckek headphone. Then sound comes from the internal speaker.
And to control the sound you use Master or headphone.

Side jack:
Sound from internal and side jack. Checking headphone silence internal speaker


And the sound volume from the side jack is low.

/Jerker

---

