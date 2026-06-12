---
title: "Why is the live DVD so laggy?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Mattrix on 2008-04-08
I've been fiddling round with ubuntu recently after using other distributions on and off for over a year and wanting a change.

My current experience of it has been using a live DVD (and ubuntu is the first live DVD distribution I've used) and it's not been that pleasant.

When I boot ubuntu from a live DVD, any apps I open, open minutes later. So I can be in the middle of using firefox and the calculator can pop up, despite me trying to load it up before I opened firefox.

Is this normal?

My PC has an Amd 4600 64-bit 2.4ghz dual core processor with 4 gig ram so I don't think it's the machine that's causing it. :(

My experience of it when installed won't be like this will it?

---

### Post by Crafty Kisses on 2008-04-08
Sometimes it's just laggy, you may want to try installing the full system and see if you still experience the issue, I only have 2GB of RAM and it never went slow for me.

---

### Post by forrestcupp on 2008-04-08
It's because it has to load every program you open from the CD/DVD rather than from your hard drive.  If you were to install Ubuntu to your hard drive, it would be fast.

---

### Post by amazingtaters on 2008-04-08
You're running the untire OS entirely out of RAM. That's generally the problem. I've never had it as bad as you're describing, but it's not unheard of. Did you build the box yourself, or is from some OEM? If you did build it yourself, are you sure you have the RAM set up correctly (eg, if you have 2 2gig sticks of RAM are the the same speed, have the same CAS latency, installed in Dual Channel configuration, etc). Anyway, it shouldn't be like that when you install.

---

### Post by Mattrix on 2008-04-08
> **amazingtaters said:**
> You're running the untire OS entirely out of RAM. That's generally the problem. I've never had it as bad as you're describing, but it's not unheard of. Did you build the box yourself, or is from some OEM? If you did build it yourself, are you sure you have the RAM set up correctly (eg, if you have 2 2gig sticks of RAM are the the same speed, have the same CAS latency, installed in Dual Channel configuration, etc). Anyway, it shouldn't be like that when you install.

It's custom (I wouldn't buy an OEM one), but everything's set up fine and works well in other distros.

---

### Post by amazingtaters on 2008-04-08
> **Mattrix said:**
> It's custom (I wouldn't buy an OEM one), but everything's set up fine and works well in other distros.

You should be ok then. It's just things loading slowly of the cd I'd say (with 99.999999999999999% certainty). Once you've installed, you'll be blazing fast.

---

### Post by Whiffle on 2008-04-08
Its because you're reading from a cdrom/dvd.  The fastest cdroms read less than 10MB/s, while even my old crappy hard drive gets 55 or so.   That will make any setup run slow.

---

### Post by Therion on 2008-04-08
> **Mattrix said:**
> ... When I boot ubuntu from a live DVD, any apps I open, open minutes later. So I can be in the middle of using firefox and the calculator can pop up, despite me trying to load it up before I opened firefox.

Is this normal?

My PC has an Amd 4600 64-bit dual core processor with 4 gig ram so I don't think it's the machine that's causing it. :(
I run a home-brewed machine with an AMD 4200+ X2 64-bit proc and 2GB of system RAM and I've always found the LiveCD's/DVD's to be pretty snappy.  I'm wondering if maybe you just got a lousy burn or something simple like that.  Yes, the OS is running off nothing but the optical and system RAM, but even so I was stunned at how fast Hardy was off the LiveCD.  Your proc whoops mine and you've got twice the RAM...  

I think you should consider reburning your .iso -- burn it nice and slow -- and try again; because no, what you're seeing is not normal in my experience.  Not even for a LiveCD/DVD.

---

### Post by SlappyPappy on 2008-04-08
My computer is about 1/8 as fast etc. as yours and the LiveCD is very snappy for me. No lag at all. I've been using gparted to tweak drives and it works great on the LiveCD. I can't explain your slowness but I can tell you it's not indicative of my results.

---

### Post by Mattrix on 2008-04-08
> **Therion said:**
> I run a home-brewed machine with an AMD 4200+ X2 64-bit proc and 2GB of system RAM and I've always found the LiveCD's/DVD's to be pretty snappy.  I'm wondering if maybe you just got a lousy burn or something simple like that.  Yes, the OS is running off nothing but the optical and system RAM, but even so I was stunned at how fast Hardy was off the LiveCD.  You're proc whoops mine and you've got twice the RAM...  

I think you should consider reburning your .iso -- burn it nice and slow -- and try again; because no, what you're seeing is not normal in my experience.  Not even for a LiveCD/DVD.

I'll try that, thanks.

---

### Post by Ieatmacs on 2008-04-08
Live disks are slow because of the access speeds of a disk drive are less than that of a hard drive. But they don't tend to be that slow, perhaps it's a corrupt iso or something.

Just install it to your machine. It should be quite fast with that set-up.

---

