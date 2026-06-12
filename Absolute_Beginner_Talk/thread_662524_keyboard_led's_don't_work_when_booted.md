---
title: "keyboard led's don't work when booted"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by wana10 on 2008-01-09
an interesting problem rose today and i was hoping someone here nows how to fix it...
simply put the leds on my keyboard for num/caps/scroll lock don't work properly. the keys themselves do but the leds do not. all throughout the boot i can toggle them on an off to my hearts content but as soon as the gdm screen loads they freeze in their last position and won't toggle again.

any help greatly appreciated 
-wana10

edit* another problem is that when the keyboard is in use(typing) i cannot move the mouse.

---

### Post by ~Maxx on 2008-01-09
I'm pretty new here, but I was just reading about this...  Check your keyboard preferences (system > preferences > keyboard), and go to the 'layout options' tab.  The very last item on the list is "Use keyboard LED to show alternative group".  Open that up and see if any of the boxes are ticked.  I believe that they should *not* be except under special circumstances.  Good luck!

---

### Post by shareMenaPeace on 2008-01-09
Did you tried choosing the correct keyboard manufacture/model from PREFERENCES -> KEYBOARD ?

---

### Post by wana10 on 2008-01-09
just checked, no odd boxes checked and my keyboard setting is the same as it always was(generic 105 key).

---

### Post by ~Maxx on 2008-01-09
> **wana10 said:**
> 
edit* another problem is that when the keyboard is in use(typing) i cannot move the mouse.
Hmm...  Mine does exactly the opposite.  Keys won't work while mouse is moving!  Heh heh...  Wish I could help you there - but I only considered it a minor and tolerable quirk, so I never researched the matter.  Let me know what you find out though!

---

### Post by ~Maxx on 2008-01-09
I just remembered...  Are you using a wireless keyboard and/or mouse.  My keyboard and mouse will work simultaneously as long as I'm using a mouse on a leash.  As soon as I switch back to the wireless mouse the issue resumes (keyboard is also wireless).

---

### Post by wana10 on 2008-01-09
SOLVED COMPLETELY!!! HUZZAH!!!:KS

found [this thread](http://ubuntuforums.org/showthread.php?t=417089) which was over in the appel-intel part of the forum (its amazing what shows up when you enter "can't move mouse when typing" into google, that thread was the top result!!)

followed its instructions to killall mouseemu and the remove the little fiend and all of a sudden my mouse and keyboard work perfectly in tandem and the leds on my keyboard work perfectly as well.

now my only question is where the hell did that program come from?! i'm running a home-built amd based desktop and evidently that program is for intel based apples...oh well, hopefully it won't come back.

thanks for the help and suggestions.
-wana10

edi* @ maxx: :oops: i'm actually using an old ps2 keyboard and ps2 mouse(with a ball!) they were the only things i could easily scrounge when i built my system.

---

### Post by ~Maxx on 2008-01-09
> **wana10 said:**
> SOLVED COMPLETELY!!! HUZZAH!!!:KS

edi* @ maxx: :oops: i'm actually using an old ps2 keyboard and ps2 mouse(with a ball!) they were the only things i could easily scrounge when i built my system.

Sounds like Santa should have brought you a few more toys this year, huh?  The keyboard and mouse are pretty secondary to having a good system though, aren't they?  Glad you got everything back on track!

---

### Post by FRuMMaGe on 2008-02-11
> **wana10 said:**
> SOLVED COMPLETELY!!! HUZZAH!!!:KS

found [this thread](http://ubuntuforums.org/showthread.php?t=417089) which was over in the appel-intel part of the forum (its amazing what shows up when you enter "can't move mouse when typing" into google, that thread was the top result!!)

followed its instructions to killall mouseemu and the remove the little fiend and all of a sudden my mouse and keyboard work perfectly in tandem and the leds on my keyboard work perfectly as well.

now my only question is where the hell did that program come from?! i'm running a home-built amd based desktop and evidently that program is for intel based apples...oh well, hopefully it won't come back.

thanks for the help and suggestions.
-wana10

edi* @ maxx: :oops: i'm actually using an old ps2 keyboard and ps2 mouse(with a ball!) they were the only things i could easily scrounge when i built my system.
THANKS SO MUCH!!!

---

