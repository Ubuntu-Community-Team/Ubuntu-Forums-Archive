---
title: "Primary or extended or WHAT"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-07-31
Could someone please advise what format i should make the little bit of unallocated space i have on my main (xp) hdd.
I have unbunto on a small slave drive but it could do with ANY spare space available.
I have a bit of UNallocated space on xp`s hdd but am not sure what to do when asked wether i want "primary" or "extended" AND of what format i should make the said space...i.e ext3,swap etc etc.
Ive got everything else working which really was`nt tooo hard BUT i could do with utilising that little bit of unallocated space...
Sorry if i asked this in a previous thread BUT i never got an answer on this

---

### Post by beniwtv on 2006-07-31
That depends.

Windows creates a 8MB partition - DON'T delete that. Windows won't start anymore after you delete it.

If you partition is not the above, you could make a "primary" partition using ext3 or even fat if you want to share the files with Windows.

---

### Post by xpod on 2006-07-31
Im not sure about this "8mb" windows partition you mention.
ALL my main hdd consists of is one big 38ish g with xp taking up about a third of the space BUT right on the end is a "UNALLOCATED" 2ish g.

I assume if thats the only 2 segments of any sort that i have THEN i dont have this separate 8mb one you talk of?

So if i just set that little space as "primary" and format it to ext3 i should be ok and unbunto will utilise the wee extra bit of space ok?

Im begining to winder if i would have been better after all just splitting the main hdd between XP & Unbunto(half & half)and using the smaller one as the swap file or something like that?

Thanks anyway.....

---

### Post by beniwtv on 2006-07-31
Ok, I suggest you to create it as primary and format it in ext3. Ubuntu can use it then but windows can't.

Anyway, if you still have more questions, ask. I'll be glad to help.

---

### Post by Thirsteh on 2006-07-31
The difference between "primary" and "extended" is simply that there can be a max of 4 primary partitions, and a lot of extended, so if you're going to have more than 4 partitions on one drive, use extended for the excessing.

---

### Post by xpod on 2006-07-31
WHOA...........Major scare!!!!!!!!!!!!!!!1

Went ahead and formatted as a primary ext3.Rebooted once it was done JUST to check and i got a BSOD when booting to XP(ouch!!!).
So after getting straight back on to linux and the Gpart I REparted that wee space right back to the unallocated space it started out as(could`nt see how THIS would have solved such a calamity).....Rebooted again and chose "last good config" from the uptions and thankfully XP loaded quite ok.

Was it mabey just protesting at a NON windows space being there.
Would it be safe to try again i wonder?????
What`dya reckon folks????

PS....is there no tabbed browsing on FF in unbunto OR am i just needing to figure out one of the many new ways of using things in linux????


OOP`S....GOT IT.....DUH!!!!!!!

---

### Post by beniwtv on 2006-07-31
Err... How much space has this partition you want to format?

I'm not quite sure what happened to your windows when formatting it, but it seems to me that windows need it - or - even by accident, you made it the active partition. Note that the windows partition needs to be the active one so that windows can boot.

---

### Post by xpod on 2006-07-31
Hi,it`s only 1.8g and it`s an UNallocated space on the end of my main hdd with xp on it.The drive is only 40g and the main partition with xp has the rest BUT only actually uses abot 1 third of that.

It`s strangER that windows come back at all if something got done to it.

All i did was click the little 1.8g unallocated space then clicked "new" and chose primary and ext3.

Surely it`s nothing to do with windows if it`s unallocated?????

OR...is that something new im learning...haha

Windows would`nt be protesting at THIS new space being allocated as "primary" would it???

---

### Post by PaulFXH on 2006-07-31
Hi
Windows will always do a CHKDSK (or something similar) whenever GPartEd makes a change to the system disk. Perhaps, this is what caused the BSoD.
Have you run CHKDSK without problems recently?

Another possibility is that you put the bootable flag on your new re-formatted partition. Are you sure you didn't do this?

I did more or less what you are trying to do without any problems about three times in the last week, so it should work!

Paul

---

### Post by xpod on 2006-07-31
Sorry..i`ve got that many qestions in my head im forgetting the ones im ASKING

As far as i recall that was fine...the whole disk was checked,defragged and sfc /scannow had been run recently.

Whatever caused it obviously did`nt quite kill xp off so i mught as well give it another go.

I feel a bit more comfortable NOW trying to cause irreversable damage to windows(nothing new)...IF it dies it dies eh

---

