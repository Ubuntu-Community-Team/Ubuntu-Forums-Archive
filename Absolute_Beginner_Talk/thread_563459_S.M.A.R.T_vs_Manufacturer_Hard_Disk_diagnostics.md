---
title: "S.M.A.R.T vs Manufacturer Hard Disk diagnostics?"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by margaf77 on 2007-09-30
On boot I just started getting a S.M.A.R.T error:

S.M.A.R.T. status bad backup and replace error

So after this I backed up the drive and ran the Seagate SeaTools diagnostic software and did the long test where it came up with a pass result. 

Which result do I believe, SMART or SeaTools?


Sorry if this is in the wrong forum, I think its correct posting it here but if not I apologize.

---

### Post by HermanAB on 2007-09-30
Well, Google proved statistically that Smart doesn't work...

Cheers,

H.

---

### Post by margaf77 on 2007-09-30
> **HermanAB said:**
> Well, Google proved statistically that Smart doesn't work...

Cheers,

H.

Yeah, I read some stuff saying that but on running SeaTools short test a couple more times did fail 1 time. Im running the long check now to see if the result is the same the second time around.

---

### Post by MJN on 2007-10-02
SeaTools is just a front end for the internal SMART diagnosis tests.
 
Install the smartmontools package and post the output from the following:
 
```
sudo smartctl -a /dev/hda    (or whatever your drive is)
```
 
We can then go on to performing some tests (short and long) to determine what, if anything, is wrong.
 
HermanAB's assertion is a little strong - Google's conclusion was that SMART is not as effective as many might think/wish. This is true; SMART is not the panacea for predicting all drive failures however compared to the alternative (if there even is one) it's extremely useful and given the lack of drawbacks (aside from overreliance and complacency) it's certainly worth employing.
 
Mathew

---

