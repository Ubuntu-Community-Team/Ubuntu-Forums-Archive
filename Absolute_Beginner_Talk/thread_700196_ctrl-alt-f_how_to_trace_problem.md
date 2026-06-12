---
title: "ctrl-alt-f how to trace problem"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by grozni on 2008-02-18
Hi guys,


I'm having trouble getting command line, everything thru f1-f6 is not working, I can normally switch back to X with f7, I read on some other thread disabling splash could solve the problem, I've tried that, the only change I've notice is that some lines appear all over the screen, screen become dissoriented, I can return normally via ctrl-alt-f7. When splash is enabled pressing ctrl-alt-f1 gives blinking line and that's it, no disorientation. I've ghosted my Ubuntu from my desktop pc, previously was nvidia card, now on laptop is x3100 (gma965). I've removed nvidia drivers, intel driver works fine. I've attached Xorg file. Any help appreciated

---

### Post by justleen on 2008-02-18
ehm... what is your problem exactly?
i read this several times, but cant fugure out what it is you need? YOu want to see all the output during boot, or do you need to get from X to a full terminal?

---

### Post by grozni on 2008-02-18
I can't get full terminal from X when I press ctrl-alt-f1, it hangs there. I can return normally via ctrl-alt-f7

---

### Post by justleen on 2008-02-18
> **grozni said:**
> I can't get full terminal from X when I press ctrl-alt-f1, it hangs there. I can return normally via ctrl-alt-f7

try this then:
- go to a terminal with ctrl-alt-F1
- when it "hangs" switch to a anohter terminal (alt-f2)
- press enter

you should get a login prompt.. 


(the step of switching to another term is not neccesary, just to check wether your actually switching to anohter term.. it screen should just blink when you switch to another term)

---

### Post by grozni on 2008-02-18
I've tried what you suggested, no luck. I've tried switching to other terminal with alt+f2, pressing enter, nothing happen. Just blinking line, any other suggestions? I've normally switched back to X via ctrl+alt+f7. Thanks

---

