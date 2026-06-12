---
title: "Core 2 Duo: newbie question"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by anemon on 2006-12-28
Hi!

I have a question that is pretty basic, but I haven't been able to find the info anywhere. I recently built myself a new computer, a Core 2 Duo on an Asus P5B-VM motherboard, and decided to give Ubuntu a try -- so I'm running Edgy on one partition, XP on the other (although I seem to never use it). 

The question is: how do I know that all my hardware is running on full capacity? I've seen a lot of people talking about the 64 bit Ubuntu being unstable and all, so I decided to go with the old 32 bit version: this will obviously slow things down a bit, but I'm sure it's worth it for the time being. But when I check my Device manager, my processor shows up as "unknown". Is this common, or does it imply that the OS doesn't recognize the processor type, and is perhaps running in some kind of generic, slower mode? The same thing goes for my RAM: how do I know that the OS can access all of it? I.e. where can I see the basic hardware facts, like the Properties window of "My computer" in XP?

For all of you who know the technical aspects of Ubuntu, this probably sounds like the rantings of a madman. Anyhow, please take the time to ease my worried mind... ;) 

Best / A.

---

### Post by bollix47 on 2006-12-28
I get the same when running device manager but using lshw the info is more complete.

Open a terminal (applications - accessories)

type:

```
sudo lshw 
```

---

### Post by pseudonym on 2006-12-28
In addition, you may want to check out the wiki on [Core 2 Duo support]("https://wiki.ubuntu.com/Core_2_Duo_Support?highlight=%28core%29%7C%28duo%29") and the [64-bit users forum]("http://www.ubuntuforums.org/forumdisplay.php?f=134") .

When I built my 64-bit machine, I thought I'd give 64-bit Ubuntu a try. I, and many other users, have found it to be perfectly stable. In fact, I was originally just going to test it out, but I've actually just stuck with it.

As far as performance goes in a 64-bit distro, you don't get much extra in 32-bit apps. The extra width starts to count in processor-intensive 64-bit apps, though. for instance, I can demux, remux, and recode digital video much faster in 64-bit.

The only problem is there are some things like browser plugins and windows codecs which aren't supported, or only partially, in 64-bit. Fortunately, there are a few ways you can get around this and run those apps anyway. It adds a small amount to your learning curve to get this going, but not much.

---

