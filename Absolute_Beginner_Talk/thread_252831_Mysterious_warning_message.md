---
title: "Mysterious warning message"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by rufousfelix on 2006-09-07
While connected to the Internet with my older ThinkPad running Breezy Badger, I got a "call-out" warning that said words to this effect: "Someone with malicious intent might be listening...Tried to grab your mouse."  Not an exact quote, but the general message.  I disconnected & changed password.  Question is, Where does this message come from?  I believe I was using Firefox at the time, and found the message quite disconcerting.  Where does one start with evaluating this message?  Any ideas would be appreciated.

---

### Post by nalmeth on 2006-09-07
If you can reproduce the warning, post the exact message you're getting.

That is a little disconcerning

---

### Post by rufousfelix on 2006-09-07
I've quoted the message as best I can remember it & I think it's 90% accurate.  I wrote it down soon afterward, but could not cut & paste.  

I should also mention I got this same message about six months ago, also after a fresh install of Breezy (as I did the other day).  I have not config'd firestarter & when I did earlier, that kept the msg from reappearing.  It seems to be some sort of hoax intrusion, but I think it's important because I had two occurrences months apart with Breezy.

---

### Post by [flax] on 2006-09-07
When you try to execute an application that required root access, gksu will  try to grab your mouse / keyboard to enter your password.

When this failed(a application that is logging / your are doing a lot of thingies while this command is executed(more likely)) a message will be displayed telling you the following could not grab mouse error.

There is also some information regarding this in [http://ubuntuforums.org/showthread.php?t=199746](http://ubuntuforums.org/showthread.php?t=199746)

---

### Post by rufousfelix on 2006-09-07
flax, thanks much.  Yeah, you've explained it as a system-generated msg & thus reduced my level of paranoia:D   The odds of my getting the identical msg twice separated by six months from an external intrusion must be on the order of <<1:1,000,000! Still, a bit creepy the first time one sees this msg out of the blue ...

---

