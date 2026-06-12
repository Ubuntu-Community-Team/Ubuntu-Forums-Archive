---
title: "Condition Zero With Ubuntu 7.10"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Bluestick on 2008-02-05
k guys ive been trying to get help on this one for a while. plz take the time to take a look at it please!
  ---everytime i try to play CZ it freezes after 4-5 min right of way, i have tried turning my visuals off no help, iam running amd 3400++ ATI x850 PRO 1.5 gig ram 200 gig HD
here are some screens take a look to see what im running maybe doing something wrong

---

### Post by Bluestick on 2008-02-05
#2 screen

---

### Post by Bluestick on 2008-02-05
bump* 
 - any ideas what could be freezing the game after 5 min of game play?

---

### Post by Bluestick on 2008-02-05
come on no one has any ideas? :(

btw im using regular wine and wine-doors!

---

### Post by fenian on 2008-02-05
disable desktop effercs.

---

### Post by Bluestick on 2008-02-05
> **fenian said:**
> disable desktop effercs.
all ready tried that!
 it makes it wors lol if i disable desktop effects, and then i lunch CZ it freezes right of way cant even play

---

### Post by hyperair on 2008-02-05
Turn off AWN as well.

EDIT: It could be a sound issue, I've had random freezing with my CS:Source as well. Could you post a screenshot of your wincfg's sound page?

---

### Post by fenian on 2008-02-05
From your screenshots it looked like you totally uninstalled the restricted driver.Thats not what you want to do , keep the restricted driver and turn the effects off from System>Prefrences>Appearance under the Visual effects tab check none.

---

### Post by Bluestick on 2008-02-05
> **hyperair said:**
> Turn off AWN as well.

EDIT: It could be a sound issue, I've had random freezing with my CS:Source as well. Could you post a screenshot of your wincfg's sound page?
whats the command how do i do that?

Oh and "fenian" i did had them turned on at the time. but i turned them off while playing restart and try it never works!!!

---

### Post by Bluestick on 2008-02-05
ok here it is, i thank you for trying to help me guys.. i really need this i love this game!

---

### Post by Bluestick on 2008-02-05
1 more..

---

### Post by Bluestick on 2008-02-05
> **hyperair said:**
> Turn off AWN as well.

EDIT: It could be a sound issue, I've had random freezing with my CS:Source as well. Could you post a screenshot of your wincfg's sound page?
How do i turn that OFF?

---

### Post by hyperair on 2008-02-05
Erm right click on it and exit. Why don't you try selecting OSS and disabling ALSA, then running Condition Zero with OSS emulation?

---

### Post by Bluestick on 2008-02-05
> **hyperair said:**
> Erm right click on it and exit. Why don't you try selecting OSS and disabling ALSA, then running Condition Zero with OSS emulation?
ok how do i do that in newb language ?
AWN is off when im playing!
someone AIM me or something and tell me how this works please

---

### Post by Bluestick on 2008-02-05
bump*
whats OSS? and how do i disable ALSA?

---

### Post by Bluestick on 2008-02-05
anyone read above plz help!

---

### Post by hyperair on 2008-02-05
OSS = Open Sound System. On most (integrated) cards, OSS causes only one application to be able to use the sound card at a time, but it's more stable when used in Wine. Also alsa-oss (from Synaptic) can provide OSS emulation, allowing more than one program to use the sound card.

EDIT: I meant disabling ALSA in winecfg. Just uncheck the box.

---

