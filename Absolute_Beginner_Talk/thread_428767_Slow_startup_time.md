---
title: "Slow startup time"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Spudnip on 2007-04-30
I installed Ubuntu 7.04 for the first time a few days ago and I've had no major problems so far, which is great. However, during bootup, the progress bar pauses midway for about a minute before resuming normally again. I'm just wondering why there is such a long pause and if there's anything I can do about it. Attached is my boot chart. Any help is appreciated, thanks.

---

### Post by mejy on 2007-04-30
Modrpobe shouldn't be running for that long I believe - it looks like it's timing out on some misbehaving device or driver.  Try unplugging all network & usb devices, and if that solves it plug them back in one by one.  This may be worth reporting on launchpad if it always happens on fresh installs.

---

### Post by Spudnip on 2007-05-01
> **mejy said:**
> Modrpobe shouldn't be running for that long I believe - it looks like it's timing out on some misbehaving device or driver.  Try unplugging all network & usb devices, and if that solves it plug them back in one by one.  This may be worth reporting on launchpad if it always happens on fresh installs.

Tried it but there was no difference I'm afraid. I found out how to enable verbose mode when booting up, and it hangs at "Loading hardware drivers". Can anyone advise me on how to figure what's wrong? This is my first time on Linux so I don't know how to go about debugging this myself.

---

### Post by dansolo on 2007-05-02
Have you got a wireless card?

If yes, try writing on a console:

```

sudo update-rc.d -f networking remove
sudo update-rc.d networking defaults 99

```

Probably you'll solve

---

### Post by Fr33d0m on 2007-05-02
Not to pick at nits, I think of startup as after login... prior to that I think of as boot.  This is important to me because I'm trying to trouble shoot why I get to see the upsplash for over 2 minutes after login.

So I wonder if there is some other term I need to search for... what is the proper terminology?

But mostly I'm wondering about why it takes so long to start after I log in. :confused:

---

### Post by Spudnip on 2007-05-04
> **dansolo said:**
> Have you got a wireless card?

If yes, try writing on a console:

```

sudo update-rc.d -f networking remove
sudo update-rc.d networking defaults 99

```

Probably you'll solve

Yes, I do have a wireless card.

Thanks for the help, but what will the commands you posted actually do? And how would I go about reversing them if something goes wrong? I'm just a bit hesitant to blindly type commands into the console without knowing what they mean.

---

