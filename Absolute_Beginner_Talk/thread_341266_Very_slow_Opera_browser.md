---
title: "Very slow Opera browser"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2007-01-18
Hi
I've just upgraded to Ubuntu 6.10 and am now just getting around to giving the Opera browser a shot.
However, I find it to be abominably slow which almost certainly means I have mis-configured something. But what?
I had a similar problem when I tried Firefox in Ubuntu (dapper) which was also extremely slow until someone told me to toggle the DNS Network switch for IPV6 in about:configure.
Can anybody help me resolve this Opera problem?
Paul

---

### Post by riven0 on 2007-01-18
Try some of these tips. Go to Tools >> Preferences >> Advanced >> Network >> Server Name Completion and uncheck everything. Then put your Max connections to a server to 16.

Then, check under your plugin directory: Tools >> Preferences >> Content >> Plug-in Options, and make sure you don't have multiple flash or java plugins listed. If you do, go to Change Path and take out some of the paths like Netscape or Mozilla. 

Then restart Opera and see if there is a speed increase.

---

### Post by PaulFXH on 2007-01-22
Thanks for the reply.
Actually, I found that Opera is actually available from the Repositories and so I re-downloaded from there (rather than from the Opera website as I had done originally).
This went flawlessly and Opera operated absolutely perfectly with the high speed I had been hoping for.

However, I intend to use the tips you suggested to see if I can add another Mach or two.

---

