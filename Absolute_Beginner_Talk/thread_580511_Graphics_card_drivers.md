---
title: "Graphics card drivers?"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by spyker3292 on 2007-10-18
When I get my new card (in the mail) will I have to uninstall any drivers? I know on windows I will just have to go to add/remove hardware but do I need to do anything like that in Ubuntu? I never installed anything. How can I install new drivers for the new card?

---

### Post by overdrank on 2007-10-18
> **spyker3292 said:**
> When I get my new card (in the mail) will I have to uninstall any drivers? I know on windows I will just have to go to add/remove hardware but do I need to do anything like that in Ubuntu? I never installed anything. How can I install new drivers for the new card?

HI and that will depend are you using a ATI card and switching to a Nvidia Card? You will most likely have to reconfigure your xorg with the command ```
sudo reconfigure xserver-xorg
```:popcorn:

---

### Post by mrvertigo on 2007-10-18
dang...... i was explaining this untill i saw overdrank answered it :P darn you jk go ubuntu!

---

### Post by spyker3292 on 2007-10-18
> **overdrank said:**
> HI and that will depend are you using a ATI card and switching to a Nvidia Card? You will most likely have to reconfigure your xorg with the command ```
sudo reconfigure xserver-xorg
```:popcorn:

Ya I am switching from an ATI to Nvidia. So should I type that in after I install the card? Also should I do anything under restricted drivers? Whenever I do something there I screw up stuff :D.

---

### Post by overdrank on 2007-10-18
> **mrvertigo said:**
> dang...... i was explaining this untill i saw overdrank answered it :P darn you jk go ubuntu!
 I agree but that command is wrong mrvertigo please feel free to intervene
the command should be ```
sudo dpkg-reconfigure xserver-xorg
``` 

:guitar:

---

### Post by mrvertigo on 2007-10-18
honestly, ive been sitting here combing through posts for 6 hours now, that DID slip by me :P 

I wonder if loosing vision due to staring at a monitor for long periods of time would qualify me as disabled.......

---

### Post by overdrank on 2007-10-18
> **mrvertigo said:**
> honestly, ive been sitting here combing through posts for 6 hours now, that DID slip by me :P 

I wonder if loosing vision due to staring at a monitor for long periods of time would qualify me as disabled.......

Please Feel Free to correct me at anytime> It has been a long Gutsy day but that is no excuses for  a bad command, :(

---

### Post by spyker3292 on 2007-10-18
> **spyker3292 said:**
> Ya I am switching from an ATI to Nvidia. So should I type that in after I install the card? Also should I do anything under restricted drivers? Whenever I do something there I screw up stuff :D.

Just in case you missed it :).

---

### Post by mrvertigo on 2007-10-18
as overdrank said > sudo dpkg-reconfigure xserver-xorg is your best bet after the install and restricted or generic/free is up to you, honestly i try to advise people to try to live with the ubuntu sanctioned drivers for simplisitys sake and to save your hair from being pulled out!  If you require fancy effects ect or special restricted features please use the restricted manager to save you time and trouble over the latest and greatest nvidia offering its tempting sometimes but its worth the wait so you dont nuke your setup

---

