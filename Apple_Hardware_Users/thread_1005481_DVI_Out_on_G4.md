---
title: "DVI Out on G4"
date: 2008-12-08
forum: Apple Hardware Users
---

### Post by pennstatebadboy on 2008-12-08
I have a Powerbook G4 with DVI out. It's running Intrepid.

When I hook up an external lcd monitor via DVI, Ubuntu recognizes the monitor and shows it in the "Monitor Resolutions" app in the Preferences menu. However, nothing is appearing on the screen of the external monitor. I just get "No Signal."

How do I get this to work?

---

### Post by stream303 on 2008-12-08
This might do the trick:

[https://wiki.ubuntu.com/PowerPCFAQ#Enable%20DVI%20out%20on%20my%20Powerbook](https://wiki.ubuntu.com/PowerPCFAQ#Enable%20DVI%20out%20on%20my%20Powerbook)

---

### Post by pennstatebadboy on 2008-12-09
No luck with that. I can't figure out why the external monitor would be recognized but nothing will show up. It knows that it's a 32 inch monitor and even shows the proper maximum resolution. So it's definitely seeing it.

Any other ideas?

---

### Post by pennstatebadboy on 2008-12-11
What the heck?

I thought maybe it was just my monitor or a bad DVI port that was causing problems, so I hooked up this G4 to a friend's monitor with a DVI-in port. That didn't work either. But while I had it attached to my friend's monitor, I decided to try booting from a live CD (8.04)--and it worked!

So I hooked it back up to MY monitor and booted from the live CD--and NOTHING! It still doesn't work with my monitor.

**To summarize**

My monitor:
[LIST]
[*]Boot from hard disk: NO DVI OUT
[*]Boot from live CD:   NO DVI OUT
[/LIST]

My friends monitor:
[LIST]
[*]Boot from hard disk: NO DVI OUT
[*]Boot from live CD:   DVI OUT WORKS
[/LIST]

In all four cases above, Ubuntu IS recognizing the monitor and the monitor's supported resolutions and refresh rates.

What the heck is going on here?

---

### Post by tiresia on 2008-12-11
I guess you have already tried to start the computer, connect the monitor and to restart X (with the monitor still connected)

---

### Post by pennstatebadboy on 2008-12-11
Yes. I've tried that. In fact, as I've been fiddling with the resolutions in my attempt to get this to work, it sometimes prompts me to restart X.

---

### Post by tiresia on 2008-12-11
I mean just restart X with Ctrl-Alt-Backspace

---

### Post by pennstatebadboy on 2008-12-11
Yep. That's what I do. CTRL-ALT-BACKSPACE

---

