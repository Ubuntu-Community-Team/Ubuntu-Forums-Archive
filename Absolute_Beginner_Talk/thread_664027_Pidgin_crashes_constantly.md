---
title: "Pidgin crashes constantly"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by Jinx-Wolf on 2008-01-10
Not sure if this is posted already, but I didn't see this exact issue (sorry if it is)

I'm at work so I can't post any terminal outputs, or test anything, but I wanna know if anybody else has heard of this issue, or if anybody has a fix for it.

The problem is that Pidgin crashes, but only when somebody  does something. By that I mean, If I try to send a message, I hear the noise, and see half of the message, but then it freezes and goes black/white. Same goes if somebody is trying to send me a message.

Now, it doesn't do this all the time. In fact, I can go for hours IMing somebody, and other times it's the first message sent that crashes it.

Thanks in advance.

---

### Post by felicity on 2008-01-10
Are you using any special plugins? Do you think your problem may be related to a specific network?

---

### Post by Jinx-Wolf on 2008-01-10
I'm not positive, but it seems to only happen with AIM, but I don't use the other ones that often.

I use guifications only for login and logout messages.

---

### Post by yarg on 2008-01-13
Doing this to me too. Very annoying. Not using any additional plugins here, just trying to use AIM protocol. Can't have a conversation of more than 10 lines most of the time before Pidgin randomly closes. This app never was this buggy while it was known as Gaim. I wonder if they call it Pidgin because they know people will want to shoot it in frustration?

---

### Post by EXCiD3 on 2008-01-17
I just started getting this problem. Every time i send/receive a message in AIM pidgin crashes. It was working perfectly fine yesterday then randomly started crashing. I have no idea what could be causing this. I'm going to try compiling from source and removing all the configuration files to see if that fixes anything.

---

### Post by erwall on 2008-01-23
Had the same problem.  I'd installed the MusicTracker plugin and after poking around on the net was able to find out that this was causing the problem.  Disabled the plugin and Pidgin hasn't crashed since.  Hope this helps someone.

---

### Post by sports fan Matt on 2008-01-23
I haven't had this issue, but I am using Pidgin 2.3.1, but not sure if that matters or not.  Sending an AIM Message in 2.3.1 works fine best I can tell

---

### Post by nikoPSK on 2008-01-23
> **EXCiD3 said:**
> I just started getting this problem. Every time i send/receive a message in AIM pidgin crashes. It was working perfectly fine yesterday then randomly started crashing. I have no idea what could be causing this. I'm going to try compiling from source and removing all the configuration files to see if that fixes anything.

gosh, that's odd.... Could you run this command in the terminal and give the output once it crashes? :)

```
pidgin
```

---

### Post by EXCiD3 on 2008-01-23
You know...i realized i had just installed the MusicTracker plugin...disabled it and what do you know...it works great yet again. :D

---

### Post by ep3hatchsi on 2008-01-25
having this same annoying problem! will see if i have any plugins when i get home.

---

### Post by Anxiety35 on 2008-06-15
This started happening to me recently as well, and I can confirm that MusicTracker seems to be causing the problem.

It only crashes however when the player is set to "Auto-detect." If I tell it what player to look for, it doesn't seem to crash.

Hope it helps some people.

---

