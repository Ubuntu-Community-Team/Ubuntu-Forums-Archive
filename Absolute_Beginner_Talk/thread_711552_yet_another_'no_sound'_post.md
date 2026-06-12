---
title: "yet another 'no sound' post"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by manicmailman on 2008-02-29
hey folks... sorry for the latest 'no sound' post... but the posts i checked seem card specific, and im not experienced enough to take that info and modify for my problem/card...

my sound is dead, nothing working... audigy....

where do i start? what do i do? i have inboard nvidia is that a problem?

i will be back in a few hours, so im sorry if i dont reply right away...

thanks

---

### Post by herbster on 2008-02-29
First thing is, disable onboard sound in your system BIOS.

Then when you're back in Ubuntu, you want to see that your card is being seen. Paste the output of the following:

```
lscpi -v
```

and

```
cat /proc/asound/cards
```

If your card is shown in the output, you want to go to the Gnome volume mixer (right-click the volume icon on your panel and hit properties) and ensure that the mixer levels aren't muted.

---

### Post by benerivo on 2008-02-29
You could also try disabling the 'Audigy digital output jack' in the switches section of the sound mixer window. I have an Audigy soundcard and that fixed it. I have seen others with the same problem.

---

### Post by arimaniac on 2008-03-03
Hi there

I've wrote a complete HOWTO on disabling your on-board card.

[http://ubuntuforums.org/showthread.php?t=712908]("http://ubuntuforums.org/showthread.php?t=712908")

Please reply with your
comments to improve the HOW TO...

Hope it helps....

---

### Post by superprash2003 on 2008-03-04
try this..may help [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

