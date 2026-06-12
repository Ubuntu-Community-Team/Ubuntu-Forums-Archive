---
title: "Sound System Stops At Random Times"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by InuyashaDuelist on 2007-04-12
A couple of months ago, I had this same problem. But I fixed it somehow, and forgot how.

Yesterday, I was listening to a really nice song on Amarok, and right as the guitar solo was coming up, the music just stopped. I took a look at the icon in the tray, and it appeared to still be playing (it still had the play symbol on it), so my fear that the problem returned immediately popped into my mind. 

I immediately closed Amarok and went to YouTube to try to view a video (as the last time I got this problem, videos would only play about two seconds, then stop playing). The same problem occurred.

So it appears the entire sound system just stopped working. I tried to restart the sound system, but it appears that the only way to fix this problem is to end my session and make a new one. And even then, I can only listen to maybe one and a half songs before it stops again. Stopping my session isn't something I'm hoping to have to do every fifteen minutes. 

Now, I don't remember what I did last time to fix it, so I was hoping someone on the forum here would have a clue. Thanks in advance.:)

---

### Post by InuyashaDuelist on 2007-04-13
Bump.

---

### Post by deadgobby on 2007-04-13
Ugg I can't recall to fix this off my head either. Have your open up the terminal and type in
killall esd

Gobby

---

### Post by InuyashaDuelist on 2007-04-13
```
esd: no process killed
```

Nope.

---

### Post by deadgobby on 2007-04-13
Have you gone through this guide?
[https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28sound%29](https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28sound%29)
[https://help.ubuntu.com/community/DebuggingSoundProblems?highlight=%28sound%29](https://help.ubuntu.com/community/DebuggingSoundProblems?highlight=%28sound%29)

---

### Post by InuyashaDuelist on 2007-04-13
Yes, I have. I recently went in and reinstalled the ALSA drivers again. I hope it stays working.

---

### Post by InuyashaDuelist on 2007-04-13
Seems to be working for now. Thread marked as Resolved until something happens again.

---

