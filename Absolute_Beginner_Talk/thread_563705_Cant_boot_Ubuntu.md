---
title: "Cant boot Ubuntu"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by docfl on 2007-09-30
I installed with no problem, ran the updates. every thing ran fine for about 36 hours. Now when I boot I get a message of: kinit resume image, doing normal boot....
Then I get Ubuntu 7.04 don-laptop tty1
then it asks for my log in info. After that it goes to what looks like the terminal prompt.
I'm new at Ubuntu, but from what Ive seen so far it looks good to me, planing on removing my Vista partition once I get everything working again.
I have a Gateway MX 6431 AMD 64 notebook if that helps.
Thanks in advance
docfl

---

### Post by overdrank on 2007-09-30
> **docfl said:**
> I installed with no problem, ran the updates. every thing ran fine for about 36 hours. Now when I boot I get a message of: kinit resume image, doing normal boot....
Then I get Ubuntu 7.04 don-laptop tty1
then it asks for my log in info. After that it goes to what looks like the terminal prompt.
I'm new at Ubuntu, but from what Ive seen so far it looks good to me, planing on removing my Vista partition once I get everything working again.
I have a Gateway MX 6431 AMD 64 notebook if that helps.
Thanks in advance
docfl

Hi and welcome, at the grub to select the OS between Windows and Ubuntu you should have more than one choice under ubuntu. Try booting to a different kernel like a older one down the list and not recovery mode.

---

### Post by BLTicklemonster on 2007-09-30
At the prompt, can you log in by entering your user name and password, and still be at the prompt?

Sounds like maybe you're locked out of X by the upgrade. Are you using video drivers you installed for your card that aren't ones you got from synaptic? (might not be a problem, I'm not sure)

From the prompt, if you can log in, try this:

sudo dpkg-reconfigure xserver-xorg

yes your way through stuff, but check the vesa option for video drivers.

Once back to the prompt, 

startx

That ought to get you to the desktop, and you can take care of your problems from there.

The new Gutsy has a failsafe to keep you from being locked out of your desktop. It will be ready in October, so don't give up!

I hope that this gets you to where you can fix your problems.

(oh, and as you go along, whenever you find something useful, pm yourself the instructions or a link to the thread. that way, if you have problems, and you can get online, you can look over the answers you already found, and make notes to get your ubuntu running again)


Or do what overdrank said, lol

---

### Post by docfl on 2007-09-30
Ok It does offer me boot options, and they all go to the terminal screen. I typed in the startx and it allowed me to boot Ubuntu  normally.
BLTicklemonster, The video dosent seem to be a problem, the display looks fine. However now I am noticing I have no sound.  I will post another question in the forum for that issue.
Thanks again
docfl

---

