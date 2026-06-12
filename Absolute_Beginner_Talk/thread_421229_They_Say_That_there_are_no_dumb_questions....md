---
title: "They Say That there are no dumb questions..."
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by bagadonitz on 2007-04-24
I'm having a hell of a time getting my java IDE (Intellij Idea) running in my Feisty Install.

it seems the issue is related to 32 bit vs 64 bit.  I'm on a 64 bit platform but I'm sure I installed 32 bit iso.

Is there some way I can see exactly which installer I used.  I need to know if I'm running and 32 bit or 64 bit version of Feisty Fawn.

Yes, I know stupid.  But I had a hell of a time installing it, had cd's for 32 bit and 64 bit both live and alternate and damned if I can remember which one eventually worked.

---

### Post by jem7v on 2007-04-24
I think that
```
uname -r
```
will tell you what kernel you are using, and if it ends in some variation of 64, you'll be running the 64-bit version.

---

### Post by MetalMusicAddict on 2007-04-24
> **jem7v said:**
> I think that
```
uname -r
```
will tell you what kernel you are using, and if it ends in some variation of 64, you'll be running the 64-bit version.

That might not work because if he's using -generic it will show the same kernel whether its 64 or 32 bit.

---

### Post by pppetter on 2007-04-24
You are right, there are no stupid questions. 

And the command "uname -r" can be executed from a Terminal Applications-->Tools-->Terminal

---

### Post by bagadonitz on 2007-04-24
As predicted...

```

jeff@enghlol:~$ uname -r
2.6.20-15-generic

```

Any other way to get the specifics.

---

### Post by bagadonitz on 2007-04-24
What about this:

```

jeff@enghlol:~$ uname -a
Linux enghlol 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux

```

Does this x86_64 indicated that Ubuntu is 64 bit version or is it just telling me what my hardware is.

---

### Post by bagadonitz on 2007-04-24
Just answered my own question on the last front:

```

jeff@enghlol:~$ uname -m
x86_64

```

  -m, --machine            print the machine hardware name

Sigh.  I guess I'll just have to install again with a known 32 bit version.

---

### Post by hyperair on 2007-04-24
Try going into the folder "/var/cache/apt/archives" and checking the contents. If your deb's have "i386" at the end then your installation should be 32-bit ^^

---

### Post by bagadonitz on 2007-04-24
Thanks.  They are all amd64.  Looks like I'll be installing again.  and I had such a hard time getting grub to dual boot properly.  Hopefully an install of 32 bit will fix my issues otherwise, <gulp>, I'm going to have to try another distro or worse, Vista.

---

### Post by flossgeek on 2007-04-24
Stop panicking, you wont need Vista, and Java is very easy to install on Feisty. I am running it with no issues, infact I always have on all previous versions.

---

### Post by silverglade00 on 2007-04-24
I used the AMD64 version of Feisty Beta for a while. It worked good, but it felt "shaky", like it was just barely holding together. There were also a lot of problems with incompatibilities. All of that went away when I reinstalled the 32 bit version. Hopefully you will have a similar experience.

Just don't put yourself through the pain of Vista. I have it. It's not worth it in my opinion. Sticking with XP is a much better idea. The 3D effects in Vista are just pitiful after you have seen Beryl and Compiz. It runs very slow. My old Emachines sempron 1800 with 512 ram and XP ran faster than my new X2 Turion64 with a gig of ram. It takes about 5 full minutes to boot up to the point it is useable. 

I guess my point is, if 32bit Ubuntu doesn't work, try Mepis or Mandriva. Even better, try PCLinuxOS when they get their hosting issues resolved in a day or two. Just don't go back to the dark side :)

---

### Post by bagadonitz on 2007-04-24
There is no problem with Java.  It seems this one particular java app will not run in a 64 bit jvm and my 64 bit ubuntu won't let me install a 32 bit jvm.  PITA.

---

### Post by bagadonitz on 2007-04-24
Yes I'll install the 32 bit later today.  I thought I had it install but evidently not.

So far I love ubuntu but when it boils down to it, it needs to run one app where I spend 10+ hours a day and so far it won't.

I had a lot of issues getting a dual boot set up with XP and hopefully they won't repeat.

---

### Post by hyperair on 2007-04-24
What is this app that refuses to run in a 64-bit JVM anyway? I've never heard of anything of that sort. Perhaps there's a workaround?

---

### Post by bagadonitz on 2007-04-24
It is a java ide called Intellij IDEA.

I can't say it refuses to run.  It runs but I get a blank screen like it isn't refreshing.  In forums related to me it was suggested to try a 32 bit jvm.  The installers for 32 bit jvms will not install on 64 bit ubuntu.

i386 iso almost done downloading.  wish me luck.

---

### Post by hyperair on 2007-04-24
You wouldn't be running Beryl or Compiz (a.k.a Desktop Effects)  by any chance would you? I hear Java/Swing applications have problems in Beryl and Compiz

---

### Post by bagadonitz on 2007-04-24
I'm not running any of those but I do have the ones built into ubuntu turned on.  I'll turn them off and give it a whirl.

---

### Post by hyperair on 2007-04-24
The ones built into Ubuntu is compiz, actually. You might want to stop the program and restart it. Stuff like Limewire and Frostwire and jEdit also don't work well.

---

### Post by bagadonitz on 2007-04-24
Bless you.  

I turned off desktop effects and the app starts and is all viewable and that stuff typically required for use by non blind users.

Thanks.

---

