---
title: "pc won't shutdown"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by matty24v on 2007-12-17
Hi I'm a complete beginner in Linux so all your help will be gratefully received

When shutting down Ubuntu it starts the shutdown process but then stalls and then I have to shut it down with the power button

It does give me an error which I will post the next time I shutdown keep forgetting to write it down

---

### Post by wormser on 2007-12-17
Post that error and we should be able to solve it.

---

### Post by Gillette on 2008-01-03
My computer does the same thing but with no error message. I've just started using Ubuntu in the last month. The computer starts shutting down and then stops at a screen that just says Ubuntu. Then I push the power button.

---

### Post by p_quarles on 2008-01-03
> **Gillette said:**
> My computer does the same thing but with no error message. I've just started using Ubuntu in the last month. The computer starts shutting down and then stops at a screen that just says Ubuntu. Then I push the power button.
What happens when you try to shut it down from the command line?:
```
sudo shutdown -P now
```

---

### Post by Gillette on 2008-01-04
The sudo shutdown -P now command had the same result. I think maybe this 1999 Gateway computer is made to be turned off manually. In the BIOS settings it describes the shutdown as holding the button down for four seconds. That is basically what I have to do to shut it down.

---

### Post by LowSky on 2008-01-04
The BIOS setting is describing a hard shutdown, you should be able to change that setting within the BIOS, but not to auto shutoffm but mabe one click shutoff, bettter that standing around for a few moments holding a butotn down.

---

### Post by p_quarles on 2008-01-04
It used to be the case that many computers had to be powered off externally, but they had actual power switches. It's very unlikely that a computer made in 1999 wouldn't have the ability to turn itself off. 

Try another couple commands:
```
sudo shutdown -h now
```
and
```
sudo poweroff -f
```
If both of those turn up the same result, I'd be interested in seeing what happens with this:
```
sudo shutdown -r now
```
Note that the "-r" option means "reboot," so if this command works correctly, it will start back up immediately.

---

### Post by Gillette on 2008-01-04
Thanks for the information on the BIOS settings. I didn't see anything about one click shutoff, but there was SUSPEND and I think AUTO. I'll look again tonight when I get home.

---

### Post by philinux on 2008-01-04
Check the link for workarounds. It's a power management thing. And when it hangs shutting down pressing the power off at that point does no harm.

---

### Post by GerryB on 2008-01-04
> **matty24v said:**
> Hi I'm a complete beginner in Linux so all your help will be gratefully received

When shutting down Ubuntu it starts the shutdown process but then stalls and then I have to shut it down with the power button

It does give me an error which I will post the next time I shutdown keep forgetting to write it down

Go to [http://ubuntuforums.org/showthread.php?t=359190](http://ubuntuforums.org/showthread.php?t=359190). It solved my problem. Happy New Year.

---

