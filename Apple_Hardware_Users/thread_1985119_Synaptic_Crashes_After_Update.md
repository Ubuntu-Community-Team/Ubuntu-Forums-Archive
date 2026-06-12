---
title: "Synaptic Crashes After Update"
date: 2012-05-22
forum: Apple Hardware Users
---

### Post by Javelin Dan on 2012-05-22
Running Lubuntu 12.04 Ppc on a G4 “Graphics” 450 MHz, 20 GB hard drive, 896 GB RAM. When I run Update Manager, or try to update through Synaptic, Synaptic crashes and I get the following message the next time I try to open it:

[I]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. [/I]

I’ve tried the commands “dpkg --configure-a”, “--debug=<octal>”, and "-D<octal>" plus all the “dpkg” commands that don’t have a “damage" warning, but can’t get it to budge. It's very possible I'm just not understanding what it wants me to do here. Any suggestions would be appreciated.

---

### Post by Javelin Dan on 2012-05-23
Correction - of ourse I meant 896 _MB_ of RAM.

---

### Post by Javelin Dan on 2012-05-23
Fixed it!  I decided to run the command:* "sudo apt-get update"* . After a lot of output looking like it was updating normally, I got the same error message as shown above in my first post. 

But then I realized that in the command "*sudo dpkg --configure -a"* there was a space between "*configure" *and "*-a"* that I hadn't picked up on before. I had them connected without a space. Rookie mistake! I actually copied and pasted the command shown in the error message into my terminal command, hit the go button, and all is right with the world! I've been updated and have Synaptic back. No one's more surprised than me that I was able to figure this out.

---

