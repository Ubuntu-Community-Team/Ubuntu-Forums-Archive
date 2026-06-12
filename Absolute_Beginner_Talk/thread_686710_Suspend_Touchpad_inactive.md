---
title: "Suspend Touchpad inactive"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Sugz on 2008-02-03
Whenever i suspend my laptop and then resume, again i lose the use of my touchpad.
It freezes i am using Gutsy with latest updates. 
please any help?
Much appreciated.
-Sugz

---

### Post by diaa on 2008-02-04
May be try this workaround:
[LIST=1]
[*]System -> Quit
[*]Switch User
[*]Login as the same user again[/LIST]It's annoying but better than a restart

---

### Post by Sugz on 2008-02-04
No that "fix" did not work :(
i really have searched EVERYWHERE, is this a common problem?

---

### Post by diaa on 2008-02-04
> **Sugz said:**
> No that "fix" did not work :(
i really have searched EVERYWHERE, is this a common problem?

Not for me, doesn't happen on my laptop

---

### Post by Sugz on 2008-02-04
What laptop model do you have?:confused:

---

### Post by diaa on 2008-02-04
> **Sugz said:**
> What laptop model do you have?:confused:

Acer Extensa 6600

---

### Post by Sugz on 2008-02-04
Hmm shame i cant find a solution anywhere, this is a real pain hence i cant realistically use suspend in themiddle of a lecture can i ? without rendering my laptop useless until restart :confused:

---

### Post by diaa on 2008-02-04
What's yours?
May be this can help
[Amilo 1520 sleep doesn't resume touchpad from suspend on ram]("https://bugs.launchpad.net/linux/+bug/52967")

---

### Post by diaa on 2008-02-04
and this too
[after suspend resum touchpad doesn't work]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84133")
Actually both bugs seem to be related to the kernel so if none of the workaround mentioned work you can try downgrading the kernel.

---

### Post by Sugz on 2008-02-04
Thanks for those two links. I have seen those pages before. none actually give a workaround that works. This is a problem but does anyone else use my laptop and experience the same problems?
Its a strange problem because Hibernate Works fine. :confused:

---

### Post by Sugz on 2008-02-06
I suppose i could try with an alternaitve kernel.. how would i go about downloading a different kernel and (temporarily) seeing if it will work?

---

### Post by diaa on 2008-02-07
I did some searching on the forums and found no easy way to downgrade the kernel to 6.21 or something... and I don't think you want to compile the kernel to do this
sorry...

---

### Post by Sugz on 2008-02-07
Thanks for searching.
Oh no, so im stuck with this problem. I tried my friends who has done the same thing recently and she has an older laptop then me (much older) and her suspend works without a hitch of any kind.
Personally i think this is a fundermental flaw and is something that should be fixed ASAP as if im not mistaken this is a typical feature of a modern day OS. 
Everything else works flawlessly except suspend which is a feature that myself (and many other laptop users) would gladly want to work without too many adjustments.
-Sugz

---

### Post by diaa on 2008-02-07
I think you should file a bug at [Launchpad]("http://launchpad.net") and hopefully it'll be included in the next release, they'll ask you for more information and give you instructions on how to obtain it, and you'll have to sign up at launchpad
Be sure to include the exact model of the laptop and the software version you are running

---

### Post by Sugz on 2008-02-08
iposted up on Launchpad about two weeks ago. and still no reply:confused:

---

