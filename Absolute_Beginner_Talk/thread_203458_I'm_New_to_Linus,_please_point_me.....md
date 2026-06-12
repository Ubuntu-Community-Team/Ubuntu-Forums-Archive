---
title: "I'm New to Linus, please point me...."
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by Worbc on 2006-06-25
..in the right direction.

Good morning all let me thank you all ahead of time to any help that you may give me.

I consider myself pretty good on computer (DOS and Windows, building, rebuilding, and some software experience) and I have wanted to experiment with Linux.  As lunch would have it, I found an old Dell Dimension 2350, 2.2gig, 30G HD (will most likely replace soon), 512Meg RAM -- all in all a pretty good machine.  It was in the trash.

So I loaded XP, and everything works great.  Now, I've replaced XP with Linux Ubuntu and need some drivers, I searched this web site for Intel 845G/GL drives and found no threads; hence, the crux of my posting.

Can someone please point me to where (1) I can locate this video driver and (2) where me as a beginner, can read and learn about Linux.  

Warmest regards,

--terry

---

### Post by tonyr on 2006-06-25
Start with the link in my signature.  Also explore the [Ubuntu Wiki]("http://wiki.ubuntu.com").

---

### Post by T700 on 2006-06-25
Using Google and the following search terms (*without *the quotes!) brought up some very promising results:

"Intel 845G/GL linux"

I didn't have time to carefully study them, but from the synopsis, some look good.

Paul

---

### Post by deadgobby on 2006-06-25
1.) [https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)
[https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28video%29](https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28video%29)
[https://help.ubuntu.com/community/FixVideoResolutionHowto?action=fullsearch&context=180&value=video+cards&fullsearch=Text](https://help.ubuntu.com/community/FixVideoResolutionHowto?action=fullsearch&context=180&value=video+cards&fullsearch=Text)
2.) All over the web. There is a VAST amount on howto's on the web. Yet depending what version of Ubie you are using. THe basic commands have not changed.
[http://www.psychocats.net/](http://www.psychocats.net/)
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)
 This is a short list. Welcome to Linux
Gobby

---

### Post by Worbc on 2006-06-25
Thanks, it appears to be sorted and thanks for the links I plan to read them completely.

--terry

---

### Post by az on 2006-06-25
[QUOTE=Worbc].
Can someone please point me to where (1) I can locate this video driver and (2) where me as a beginner, can read and learn about Linux.  

Warmest regards,

--terry[/QUOTE]
 I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
        i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),

that would be the i810 xorg driver that is part of xorg.  It is GPLed.  You already have it.  You shold already be running it.

What is the problem you have with your video?

---

### Post by Worbc on 2006-06-26
it appears to working fine now.  thanks.

---

