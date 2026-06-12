---
title: "noob with nvidia card on Live CD 6.10"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Dellasaurus on 2008-01-31
I'm fairly new to this, I've just gotten a Ubuntu for Dummies (yeah I know) and I've started tinkering with Ubuntu 6.10  and I've had to resort time after time to using my Dell internal card, I have a Nvidia GeForce MX4000 card. When I use the card, I get the initial boot screen for Ubuntu then I get a black screen, nothing else. I don't know what I'm doing wrong here, and I'm using the Live CD, I haven't done an install yet.  I'd like to set up a dual boot system down the road, one side my Win 98SE, or XP (once I get a larger HD) and the other linux.

---

### Post by overdrank on 2008-01-31
> **Dellasaurus said:**
> I

HI and welcome, we will need a little more info. :)

---

### Post by aeiah on 2008-01-31
have you tried booting with the safe graphics mode? (if ver 6.10 has this)

other than 6.10 being the version you got with the book, is there another reason why you arent using a newer version of ubuntu? (slow download speed, no cd burner etc)

---

### Post by Dellasaurus on 2008-01-31
I actually have a live 7.10 CD, that I burned myself. I thought I would use the earlier one due to the book.

But I'll try the safe mode see if that kicks.

---

### Post by oedha on 2008-01-31
why don't you just use the 7.10 ?
i know you have 6.10 book but it's quiet similar though
and boot just like what aeiah #3 said 

regards;
~E~

---

### Post by alfoness on 2008-01-31
> **Dellasaurus said:**
> I'm fairly new to this, I've just gotten a Ubuntu for Dummies (yeah I know) and I've started tinkering with Ubuntu 6.10  and I've had to resort time after time to using my Dell internal card, I have a Nvidia GeForce MX4000 card. When I use the card, I get the initial boot screen for Ubuntu then I get a black screen, nothing else. I don't know what I'm doing wrong here, and I'm using the Live CD, I haven't done an install yet.  I'd like to set up a dual boot system down the road, one side my Win 98SE, or XP (once I get a larger HD) and the other linux.

Well, I'm not the most experienced Linux user, but I'm able to use it effectively.

If I were in your situation, I would, when the boot screen for LiveCD comes up (which you can select start/install ubuntu, start in safegraphics mode, etc), press F6, and type at the end of the string of code:

noapic irqpoll noirdebug

Remember, don't modify anything in that box which appears. Enter that string after the last hypen (-)

This should modify a configuration file to allow you to boot the LiveCD, but the screen resolution may be incorrect, and things may not display properly. Once ubuntu is installed you'll have to configure the driver to allow video acceleration.

I hope this helped. It was my solution to using my Nvidia GeForce 6150 card to boot a LiveCD.

edit -  as others have said, I would recomment using ubuntu 7.10, as it's most up to date and would be easier to set up with your graphics card.

---

### Post by Dellasaurus on 2008-02-01
I'm using the 7.10 Live CD - I'm still getting a blank screen after the main boot menu. I've tried that bit of script and still nothing. What's odd is the Nvidia card and my Intel internal card both show up on the system, and I can install the Nvidia card driver and it prompts for restart.

I can't do that on Live CD right?

---

### Post by Dellasaurus on 2008-02-04
I'm using the 7.10 Live CD, and I keep getting the black screen of death when I plug my monitor into the Nvidia card, but when I plug into the Intel controller, its fine. It boots up no problems. I haven't done an install because I want to see if I can run the Nvidia card with the Live CD. Or can't I activate those drivers when I'm running the Live CD?

Help.

---

