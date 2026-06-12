---
title: "Ubuntu willnot start properly."
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by XLostSpartanX on 2007-01-24
So I just downloaded Ubuntu 6.10 and installed it on my laptop. Everything went great.  Next up I went to put it on my desktop and it wont start. 

When I choose either "Start or install Ubuntu", or "Start or install Ubuntu in safe graphics mode", it just won't come up.  I see deep blue screen with a few diagonal lines going though it.

Also, one more question.  I am running a raid0 setup on it too.  I was just wondering if Ubuntu would be able to see that.

---

### Post by XLostSpartanX on 2007-01-24
People please help... I need to use my computer.

---

### Post by meng on 2007-01-24
1. Be patient. Nobody likes a bumper, especially after just 15 minutes.
2. Post your system specifications please.

---

### Post by jbayone on 2007-01-24
You can try changing to a lower resolution; I think by pressing F4 on the splash screen when you choose to "start or install ubuntu".

---

### Post by XLostSpartanX on 2007-01-24
> **meng said:**
> 1. Be patient. Nobody likes a bumper, especially after just 15 minutes.
2. Post your system specifications please.

Sorry.  

nvida 7600gt
P5NSLI
intel E6300

> **jbayone said:**
> You can try changing to a lower resolution; I think by pressing F4 on the splash screen when you choose to "start or install ubuntu".

ok i will try that.

---

### Post by XLostSpartanX on 2007-01-24
> **jbayone said:**
> You can try changing to a lower resolution; I think by pressing F4 on the splash screen when you choose to "start or install ubuntu".
Ok.  So I did that and it worked.  Now when I reboot I get the same screen.  What now?

---

### Post by teitunge on 2007-01-24
When you have logged into your system, type sudo dpkg-reconfigure xserver-xorg in your terminal. Then you could set up your x-server, and that information should be stored.

---

### Post by XLostSpartanX on 2007-01-24
> **teitunge said:**
> When you have logged into your system, type sudo dpkg-reconfigure xserver-xorg in your terminal. Then you could set up your x-server, and that information should be stored.

I can't login.  I get that screen as soon as Ubuntu finishes booting up.

---

### Post by teitunge on 2007-01-24
Press alt+f2 and log in though the text-based interface. Then you should be able to log in.

---

### Post by XLostSpartanX on 2007-01-24
> **teitunge said:**
> Press alt+f2 and log in though the text-based interface. Then you should be able to log in.

I have no clue what you mean by that, but I did press ESC when booting up to get to the grub menu.  I then went into the recovery and did the xserver thing. 

It worked, so I guess I did it right.

---

### Post by teitunge on 2007-01-24
Whops, my language kind of went crazy there :)
Good job, so now everything is cool?

What I mean was to log in though the text-based interface. If you press alt+f2 at the login-window, you will turn to one of the other log-in windows, without x-server running.

---

### Post by XLostSpartanX on 2007-01-24
> **teitunge said:**
> Whops, my language kind of went crazy there :)
Good job, so now everything is cool?

What I mean was to log in though the text-based interface. If you press alt+f2 at the login-window, you will turn to one of the other log-in windows, without x-server running.
Haha ok.  Well now I just need to know how to get the 7600gt drivers installed and the correct res set.  Can you help me what that?

---

### Post by jbayone on 2007-01-24
Have you tried the envy script?  There's a link in my signature.

---

### Post by XLostSpartanX on 2007-01-24
> **jbayone said:**
> Have you tried the envy script?  There's a link in my signature.

Trying it now.

---

### Post by XLostSpartanX on 2007-01-24
Amazing.  I got all that done and it works great... now about sound.  

I was getting sound out from a coaxial cable in Windows.  Now I am getting no sound.  Any fixes?

Thanks,
Nick

---

### Post by jbayone on 2007-01-24
Sorry man, I have no idea about the sound thing.  I've got enough sound problems of my own with a usb phone.

---

### Post by XLostSpartanX on 2007-01-24
> **jbayone said:**
> Sorry man, I have no idea about the sound thing.  I've got enough sound problems of my own with a usb phone.

Hmm ok.  Maybe someone else can help,

---

### Post by jbayone on 2007-01-24
Have you checked out the comprehensive sounds guide?  [http://www.ubuntuforums.org/showthread.php?t=205449]("http://www.ubuntuforums.org/showthread.php?t=205449")

I did a quick search on the forums and someone had a similar problem they fixed using ALSA mixer.

---

### Post by XLostSpartanX on 2007-01-24
Oh god.  This is just getting worse and worse.  I had everything with the graphics set up and working... then I install some updates.  Then when I reboot it tells me that it failed to start the xserver and that is now disabled.  Now what?

---

### Post by jbayone on 2007-01-24
Damn, you can sudo dpkg-reconfigure xserver-xorg and choose the nvidia driver, or the nv driver if that doesn't work.

---

### Post by XLostSpartanX on 2007-01-24
> **jbayone said:**
> Damn, you can sudo dpkg-reconfigure xserver-xorg and choose the nvidia driver, or the nv driver if that doesn't work.
Ok.  Just tried that.  Hope it works.

---

### Post by XLostSpartanX on 2007-01-24
K it worked.  Now to redo the nvidia thing.

---

### Post by XLostSpartanX on 2007-01-24
Ok this just keeps getting worse and worse.. I can't handle much more.  I got the graphics working again, but now my mouse is screwing up.  I have tried two differnet mice and they both just freeze after a few minutes and I have to unplug it then plug it back in again.  Not to mention the sound.

---

### Post by jbayone on 2007-01-24
Is it just the mouse that freezes up or everything?  There's a common problem with Nvidia cards where everything will freeze except for the mouse, but this may be related to the nvidia driver also.  Hopefully I haven't steered you in the wrong direction.

---

### Post by jbayone on 2007-01-24
Here is a thread with the same issue: [http://www.ubuntuforums.org/showthread.php?t=280033&highlight=mouse+freezes]("http://www.ubuntuforums.org/showthread.php?t=280033&highlight=mouse+freezes")

---

