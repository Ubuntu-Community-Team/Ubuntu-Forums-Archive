---
title: "MPlayer on hardy (on imac G3)."
date: 2008-11-01
forum: Apple Hardware Users
---

### Post by milkwood on 2008-11-01
Perhaps G3 users can not use listed MPlayer.
Here is my tip.

You search mplayer-1.0~rc1.orig.tar.gz(gutsy version) by ubuntu package search and etc,and download it.
And extract it to /home/... or wherever you prefer.
And cd /mplayer-1.0~rc1(open folder where you extracted the source).
And type command ./configure --disable-altivec.
Then follow "make" and "make install"(just type command.No need "").
This finishes installing MPlayer.
With My 400mhz computer it takes 3 or 4 hours.Be patient.
But only doing this is relatively useless.
Indeed,What I want to recommend you is SMPlayer.
You can just install smplayer by using repositroy or whatsoever.
After install smplayer,open preferences and select mplayer you compiled
(and you may have to choose "xv" and "oss" as Output drivers).
Then just let's enjoy it's functions.
SMPlayer can control the pitch of speed of movie or sound.
That's very useful,for example, for learners learning foreign languages.
And you can select many other options of MPlayer easily.

I hope this tip will eliminate anyone's woes.

Thanks.

milkwood.

---

### Post by cyberdork33 on 2008-11-01
Just a tip as I notice you do this each time you post, you have to put commas between your different tags otherwise they all become one big tag.

---

### Post by milkwood on 2008-11-01
Thanks for your tip cyberdork33!
I'll never notice about that without your notice.
I'm wondering how did you know that?
Anyway,thanks.

milkwood.

---

### Post by cyberdork33 on 2008-11-02
> **milkwood said:**
> Thanks for your tip cyberdork33!
I'll never notice about that without your notice.
I'm wondering how did you know that?
Anyway,thanks.

milkwood.
i do a lot of tagging.

---

### Post by milkwood on 2008-12-03
Sorry guys:(.
I've been making a mistake.
If you try to compile something you should do "sudo apt-get build-dep" first of all.
I should have done so.It was all dependencies matter.
In this case,I should have typed "sudo apt-get build-dep mplayer" in terminal to get all-needed-dependencies before compiling.
Today I've succeeded in installing the-newest-mplayer.
You know,not knowing is good,but to know what You were not knowing is better.And a bit bitter.
By the way,I agree that this forum covers Debian users.
Because Ubuntu had ended to support for PPC users and others.
To say about me,I'll give up Ubuntu at my current version(hardy).
To try new is very annoying for my current computer.
Next two years and a few months is enough for me to change my course(even if it were one year) .
I could be using Mac or Windows or other Linux Distributions.
Anyway I would thank Ubuntu in advance,and many other contributers;). 
I wish the rest of my life with Ubuntu is much glorious.

Thanks.

milkwood):P.

---

### Post by milkwood on 2008-12-03
And another way,I can just continue using Ubuntu on another computer.
I've been thinking if I were using Windows I would use Windows by now.
And if I were using latest Mac I would use latest Mac OS X.
Then why am I using Ubuntu on that old machine right now?
Because,I think,it's my way.
You know about OS's share?
I'm just wondering why you and me met each other despite such a statics.
I'd thought before that these old computers and free distributions may be useful somewhere.
Can you believe that I've been trying to learn other languages and cultures by using "the-latest-information-technology"?
It's very out-of-date.

What I want to say is...

What do you want to do with that?

milkwood):P.

---

