---
title: "Screen greys  out"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by allsys3 on 2008-01-10
sometimes on youtube when i click on a video the screen will grey out after about ten seconds or so  and everything locks up. Then i need to force quit to restart the browser. Ive also encountered the same problem on occassion while using rhythm box. Im currently running gutsy with compiz fusion and AWN . Any ideas would be appreciated.

---

### Post by rune0077 on 2008-01-10
I've been having the same problem playing videos through Firefox. However, you don't need to force quit it: if you're patient and just wait, the video will eventually begin to play or the page will change to the one you wanted to go to. This can take anywhere from a minute to ten minutes, depending on the size of the videofile (I think) that caused the freeze.

---

### Post by nikef on 2008-01-10
Yes i have the same problem 2
so i think its to do with firefox,so i started to use  opera instead

---

### Post by zero-9376 on 2008-01-10
the greying out is a feature of compiz-fusion to let you know that the app has stopped responding, you would likely get the same 'lockup' without CF enabled but you would not get the feedback, this is one of the unrecognised non-eye-candy-only features of CF.
as for firefox locking up rune0077 is right firefox should come back if you are patient. as for rhythm box i have always found it to be very buggy so i dont know if patience will get you through with that particular app.

---

### Post by FuturePilot on 2008-01-10
> **nikef said:**
> Yes i have the same problem 2
so i think its to do with firefox,so i started to use  opera instead

This is not a Firefox issue. If it's happening on pages with Flash content it's a Flash issue and it will affect all browsers. It's been going on for a long time now, you can search the forums to see what I mean. And Adobe doesn't seem to want to do anything about it.

---

### Post by rfruth on 2008-01-10
I set visual effects (GG, System >> Preferences >> Appearance) to NONE cause don't like this effect

---

### Post by rune0077 on 2008-01-10
> **FuturePilot said:**
> This is not a Firefox issue. If it's happening on pages with Flash content it's a Flash issue and it will affect all browsers. It's been going on for a long time now, you can search the forums to see what I mean. And Adobe doesn't seem to want to do anything about it.

Yeah, this is almost certainly a Flash issue. Considering how much trouble Firefox has had with Flash, though, it may turn out to be more relevant to Firefox than to other browsers. 

Next interesting question: is it only a 64bit issue, or do any of you that has this issue run 32bit systems?

---

### Post by FuturePilot on 2008-01-10
I have the problem on 3 32 bit systems so it's not a 64 bit issue.

---

### Post by irv on 2008-01-10
Maybe it might be a problem with both flash and compiz fusion running at the same time. Try turning off compiz fusion by going to Atl F2 and type "metacity --replace". then see if it happens again.

---

### Post by allsys3 on 2008-01-10
you mention that if you wait long enough the movie will start so could it be that compiz is set to grey out after a predetemined amount of time if the flash player doesnt connect?

---

### Post by FuturePilot on 2008-01-10
> **irv said:**
> Maybe it might be a problem with both flash and compiz fusion running at the same time. Try turning off compiz fusion by going to Atl F2 and type "metacity --replace". then see if it happens again.
They grey out effect is just a Compiz effect. The underlying problem is most likely Flash in this case so the browser will still freeze up.
> **allsys3 said:**
> you mention that if you wait long enough the movie will start so could it be that compiz is set to grey out after a predetemined amount of time if the flash player doesnt connect?
Yes Compiz is set to grey a window out if it doesn't receive a signal after a certain period of time.

---

### Post by billgoldberg on 2008-01-10
I get that all the time when viewing flash videos in firefox (and other firefox based browsers like flock, netscape navigator 9) and epiphany.

I just use the "pkill firefox", then use firefox's button to restore the session.

I believe this doesn't happen in opera.

I hope firefox will sort this out in 3.0

---

