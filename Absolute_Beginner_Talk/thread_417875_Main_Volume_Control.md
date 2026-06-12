---
title: "Main Volume Control"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Biscuitpie on 2007-04-22
For some reason my main volume control doesn't affect anything, even when muted. Nothing huge, but it's bugging me. >.<

---

### Post by kittyhawk63 on 2007-04-22
> **Biscuitpie said:**
> For some reason my main volume control doesn't affect anything, even when muted. Nothing huge, but it's bugging me. >.<

Biscuitpie,
What do you mean that it does not affect anything? Do you mean that you can not turn the volume up or down with it? Do you hear audio, but you can't mute it?
When you reply, someone will know your problem and will give you a solution. 
kh
You will have an someone to help you.

---

### Post by Biscuitpie on 2007-04-22
Yeah, I hear things, and the volume controls integrated into the programs themselves work. But the master volume control doesn't change anything, even though it says it's louder, muted, or softer. =/

---

### Post by kittyhawk63 on 2007-04-22
I'm sure that there is a fix for this. I am giving you a bump to keep you on the first page. Someone should be able to help. 
I am too new myself to give you the answer you need. 
kh

---

### Post by marko_4454 on 2007-04-22
> **Biscuitpie said:**
> For some reason my main volume control doesn't affect anything, even when muted. Nothing huge, but it's bugging me. >.<

If you are saying the volume control icon in the gnome-panel, then just right click it, then preferences. Then choose PCM, that should work. :)
If it doesnt, then try the other options. If it doesnt for some reason, post again here.

---

### Post by Biscuitpie on 2007-04-22
Well, I just installed Beryl again and can't hear anything, so I can't test that. :(

---

### Post by marko_4454 on 2007-04-22
So did you have sound before beryl???
have you tried
```
alsamixer
```

and change the MM in the bars?? and also raise the volume?

---

### Post by Biscuitpie on 2007-04-22
I love you for that. PCM DOES work, as well, is there anyway to make it the one changed by the small slider by simply clicking the volume button or using my keyboard? Right now it's controlling "Headphone". Also, Beryl stopped me from seeing videos. Know anything about it?

---

### Post by Biscuitpie on 2007-04-22
Everything is fixed but making PCM the main one.

---

### Post by marko_4454 on 2007-04-22
> **Biscuitpie said:**
> Everything is fixed but making PCM the main one.

I think thats the way its supposed to go :)
But I am not sure though....I just have it that way. Anyways, I am glad that you got it fixed..

---

### Post by irw on 2007-05-05
I have exactly the same problem - started a few days ago, but have no idea why.
I have changed the preferences of the volume control to control PCM, so that works, but for some reason the volume / mute keys on my laptop still do nothing. 

Any other ideas please?

---

### Post by FerGeCo on 2007-05-18
> **irw said:**
> I have exactly the same problem - started a few days ago, but have no idea why.
I have changed the preferences of the volume control to control PCM, so that works, but for some reason the volume / mute keys on my laptop still do nothing. 

Any other ideas please?

Well .. what helped in my case (feisty) was:

run : gnome-sound-properties

and change standard mixer thingie to PCM.

---

### Post by irw on 2007-05-18
I did this, changing to PCM, so it worked.  A few days later I changed it back to master, which is what was selected when it did not work ... and it now works as it used to ... :confused:

by the way, what does PCM stand for?

---

### Post by isagani on 2007-05-31
Pulse Coded Modulation... It's geek talk for digital sound. :D

---

### Post by greenstar on 2007-06-01
> **marko_4454 said:**
> If you are saying the volume control icon in the gnome-panel, then just right click it, then preferences. Then choose PCM, that should work. :)

Thanks marko. I was stumped on this one also. Worked like a charm, first time.

Greenstar

---

