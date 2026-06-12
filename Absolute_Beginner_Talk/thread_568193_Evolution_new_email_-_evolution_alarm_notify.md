---
title: "Evolution new email - evolution alarm notify"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by keyboardashtray on 2007-10-05
Does/should/can Evolution simply run in the background, download new email from my gmail account, and notify me of it?

I don't understand if Evolution is bugged or if I have something set up wrong.

I have evolution-alarm-notify checked in Sessions, and when I check the priorities there are two listings for it, one normal one and at the bottom one listed as the whole directory path. Both are priority 50. I don't know if this is relevant.

When I first setup Ubuntu, and then later this account, I didn't need it so at the time I unchecked it. I don't know if this is relevant either. 

Also, when I try to access Help from in Evolution, it doesn't bring me the help files. I have to open help manually, and navigate to Evolutions section. This isn't my problem, but I thought it might mean I had a bad install. I reinstalled through Synaptic, along with common files and a couple other Evolution things. Still doesn't work.

I found a few posts, either unanswered or really old. One old one said to use Alltray, which will work for now, as a workaround I guess. But I'd much rather not have to run a whole separate program to have Evolution working in the background, I'd much rather have it so that I could simply log on, and something in the panel would tell me when I have new mail, and I could click it.

Shouldn't evolution-alarm-notify be checking my email and notifying me? And if thats not what it is for, what is the point of having a process running in the background (along with 2 other ones, evolution data server and evolution exchange storage)?

---

### Post by dcstar on 2007-10-06
> **keyboardashtray said:**
> Does/should/can Evolution simply run in the background, download new email from my gmail account, and notify me of it?

I don't understand if Evolution is bugged or if I have something set up wrong.

I have evolution-alarm-notify checked in Sessions, and when I check the priorities there are two listings for it, one normal one and at the bottom one listed as the whole directory path. Both are priority 50. I don't know if this is relevant.

When I first setup Ubuntu, and then later this account, I didn't need it so at the time I unchecked it. I don't know if this is relevant either. 

Also, when I try to access Help from in Evolution, it doesn't bring me the help files. I have to open help manually, and navigate to Evolutions section. This isn't my problem, but I thought it might mean I had a bad install. I reinstalled through Synaptic, along with common files and a couple other Evolution things. Still doesn't work.

I found a few posts, either unanswered or really old. One old one said to use Alltray, which will work for now, as a workaround I guess. But I'd much rather not have to run a whole separate program to have Evolution working in the background, I'd much rather have it so that I could simply log on, and something in the panel would tell me when I have new mail, and I could click it.

Shouldn't evolution-alarm-notify be checking my email and notifying me? And if thats not what it is for, what is the point of having a process running in the background (along with 2 other ones, evolution data server and evolution exchange storage)?

You can set up stand-alone mail checkers to check POP acounts for new mail, the Evolution checker just checks when Evolution receives new mail, and then informs you. If Evolution is not running, then it cannot receive mail for the mail notifier to know about and then inform you.

The help file problem is probably a known bug (it also doesn't work for me), it may be fixed in the 7.10 Ubuntu release available shortly.

I also have two entries for the alarm-notifier, mine works fine.

---

### Post by keyboardashtray on 2007-10-06
> **dcstar said:**
> You can set up stand-alone mail checkers to check POP acounts for new mail, the Evolution checker just checks when Evolution receives new mail, and then informs you. If Evolution is not running, then it cannot receive mail for the mail notifier to know about and then inform you.

The help file problem is probably a known bug (it also doesn't work for me), it may be fixed in the 7.10 Ubuntu release available shortly.

I also have two entries for the alarm-notifier, mine works fine.

Thanks, I appreciate the help. :) I still am wondering, though - what is the use, then, for evolution-alarm-notification to be running in the background, when it won't tell you anything unless you start evolution anyway. Sort of seems like a solar powered flashlight.

---

### Post by Faud on 2007-10-06
Just my two cents, sorry if its out of line. If that is all you want evolution for is to notify you of incoming mail to your gmail account; you could just use a gmail notification screenlet instead.

---

### Post by keyboardashtray on 2007-10-06
> **Faud said:**
> Just my two cents, sorry if its out of line. If that is all you want evolution for is to notify you of incoming mail to your gmail account; you could just use a gmail notification screenlet instead.

No, its not out of line, you just misunderstood the question.

---

### Post by FuturePilot on 2007-10-06
I also noticed that when I click on Help nothing opens. Haven't tested it on Gutsy yet.

---

### Post by SLIMwoogi on 2008-02-28
"Evolution Alarm Notifier" is not for email. It's a alarm notifying process for Calendar of Evolution.

---

