---
title: "Need help desperately - CRC Error, System Halted!!!!!!!!!!!!!"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by agarwaldvk on 2006-03-06
Hi Everybody

I have been trying to get my Dad's broadband connection going in Breezy.

I followed the suggestion by jbmalone (reproduced below) :-

> Shut down the computer, plug in the modem, then unplug the power cord. Plug the power cord back in and then restart the computer. This should reset the modem and have to pull the DNS servers again. You should know if everything worked if the clock synchronized with the linux site on startup. To make sure that everything is ok, go into Networking and make sure the eth0 connection is active. You can poke around in those tabs too to figure out what your problem is, like if the computer is even recognizing the modem itself.

I have dual boot system with Windows XP. So after following the above suggestion, when I restarted the computer and selected the Ubuntu option, it went upto a stage and them came up with this error and halted :-


"CRC error, system halted".

What do I do next? Need help desperately.

It still does work OK when the Windows XP option is selected.


Best regards



Deepak Agarwal

---

### Post by maubp on 2006-03-29
CRC errors indicate some problem reading the hard disk.  It may be getting old and wearing out.

You haven't opened the computer case recently have you?  A slightly loose IDE ribbon cable can also cause this.

---

### Post by agarwaldvk on 2006-03-29
Dear maubp

Thank you very much for your response. I nearly gave  since I didn't hear from anyone.

I really really appreciate it.

No I haven't opened the case and done nothing to any of the hardware. Admittedly, the drive is getting very old. If this error is only indicating the ageing of the hardware and nothing more sinister than that then I am not too worried.

However, can you please suggest any further solutions that I am having in trying Ubuntu (Breezy) recongnize the Broadband connection on my Dad's computer?

You may want to have a look at the previous correspondences by going to this post of mine earlier titled :-

"Setting up Broadband in Breezy"



Best regards


Deepak Agarwal

---

### Post by chusome on 2006-03-29
CRC don't always mean bad drive's.

eg. In IBM laptops this is usually due to a bad board.
If you're able to boot into windows, go to start->run Type: eventvwr.msc

Look at the system log and check for anything under the source column that says "disk". If so, then the drive is quite possibly failing.

---

### Post by agarwaldvk on 2006-03-30
Dear Chusome

That's ok! I shall check that tomorrow when I see him.

And by the way, how do I check the system log?

Excuse my ignorance on Ubuntu. I am "pretty" new to this Ubuntu stuff.


Best regards


Deepak Agarwal

---

### Post by vazzeroni on 2007-12-05
FWIW, I got this message when I had a bad stick of RAM

---

