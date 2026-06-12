---
title: "Time changes in windows after using Ubuntu"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by Stone_Wolf on 2006-02-20
Hiyas

I've noticed a glitch with my pc after using Ubuntu. It's more of an annoyance than anything, and i'm assuming it's something to do with the way i mount the windows partitions.

After every session in Ubuntu my Windows is set two hours earlier than it actually is. I'm guessing this is to do with the utf=8 part of the NTFS mount command? I'm in GMT+2 hours, give or take a few minutes. 

Does anyone know what causes this, or if i'm not using the correct setting? Also if it's a setting, the relative for Fat32 would also help. 

Many thanks
SW

---

### Post by Mustard on 2006-02-20
I'll think you will find its because ubuntu is using UTC time in the preferences for the date and time.  I noticed the same thing recently and it was a bit annoying. :)  Try turning off UTC time in the date/time preferences  and that should remove the discrepancy between the two operating systems.  You may need to set the time again though.  You might find a few errors in your logs for a while after the time/date changes too.

That's my theory on the problem anyway.

---

### Post by earobinson on 2006-02-20
yup that should be it, if not do a quick search for [time windows] and that will answer your problems.

[http://www.ubuntuforums.org/showthread.php?t=133482&highlight=time+windows](http://www.ubuntuforums.org/showthread.php?t=133482&highlight=time+windows)

---

### Post by chimera on 2006-02-20
You caused a time-warp by installing Ubuntu. Next time, read the anti-time diletation HOWTO before you install.

---

### Post by Mustard on 2006-02-20
[QUOTE=earobinson]yup that should be it, if not do a quick search for [time windows] and that will answer your problems.

[http://www.ubuntuforums.org/showthread.php?t=133482&highlight=time+windows](http://www.ubuntuforums.org/showthread.php?t=133482&highlight=time+windows)[/QUOTE]
Hehehe..I think I am caught in a bit of a time warp when I click on the link earobinson. :)

It brings me straight back to this thread. :P

---

### Post by ahlich on 2006-02-20
It's actually a windows "feature". It is trying to go back in time and undo itself to pre-existence. Pretty soon you will be using 5 and a quarter floppies if you don get rid of your MS products right now...

---

### Post by SMF on 2006-02-20
Well I am glad I was not the only one that was experiencing this problem. I did not think it had anything to do with ubuntu but it was possible. I thought maybe it was another newly installed program I had installed on windows just before I installed Ubuntu. Anyways, I agree it was a pain getting back on windows and seeing my clock moved ahead 8 hours:rolleyes: Windows is now gone and I dont have to worry about that anymore:mrgreen:

---

### Post by unbutuju on 2006-02-20
Ubuntu loads time sync thru ntp server by default, windows doesn't!

Could that be related?...

---

### Post by earobinson on 2006-02-20
[QUOTE=Mustard]Hehehe..I think I am caught in a bit of a time warp when I click on the link earobinson. :)

It brings me straight back to this thread. :P[/QUOTE]
sorry about that cut and paste the worng link, but a simple search should solve your problem.

---

### Post by Stone_Wolf on 2006-02-21
Okay then...

Just checked and i'm not using UTC. I've got the timezone set to Johannesburg, which is what i use for MircoHell also.

I'm still looking around though, and i'll let you know if i come across anything interesting ;)

Regards
SW

---

### Post by WakkiTabakki on 2006-02-21
Check in[FONT="Courier New"] /etc/rcS[/FONT]. There should be a line UTC=yes, chacge this to <tatatatataaa> UTC=no.

Hope it works
/N

---

### Post by Mustard on 2006-02-21
[QUOTE=Stone_Wolf]Okay then...

Just checked and i'm not using UTC. I've got the timezone set to Johannesburg, which is what i use for MircoHell also.

I'm still looking around though, and i'll let you know if i come across anything interesting ;)

Regards
SW[/QUOTE]

If you are using gnome, which I assume you are, you should be able to right click on the date/time in your top right corner and choose 'preferences'.  I think you will find the option for 'Use UTC' in there.

---

### Post by Stone_Wolf on 2006-02-28
Hiyas

Alright, just an update. I've not yet neem able to solve this little mystery.

I've done everything you guys suggested, but nothing worked. "Use UTC" under preferences for the clock is unchecked, and there is nothing in the file "ect/rcS". It's blank, so i don't think i can change anything there. I'd rather not tinker with things i know nothing about just to sort out a minor annoyance.

I'm still looking around though, i'll report back if i find anything. ;)

Regards
SW

---

