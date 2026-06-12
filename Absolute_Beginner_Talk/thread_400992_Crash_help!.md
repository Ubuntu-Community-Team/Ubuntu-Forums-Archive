---
title: "Crash help!"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by gosunsgo on 2007-04-04
Hi everybody,
long time reader, first time poster.

I completly switched off from windows more than 2 months ago and so far so good.

I have a problem though:
I searched a lot on the forum but i didn't find any answers.
Here it goes:
Sometimes Kde hangs on me, the mouse stops working and everything is frozen. If I am at the pc when it does happen, I can gently switch the pc off with the RSEIUB method (Raising skinny elephants...) because ctrl-alt-backspace doesn't work nor ctrl-alt-f1 to login to another console.
Otherwise if I am not at the pc but i come back 1 hour later even the RSEIUB doesn't work.

Since I wanted to know the reason why the crash happens I have searched in the log files in /var/log but there is no indication in the logs in this folder.

Are there any other logs in some other folder that i don't know about that can help me determine the reason why this happens?

Thanks to everybody on this great forum for any help and for the great support so far!!

By the way i have kubuntu edgy regularly updated through apt-get, nvidia drivers thruogh envy. (If you need more specs, tell me!)

---

### Post by Skrynesaver on 2007-04-04
That sounds like a hang rather than a crash, some process has gone hog wild on your memory.  Is there any particular application that is always running when this occurs

---

### Post by gosunsgo on 2007-04-04
Hi,
It depends: usually in the background there is beagle, kde notes and gaim.
But other than that there isn't one application in particular. The one i use the most are: amule, amarok, firefox, kaffeine and VLC.

What I was looking for is if there is a log that I can look at to know what is going on when this happens.

If it is a memory issue (1 Gb RAM, 1,5 swap) what can i do to monitor these problem?

Thanks for the answer, by the way

---

### Post by gosunsgo on 2007-04-04
I stumbled upon this: [http://ubuntuforums.org/showthread.php?t=373087](http://ubuntuforums.org/showthread.php?t=373087) because I read about memory leakege in Xorg.

Will try that and post the results

---

