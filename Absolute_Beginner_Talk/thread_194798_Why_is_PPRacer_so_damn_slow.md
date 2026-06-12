---
title: "Why is PPRacer so damn slow?"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by Raavea on 2006-06-11
Penguin Planet Racer is the slowest thing I have EVER attempted to play. I mean... It takes a minute for me to select 'quit' after opening the thing for a look. It's not like it's a high-end game (I had DS running on here on windows. Went a bit sluggish if it rained, but even then not THIS bad!) or anything.

Could it be my hardware isn't set up? Or is it just (no offence) shoddy programming?

I've got this;
NV34 [GeForce FX 5200]
512MB RAM

And surely it should work? I even tried turning off all the effects (took me about ten bloody minutes..) and it was no change at all in speed.
Can anyone help, or tell me what's going on? I don't really remember much about my specs, as it was a year ago, mebbe more, that I upgraded Bernard..

---

### Post by user1397 on 2006-06-11
> **Raavea]Penguin Planet Racer is the slowest thing I have EVER attempted to play. I mean... It takes a minute for me to select 'quit' after opening the thing for a look. It's not like it's a high-end game (I had DS running on here on windows. Went a bit sluggish if it rained, but even then not THIS bad!) or anything.

Could it be my hardware isn't set up? Or is it just (no offence) shoddy programming?

I've got this said:**
> 
512MB RAM

And surely it should work? I even tried turning off all the effects (took me about ten bloody minutes..) and it was no change at all in speed.
Can anyone help, or tell me what's going on? I don't really remember much about my specs, as it was a year ago, mebbe more, that I upgraded Bernard..
does any other game or program act as sluggish as this one?

---

### Post by caserio on 2006-06-11
Hi,

You need nvidia-glx installed.
PPRacer runs fine here.

---

### Post by Raavea on 2006-06-12
NVidia glx?

 o.O Okies. *runs off to the wiki*

---

### Post by mostwanted on 2006-06-12
Nvidia GLX = the proprietary Nvidia drivers that support 3D graphics acceleration. The open source Nvidia drivers do not support this unfortunately.

---

### Post by JanVH on 2006-06-12
If

```
glxinfo | grep "direct rendering"
```

says no, you're hardware isn't installed properly.

---

### Post by Raavea on 2006-06-12
*boggles*

 I installed it. My computer is already faster just doing desktop stuff!
(Though restarting X server killed my screen just like installing dapper did. Ya think after eight-odd years I should get a new one? :lol:)

 Thanks everyone~ I'm off to try this out. ^_^

---

### Post by someusernoob on 2006-06-12
[QUOTE=JanVH]If

```
glxinfo | grep "direct rendering"
```

says no, you're hardware isn't installed properly.[/QUOTE]
Unless youre using Xgl. Then direct rendering wont work, so the answer will be no even when your hardware is installed properly.
See: [http://en.opensuse.org/Xgl#Frequently_Asked_Questions_.28FAQ.29](http://en.opensuse.org/Xgl#Frequently_Asked_Questions_.28FAQ.29)

---

