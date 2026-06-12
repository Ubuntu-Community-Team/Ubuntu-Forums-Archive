---
title: "No Audio -- How do I find a solution?"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by thornomad on 2006-10-30
Hi --

I had been running 6.06 and audio worked fine; now I am in 6.10 and audio is not working!  I have a IBM R32 Laptop; everything else is working great.

(When I first installed 6.10, I cannot remember if I had sound or not initially ... it has only been a couple days and I am now just getting around to listening to some audio and watching movies.)

Anything I can try to troubleshoot?  Volume is up, I played with the special "thinkpad keys" ... can't get it working again.  Headphone jack doesn't work either.

Thanks,
Damon

---

### Post by raqball on 2006-10-30
have you tired in terminal 

```
alsamixer
```

make sure the sound there is maxed and it is not muted (MM)

---

### Post by thornomad on 2006-10-30
I had not tried that!! Didn't know about it ... but, the MASTER was maxed (it follows the little buttons on my system like it should) ... everything else was MM ... so, I raised everything ... but, still, I am not getting any sound.

Have tried my Sound Preferences and used Test but no luck.

---

### Post by raqball on 2006-10-30
To unmute you need to move to that section and hit the 'm' key. I assume you did that?

---

### Post by thornomad on 2006-10-30
> **raqball said:**
> To unmute you need to move to that section and hit the 'm' key. I assume you did that?

Woah!  No, I did not see the "M" key ... woo hoo!  It is working again.  Was my PCM setting I guess ... everything else was MM ... fascinating! 

Learning something new everyday.

Thanks!

---

### Post by raqball on 2006-10-30
Awesome! I am glad you have sound! :)

---

### Post by numbah1 on 2006-11-02
I'm sorry to take over your post but it has the same idea....have u sound in headphone jack?!cause i have sound normally but if i put on the headphones e dont get any sound on them....think u can give me a few hints?!
thkx

---

