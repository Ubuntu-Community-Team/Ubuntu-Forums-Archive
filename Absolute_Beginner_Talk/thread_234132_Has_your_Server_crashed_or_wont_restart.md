---
title: "Has your Server crashed or wont restart?"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by Gig on 2006-08-11
I Had a Server problem and couldnt remotely access it. It is over 600 kms away and it took half a day to help someone through this fix as I couldnt find anything on the net. so, to help others I decided to add it in case someone else could use it.

Basically, my server kept restarting and when it occassionally would start it would not start my pppoe connection and dialout the adsl line to connect. Thus I could not log in through my dyndns remote login and access the server and the site was down for a day or so. It actually all started when the power died and the ups eventually ran out of power, some 2 or so hours and seemed to corrupt the server, very odd.

But, the fix eventually wasnt that hard. To get linux working what I eventually did was:

When Ubuntu reboots it give you a Grub menu option. We pressed escape to go to the menu. we then chose the recovery mode for the Kernel which seemed to repair the kernel. Once in we logged in and rebooted the system by typing reboot at the command prompt and it started rebooting normally again.

To fix the pppoe I got the person there to re-install the pppoe by typing apt-get install pppoe at the command prompt. This fixed the problem in the pppoe software.
We then reconfigured the pppoe link by typing pppoeconf at the prompt, entered the dialout details, and it worked. 

If you have any questions on this you can mail me on grantg at mrit dot co dot za.

Good Luck if you have this error.

---

