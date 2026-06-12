---
title: "I have no sound."
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by infernohit on 2008-03-08
I have a Creative Sound Blaster X-Fi XtremeGamer and X-540 Logitech speakers. Are there any drivers I should be aware of installing?

---

### Post by The Titan on 2008-03-08
I'm not sure about that specific piece of hardware but have you tried using:

```
sudo alsamixer
```

in the terminal, it will allow you to edit the settings for your sound device.

---

### Post by infernohit on 2008-03-08
> **The Titan said:**
> I'm not sure about that specific piece of hardware but have you tried using:

```
sudo alsamixer
```

in the terminal, it will allow you to edit the settings for your sound device.

I put everything to 100 but I still have no sound.

It says the card I'm using is HDA Intel, and the chip is Realtek ALC88.

---

### Post by handy on 2008-03-08
It seems that you have on board sound built into your motherboard as well as the Creative card.

Is that right?

---

### Post by infernohit on 2008-03-08
Yeah, that's right. I don't know how to disable the on-board sound through BIOS. Windows let me choose between Realtek and my sound card.

---

### Post by EKa on 2008-03-08
Hi,

you may find helpful hints using "Comprehensive Sound Problem Solutions Guide".

[http://ubuntuforums.org/showthread.php?t=205449&highlight=Comprehensive+Sound+Problem+Solutions+Guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=Comprehensive+Sound+Problem+Solutions+Guide)


EKa

---

### Post by handy on 2008-03-08
> **infernohit said:**
> Yeah, that's right. I don't know how to disable the on-board sound through BIOS. Windows let me choose between Realtek and my sound card.

Do you have any use for the on board sound, if not you should go into the BIOS & turn it off?

If you want I can help you do that?

---

### Post by handy on 2008-03-08
[***_This link will take you through your problem of multiple sound cards, it is the best solution for your problem._***]("http://ubuntuforums.org/showthread.php?t=205449")

[Edit:] Sorry the EKa posted the same link. :redface:

---

### Post by infernohit on 2008-03-08
> **handy said:**
> Do you have any use for the on board sound, if not you should go into the BIOS & turn it off?

If you want I can help you do that?

Yeah, sure. I have no use for on-board sound if Ubuntu supports my sound card.

---

### Post by handy on 2008-03-08
> **infernohit said:**
> Yeah, sure. I have no use for on-board sound if Ubuntu supports my sound card.

You will get a healthier result if you use [***_the how-to_***]("http://ubuntuforums.org/showthread.php?t=205449&highlight=Comprehensive+Sound+Problem+Solutions+Guide"), you will also learn about sound, Linux & your computer.

---

### Post by infernohit on 2008-03-08
Thanks, I'll look through it.

---

### Post by infernohit on 2008-03-18
It didn't help. I couldn't find my card on ALSA.

Am I stuck with no sound until Creative comes out with Linux drivers?

---

### Post by infernohit on 2008-03-19
Bump.

---

### Post by infernohit on 2008-03-20
I'd like to listen to music again. :(

---

### Post by infernohit on 2008-03-21
Going to bed. Hopefully they'll be some new replies when I wake up.

---

### Post by infernohit on 2008-03-24
Is there any way to get my sound card working? I want to be able to listen to music under Linux. ;___;

---

