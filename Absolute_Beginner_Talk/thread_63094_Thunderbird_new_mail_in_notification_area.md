---
title: "Thunderbird: new mail in notification area?"
date: 2005-09-06
forum: Absolute Beginner Talk
---

### Post by aysiu on 2005-09-06
So I searched around (e.g., [here](http://www.google.com/search?num=100&hl=en&lr=lang_en&safe=off&q=thunderbird+notification+area+site%3Aubuntuforums.org&btnG=Search)), and I can't seem to find much about this. In Windows, there's an option to have Thunderbird display a visual notification of new messages. In Linux, there's only a sound and nothing else.

I hate sounds. Maybe it's just me, but I hate them. I'll listen to music but not sounds.

Is there any way to enable Thunderbird to notify me of new mail in the notification area (where I get notified of software updates)?

---

### Post by Nequeo on 2005-09-06
[QUOTE=aysiu]So I searched around (e.g., [here](http://www.google.com/search?num=100&hl=en&lr=lang_en&safe=off&q=thunderbird+notification+area+site%3Aubuntuforums.org&btnG=Search)), and I can't seem to find much about this. In Windows, there's an option to have Thunderbird display a visual notification of new messages. In Linux, there's only a sound and nothing else.

I hate sounds. Maybe it's just me, but I hate them. I'll listen to music but not sounds.

Is there any way to enable Thunderbird to notify me of new mail in the notification area (where I get notified of software updates)?[/QUOTE]
 Something like Mail-notification: [http://www.nongnu.org/mailnotify/](http://www.nongnu.org/mailnotify/) is probably as close as you're going to get. 

You could also try Gnubiff (or was it gbiff?) if you want the number of unread e-mails displayed. However, on my system displaying the mail summary is buggy, ugly, and crashes a lot.

EDIT: Both in the Universe rep.

Personally, I'm working on a panel applet 'Gnoptray', to address this shortage ([http://sourceforge.net/projects/gnoptray)](http://sourceforge.net/projects/gnoptray)), which will hopefully combine the best of both programs. It will never support as many mailbox types as mail-notification, but for standard POP3 and IMAP it should be fine. Unfortunately, developement is stalled until Breezy becomes stable - as a bug in the version of PyGTK shipped with hoary prevents spawned threads from starting if you're running the program as a panel applet. Which I am :)

---

### Post by aysiu on 2005-09-06
Thanks for the quick response! I'll look into those.

---

### Post by Hobbsee on 2005-09-07
[QUOTE=aysiu]Thanks for the quick response! I'll look into those.[/QUOTE]
 [http://moztraybiff.mozdev.org/](http://moztraybiff.mozdev.org/) may be another answer to what you are looking for.

(it's a thunderbird extension)

Or is that the thing Nequeo mentioned above?

---

### Post by aysiu on 2005-09-07
[QUOTE=Hobbsee][http://moztraybiff.mozdev.org/](http://moztraybiff.mozdev.org/) may be another answer to what you are looking for.

(it's a thunderbird extension)

Or is that the thing Nequeo mentioned above?[/QUOTE] That's not what Nequeo mentioned above. I'll explore that extension, too. Thanks for all the suggestions!

---

### Post by aysiu on 2005-09-07
I just tried out that Thunderbird extension. Perfect! Thanks again.

---

### Post by Hobbsee on 2005-09-08
[QUOTE=aysiu]I just tried out that Thunderbird extension. Perfect! Thanks again.[/QUOTE]
 No problems :)

I've found it to be really useful.

---

### Post by ESM on 2006-02-28
About six months later: I started to use Ubuntu with Thunderbird and I have a question too:

Is it possible that Thunderbird goes to the upper panel when closing with the notifier still working?

---

### Post by MadL on 2006-02-28
Thanks to aysiu for asking the question, and to Hobbsee for pointing out the Thunderbird extension. I'd been wondering about this myself (don't like the sound, either, and I'm not always at the computer to hear it, anyway).

---

### Post by ESM on 2006-03-01
I use mail notification 2.0 now and this morning all of a sudden it popped up by itself to tell me that there was new mail.. amazing ;)

---

