---
title: "[SOLVED] Thunderbird automatic startup"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by ubername on 2007-11-26
Hi

I have added thunderbird to my startup sessions. However, when it starts it does not automatically download messages from the accounts I have set up to download on startup (by which I mean it doesn't ask for the password for these accounts). If I close it and start manually it does.

Perhaps this is the wrong place, so I will also ask the question in the Mozillazine Thunderbirtd support forums, but thanks to anyone who can help.

---

### Post by kelbizzle on 2007-11-27
> **ubername said:**
> 
Perhaps this is the wrong place, so I will also ask the question in the Mozillazine Thunderbirtd support forums, but thanks to anyone who can help.

You were absolutely right when you said that. At least you did the right thing and posted on the Mozilla support forums.[ There's a couple things in this support article you may want to check out]("http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Automatically_Download_Messages"). It's just a little bit more things to troubleshoot. Better for you to read for yourself rather than me walk through the article with you step by step.

---

### Post by ubername on 2007-11-28
> **kelbizzle said:**
> You were absolutely right when you said that. At least you did the right thing and posted on the Mozilla support forums.[ There's a couple things in this support article you may want to check out]("http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Automatically_Download_Messages"). It's just a little bit more things to troubleshoot. Better for you to read for yourself rather than me walk through the article with you step by step.

Hi
Thanks for the reply. 

I felt it was appropriate to post here as well, because, as I mentioned in my original post, thunderbird works as expected when started manually after Ubuntu has started up, it is just when I start TB from the 'sessions' program, to run at startup. that it does not get messages.

---

### Post by kelbizzle on 2007-11-28
Are you using pop or Imap? I use imap and I can't reproduce the issue?

---

### Post by kelbizzle on 2007-11-28
Here create a new file and save it as "tbstartup" in /usr/bin. Open the properties and goto the permissions make sure all have read and execute permissions.  Goto sessions and just put tbstartup.
see if that works for you.

```
#! /bin/sh
sleep 30;
thunderbird
 
```

---

### Post by ubername on 2007-11-30
> **kelbizzle said:**
> Here create a new file and save it as "tbstartup" in /usr/bin. Open the properties and goto the permissions make sure all have read and execute permissions.  Goto sessions and just put tbstartup.
see if that works for you.

```
#! /bin/sh
sleep 30;
thunderbird
 
```

Thanks!

Fixed like a charm. Good thinking and thanks for the script. I guess the next question is why this happens at all, but your workaround does the job.

---

### Post by kelbizzle on 2007-12-01
hm... try posting a bug report. It maybe be something we're overlooking.  It's funny how things work out. Since troubleshooting your issue I've been using thunderbird since :-D

---

