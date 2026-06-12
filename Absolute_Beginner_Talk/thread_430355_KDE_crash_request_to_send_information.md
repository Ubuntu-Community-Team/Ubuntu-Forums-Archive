---
title: "KDE crash request to send information"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by darkworld on 2007-05-02
After booting my machine I was told kde had crashed at some point and if I liked I could send the information. It wasnt the usual KDE crash screen bug report, it was something new. A bit like microsoft send report now?

Is this a new kde feature or have i loaded a trojan?

---

### Post by fakie_flip on 2007-05-02
> **darkworld said:**
> After booting my machine I was told kde had crashed at some point and if I liked I could send the information. It wasnt the usual KDE crash screen bug report, it was something new. A bit like microsoft send report now?

Is this a new kde feature or have i loaded a trojan?

Make a screenshot and then upload it in your post or give us a link to it.

If you really think you could have a trojan or something similar in Ubuntu, then install and run chkrootkit, but I highly doubt it. Probably 99% of all trojans are made for Winblows, and won't harm Linux.

---

### Post by darkworld on 2007-05-02
ok I will reboot to see if it comes back.

The thing is it didnt look that professional, I cancelled it.

---

### Post by darkworld on 2007-05-02
well i rebooted and nothing. Then I locked firestarter while I looked at Ksystemlog. No clues there but then im a newbie so not sure what im looking for. 

Next I went to unlock firestarter and come back to forum but firestarter froze, rebooted still no repeat of crash data collection.

Any ideas?  Who can tell me if KDE have implemented a new style bug data collection?

---

### Post by fakie_flip on 2007-05-02
> **darkworld said:**
> well i rebooted and nothing. Then I locked firestarter while I looked at Ksystemlog. No clues there but then im a newbie so not sure what im looking for. 

Next I went to unlock firestarter and come back to forum but firestarter froze, rebooted still no repeat of crash data collection.

Any ideas?  Who can tell me if KDE have implemented a new style bug data collection?

Install and run chkrootkit. If that isn't enough, you can do forensics test from a special live cd made for security. I don't understand why a cracker would put some fake bug reporting software on your system, but go ahead and run chkrootkit and tell us the results. If you think you have a trojan, you can use clamav or search adept for other antivirus software.

---

### Post by darkworld on 2007-05-02
Ok the reason I wondered about trojan was because it occurs just after boot up when I have entered root password to run fire starter. The message about what has happened reads 

"sorry the program kdeinit closed unexpectedly."

"If you were not doing anything confidential (entering passwords or other private information). You can help to improve the application by reporting the problem."

It then goes into an XP style data collection which I have never seen KDE do and this alarmed me. Ive crashed KDe before several times when I was on Mandriva 2007 and never seen this. What do peeps think?

Since this firestarter has been playing up occasionally freezing. I will do what you suggest above next.

(I have inserted screen shots below, need magnifying. the knote on desktop was me copying message in case I couldnt read screen shots.)

[ATTACH]31574[/ATTACH]

[ATTACH]31575[/ATTACH]

[ATTACH]31576[/ATTACH]

---

### Post by ltk5 on 2007-05-02
to me it doesn't look like anything special, just a crash report

---

### Post by darkworld on 2007-05-02
> **ltk5 said:**
> to me it doesn't look like anything special, just a crash report

Is it a KDE crash report? have they changed them? is the sending data xp style how its done now?

The thing is if its how it is now then Im happy, but if nobody else has seen this 'sending data' then im wondering. Sending what data? because yes I was entering root password when it occured! 

carried out chkrootkit. No problems.

---

### Post by darkworld on 2007-05-03
well I posted on Kubuntu form and nobody on there can tell me if this is KDE behaviour.

---

### Post by darkworld on 2007-05-03
SORTED - thanks everybody

---

### Post by petersjm on 2007-05-03
> **darkworld said:**
> SORTED - thanks everybody

So what was it?

---

### Post by fakie_flip on 2007-05-04
Do a search on the error message. I suggest you start searching errors like this before posting because chances are someone has already asked and found a solution for it. You'll save a lot of time solving your problems if you do simple searches first. they get you an anwser quicker 9 times out of 10, and after that if you don't find what you are looking for, you should start a thread. These error messages in KDE are nothing unusuall. I have seen them before, and they are not from a trojan. I told you earlier that I highly doubt that was the cause. You could have also gone a long, and made a bug report. Then a developer would email you back by asking you for more information until he can tell you what is wrong.

---

