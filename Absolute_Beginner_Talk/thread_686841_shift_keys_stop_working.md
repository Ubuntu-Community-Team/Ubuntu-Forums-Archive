---
title: "shift keys stop working"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by giftedwon on 2008-02-03
hello,

i am running ubuntu on a dell laptop.  last week the shift keys stopped working and i was unable to get them to work again.  i had to reload the laptop and it then worked.  yesterday it stoped  working again.  it does not work in   gnu or  kde

i used   xev

i get a response on every key except the  two shift buttons
please help

---

### Post by pmshirey on 2008-02-06
Ok, this is very hard, and may have to be done by a professional, but, carefully take out the shift key with a small flat head screw driver, and take a sanitizing wipe and clean the place where the key was, and clean off the bottom of the key and see if that works. I had this problem 2 years ago, and did this, and it worked.

Tell me when you have replied in a private message, and include the link of the thread,

---

### Post by nikoPSK on 2008-02-06
As stated above, possibly just keyboard age. :)

---

### Post by giftedwon on 2008-02-07
i really doubt thats it because its both of the  shift keys that are a problem.

---

### Post by nikoPSK on 2008-02-07
> **giftedwon said:**
> i really doubt thats it because its both of the  shift keys that are a problem.

hrm, does your keyboard have special software? Maybe you somehow reconfigured keys? :confused:

---

### Post by giftedwon on 2008-02-08
ok i got it working.  this is ghetto  but I got so pissed off I literally smacked the keyboard.  I smacked it as hard as I can .  the screen went blank and I restarted the laptop.   Once it came back up the keyboard worked!!

---

### Post by nikoPSK on 2008-02-08
> **giftedwon said:**
> ok i got it working.  this is ghetto  but I got so pissed off I literally smacked the keyboard.  I smacked it as hard as I can .  the screen went blank and I restarted the laptop.   Once it came back up the keyboard worked!!

lol, it might fail in future from smacking... please mark this thread as solved in thread tools. :)

---

### Post by brokenhachi on 2008-02-08
i guarantee you it is because the keyboard is dirty and old. i had the EXACT same problem.. i smacked it... it worked.. then a couple months later half the keyboard stopped working. 


you need to clean/get a new keyboard dude. (they are only like 15-20 bucks and easy to change)

---

### Post by pmshirey on 2008-02-08
lol omg wtf! Well im glad that that worked! Please thank me for the help by clicking my badge.

---

### Post by nikoPSK on 2008-02-08
> **pmshirey said:**
> lol omg wtf! Well im glad that that worked! Please thank me for the help by clicking my badge.
 
best not to promote it... Anywyas, just to let you know, in my opinion, smashing the keyboard won't have a nice effect later...

---

### Post by decoherence on 2008-05-21
i'm having the same problem. it is fixed by logging out and logging back in, however that is not an acceptable solution.

it is certainly not the keyboard. i'm running vmware and the guest has no problem. also, the caps lock key does nothing. it's literally like i've been stripped of all capital letters11111 9oh, and things like parentheses and exclaimation marks10

any ideas/ --god having no shift sucks11

---

### Post by xeth_delta on 2008-05-21
> **decoherence said:**
> i'm having the same problem. it is fixed by logging out and logging back in, however that is not an acceptable solution.

it is certainly not the keyboard. i'm running vmware and the guest has no problem. also, the caps lock key does nothing. it's literally like i've been stripped of all capital letters11111 9oh, and things like parentheses and exclaimation marks10

any ideas/ --god having no shift sucks11

In your case it seems to be a different problem. Maybe a keyboard misconfiguration. please open a terminal and run:
```
xev
```
Try the shift and CapsLock keys. Is there any output in the terminal?

---

### Post by Zularan on 2008-05-23
i'm having this issue now as well [hence no caps or correct brackets] and xev shows output as lshift and r-shift as well as capslock.

alt works
```
KeyPress event, serial 27, synthetic NO, window 0x4800001,
    root 0x1a6, subw 0x0, time 3307012, (342,206), root:(351,370),
    state 0x10, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 27, synthetic NO, window 0x4800001,
    root 0x1a6, subw 0x0, time 3307124, (342,206), root:(351,370),
    state 0x18, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
shift and control on both sides do not
```
KeyPress event, serial 27, synthetic NO, window 0x4800001,
    root 0x1a6, subw 0x0, time 3354805, (33,-13), root:(42,151),
    state 0x10, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 27, synthetic NO, window 0x4800001,
    root 0x1a6, subw 0x0, time 3354901, (33,-13), root:(42,151),
    state 0x10, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

``````

KeyPress event, serial 27, synthetic NO, window 0x4800001,
    root 0x1a6, subw 0x0, time 3355653, (33,-13), root:(42,151),
    state 0x10, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 27, synthetic NO, window 0x4800001,
    root 0x1a6, subw 0x0, time 3355701, (33,-13), root:(42,151),
    state 0x10, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

i seem to get a response in xev, but not when typing normally here, terminal or any apps..

i'm sure rebooting might correct it but i too am curious what the actual problem is. 

i have a logitect g15 connected to a dellxps laptop whose keyboard has identical symptoms.  this issue just arose 10mins ago and has been working fine up until then.

*edit;* vmware seems to recognise the control-alt keypress to letgo of the mouse cursor.
ubuntu also just rebooted from about 44 updates an hour or so ago not sure if thats related however.

---

