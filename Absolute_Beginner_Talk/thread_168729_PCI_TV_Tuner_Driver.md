---
title: "PCI TV Tuner Driver??"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by MHlavsa on 2006-05-01
Hey all,

I have a PCI TV Tuner Card (PCI TV input adapter) that in windows, works fine but has no sound.  I wanted to know if anyone had heard of any drivers for Ubuntu, in hopes that the sound would work here so that I could actually use it.  The company that it is put out by is called Norwood Micro, but aparently it is a crap company because I can't even find a site for them (to call tech support).

Any info would be much appreciated!

---

### Post by christhemonkey on 2006-05-01
Does the  card work at all?

What is the output of ```
lsmod | grep bttv 
```

If that gives no output, then you might need to load the bttv module.

```
sudo modprobe bttv 
```

As for the sound, my TV card has a cable that (still!) needs connecting to my sound card to give any sound.

---

### Post by MHlavsa on 2006-05-02
I did have to load the bottom code before, afterwards the top output:

~$ lsmod | grep bttv
bttv                  141456  0
firmware_class          9472  1 bttv
i2c_algo_bit            8584  2 bttv,cx88xx
video_buf              19844  3 bttv,cx8800,cx88xx
tveeprom               12568  2 bttv,cx88xx
i2c_core               19728  6 bttv,i2c_acpi_ec,tuner,cx88xx,i2c_algo_bit,tveeprom
v4l2_common             5888  2 bttv,cx8800
btcx_risc               4872  3 bttv,cx8800,cx88xx
videodev                9344  3 bttv,cx8800,cx88xx

---

### Post by Flojomojo on 2006-06-13
I just got one of these cards for free after rebate from CompUSA -- will give it a shot and see what I can do with it. I **think** this is a rebranded bigname card like ...

Check out this link.
[http://www.linuxquestions.org/questions/showthread.php?t=344884](http://www.linuxquestions.org/questions/showthread.php?t=344884)
The poster thinks it's a generic Conexant 23880 card, same chipset as used in an Asus card. If CompUSA or its house brands won't support Linux, perhaps the other companies will.

---

### Post by Drakkor on 2006-06-13
You should also double-click your speaker icon and in the mixer/capture tab,make sure that line in is not muted,if that's how your tv card connects to your sound card.

---

