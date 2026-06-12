---
title: "Ubuntu crashing! HELP !"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by czepluch on 2007-07-08
My Ubuntu is freezing just after i've done my username and password the little jingle plays, the screen becomes orange and the mouse is in the middle of the screen and then... nothing happens ! Please HELP me !! Desperately need help !!!!

---

### Post by robertc36 on 2007-07-08
You need to change session .
Me thinks this is a compiz issue.
I had similiar problems , i removed emerald from the start up .
When you are in and its ok remember to save that session and restart to see if it happens again.

---

### Post by czepluch on 2007-07-08
> **robertc36 said:**
> You need to change session .
Me thinks this is a compiz issue.
I had similiar problems , i removed emerald from the start up .
When you are in and its ok remember to save that session and restart to see if it happens again.

How do i remove emerald when i cant acces ubuntu? I'm pretty new to Ubuntu

---

### Post by czepluch on 2007-07-08
BumP

---

### Post by czepluch on 2007-07-08
It's been about an hour now. and still haven't figured it out. Please.

---

### Post by robertc36 on 2007-07-08
Before you type in username and password there is an option to change session.
There is something like a recovery or safe session option change to that but dont set it as default.
Ubuntu should then boot ok.
Then remove emerald from startup if that does not work try again with compiz.
In the tutorial you added the emerald-replace option to start up remove that.

---

### Post by czepluch on 2007-07-08
> **robertc36 said:**
> Before you type in username and password there is an option to change session.
There is something like a recovery or safe session option change to that but dont set it as default.
Ubuntu should then boot ok.
Then remove emerald from startup if that does not work try again with compiz.
In the tutorial you added the emerald-replace option to start up remove that.

Still freezing after the jingle....

---

### Post by robertc36 on 2007-07-08
Sorry is that with the Failsafe gnome option

---

### Post by czepluch on 2007-07-08
> **robertc36 said:**
> Sorry is that with the Failsafe gnome option

Yes, it is. Any advice of what to do ? will uninstalling emerald in a terminal work`?

---

### Post by robertc36 on 2007-07-08
Sorry i am only running through what worked for me.
i had the same problem.
As there is no error  message its a little difficult to work out.
But iwould guess its compiz or emerald.
So does anyone else have a solution .
Can ypu control+alt+backspace from the blank screen at all

---

### Post by czepluch on 2007-07-08
> **robertc36 said:**
> Sorry i am only running through what worked for me.
i had the same problem.
As there is no error  message its a little difficult to work out.
But iwould guess its compiz or emerald.
So does anyone else have a solution .
Can ypu control+alt+backspace from the blank screen at all

yeah i can do the Ctrl+Alt+Backspace

The uninstall command for compiz is: sudo apt-get remove compiz (right?) Because i've tried that, but still doesn't work!

---

### Post by czepluch on 2007-07-08
I uninstalled compiz but it didn't work the first time i rebooted, so i did the Ctrl+Alt+Backspace when it frooze and now it works again. So thats fine :):) But now i would like to know why it suddenly works ?

---

### Post by robertc36 on 2007-07-08
ok if ctrl+alt+backspace takes you back to login have tou tried to log-in again from there.
So did that remove compiz because i think that your system is ok just hanging if that makes sense seems to be a bug of some sort.
I have login problems sometimes but i just go back to login screen and login again.
So suprised that failsafe gnome does not work.

---

### Post by robertc36 on 2007-07-08
ok cool if you have  emerald set to start up remove that( just from start up) go to sessions save session and reboot

---

### Post by czepluch on 2007-07-08
> **robertc36 said:**
> ok cool if you have  emerald set to start up remove that( just from start up) go to sessions save session and reboot

Okay thanks a lot for helping me out. - I really apreciate that :)

---

### Post by robertc36 on 2007-07-08
No problem.
I am only a couple of steps ahead of you, just seem to be encountering the same probs lol

---

### Post by czepluch on 2007-07-08
> **robertc36 said:**
> No problem.
I am only a couple of steps ahead of you, just seem to be encountering the same probs lol

Hehe. Then i'll just write to you next time i've got a prob :P

---

