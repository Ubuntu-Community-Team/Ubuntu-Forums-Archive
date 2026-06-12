---
title: "edgy"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by captgadget on 2006-12-10
I've got Edgy installed but can anyone tell me why my hard drive light shows the hard drive is in use when nothing is no activity?

---

### Post by axle_foley00 on 2006-12-10
Well it might seem that nothing is in use, but perhaps there is some process running in the background.

Go to **System->Administration->System Monitor** and take a look at the *resources tab* and see what your *CPU history* shows. If the percentage seems a little high then perhaps there is something taking up a lot of CPU time. Occasionally it might spike, but if you see it at 100% for prolonged periods of time then quite likely there is a little problem. You can then check the *Processes tab* and see if anything there is using up a lot of memory or if you have duplicates of programs open. If there is anything taking up a lot of memory or CPU usage, then you could try ending the process and seeing if that helps.

Does this happen all the time though? Or only sometimes?

---

### Post by lamego on 2006-12-10
Probably there are some backend tasks runnning like utilities which update the system  files search database etc.

---

### Post by captgadget on 2006-12-10
I checked the system monitor and there doesn't seem to be anything unusual in there. Do either of you feel like that is a problem? I mean that the hd light stays on. I was gone from the computer almost 2.5 hours, came back and it was still lit.

Thanks

---

### Post by axle_foley00 on 2006-12-10
> **captgadget said:**
> I checked the system monitor and there doesn't seem to be anything unusual in there. Do either of you feel like that is a problem? I mean that the hd light stays on. I was gone from the computer almost 2.5 hours, came back and it was still lit.

Thanks

Hmmm...I'm not quite sure. That's the first thing that came to mind when I read the problem you were having, but if you said you checked and everything seems fine (ie. no processes doing anything weird) then I'm not quite sure what else it could be).

Is the computer running slowly, programs taking a while to load, freezing up on you, hard drive making any sounds or is it operating fine but its just the light staying on that is bothering you?

---

### Post by captgadget on 2006-12-10
Nothing unusual about the computer. Just that the hd drive light is always on.

---

### Post by axle_foley00 on 2006-12-10
Really not sure what else to tell you. Hopefully someone else will post soon with a solution.

Sorry I couldn't be of more help.

---

### Post by captgadget on 2006-12-10
Not a problem. Appreciate the input.

---

### Post by igknighted on 2006-12-10
Do you have beagle search installed?  If you do, the light is probably beagle indexing your drive for fast search times.  Beagle is able to do what it does  because it reads every file on your HD to see whats there, then when you search it alreadys knows where stuff is.  It's a great feature, but takes a while to do the initial index.

---

