---
title: "Sound Card problem"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by JCM45 on 2008-03-30
when i installed ubuntu studio my sound didnt work.  my OS says that its unmuted and ot top volume.  however on my computer (HP Laptop) the mute button is red meaning it is muted.  when i press the button nothing happens.  how can i fix this.  also complete noob at linux.

---

### Post by JCM45 on 2008-03-30
come on guys.  i need some help.  isnt this the help forum?

---

### Post by JCM45 on 2008-03-30
bump

---

### Post by JCM45 on 2008-03-30
anyone there to help?

---

### Post by rkd on 2008-03-30
Well, it might help to tell us what model of HP laptop you have and which version of Ubuntu you are using.

If it is a Pavilion DV2000 series, DV6000 series, DV6500 series, or DV9000 series, this page has a lot of suggestions:

[http://aldeby.org/blog/?page_id=87](http://aldeby.org/blog/?page_id=87)

In particular, for getting sound to work, he says```
sudo apt-get install linux-backports-modules
```will do the trick.  Be a little cautious with his other advice.  I'm sure most of it is good, but at one point, he mentions using Envy, but Envy has been shown to introduce latent problems that don't show up until you try to upgrade software.  (To be fair, he does say you don't really need to use Envy, but he still talks about using it.)

This thread in the forums:

[http://ubuntuforums.org/showthread.php?t=693303](http://ubuntuforums.org/showthread.php?t=693303)

describes a long struggle someone had with Gutsy on a DV2000.  Ultimately, she solved it by removing the laptop's battery then putting it back in again.  Something in the audio hardware needed to be completely powered off before it would get into a state that Ubuntu could use it.

Who knows what the answer to your problem will turn out to be?

---

### Post by JCM45 on 2008-03-30
wow thank you.  i will try this and hope it works.  my laptop is a dv 6780 and i have ubuntu studio and it says its 7.10.  i will see if it worked.  and thanks again.

---

