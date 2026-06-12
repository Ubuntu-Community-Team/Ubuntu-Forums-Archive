---
title: "using same install disc on multiple computers (Windows)"
date: 2013-09-15
forum: Any Other OS
---

### Post by rybnik on 2013-09-15
It's been a little over one and a half years since I used Windows, and that was just XP--never ran Vista, 7, or 8 on my own computer.  Back then, I remember being able to use my XP Pro install disc multiple times on multiple computers, but I understand that, now, Microsoft is cracking down on that.

So I see that Win7 and Win8 come in OEM and retail versions--if I understand correctly, the former (i.e. OEM) is tied to a specific motherboard, so it can't be installed on more than one computer, while the latter (i.e. "retail") lets you install on more than one computer, although other restrictions apply--I don't really understand what they are, specifically.

So, my question:

How is it (logically) possible for Microsoft to enact restrictions like that, such as being able to only install on one computer? When you perform a clean install, you don't have internet access yet anyway, so at that point, how can microsoft check whether your product key was used previously?

Thanks!

---

### Post by TheFu on 2013-09-15
They check for specific BIOS settings that OEMs put inside.  It isn't hard.  I don't think they check for a specific CPU or serial number, so if you buy 2 or 50 identical systems, then the same /DVD can be reused over and over across them all.

Every computer has a slightly different "finger print" based on the BIOS, hardware, drivers, partitioning, and more.  When an OS is running and a web browser is used, even more data helps to uniquely identify it.   [This link]("https://panopticlick.eff.org/") will give you an idea of how unique your computing environment is. The more you customize, the more unique your system is ... which is great for tracking without cookies.

---

### Post by buzzingrobot on 2013-09-15
Isn't the MAC address unique?

---

### Post by rybnik on 2013-09-16
[quote=buzzingrobot]Isn't the MAC address unique?[/quote]
Well yes, my point was that when you perform the install, you don't have networking in the first place, so microsoft can't check anything other than the product key--which is checked only by the disc itself, and the disc is read-only, so it can't tell whether it was used before.

[quote=TheFu]They check for specific BIOS settings that OEMs put inside.  It isn't  hard.  I don't think they check for a specific CPU or serial number, so  if you buy 2 or 50 identical systems, then the same /DVD can be reused  over and over across them all.

Every computer has a slightly different "finger print" based on the  BIOS, hardware, drivers, partitioning, and more.  When an OS is running  and a web browser is used, even more data helps to uniquely identify it.    [This link]("https://panopticlick.eff.org/")  will give you an idea of how unique your computing environment is. The  more you customize, the more unique your system is ... which is great  for tracking without cookies.[/quote]

I see what you're saying, but I believe that my objection (as stated earlier in this particular post) stands.  I don't mean to argue; I'm just trying to make sense of how msft is able to run a check [b]during the installation[\b].

---

### Post by TheFu on 2013-09-16
MS burns the system fingerprint (probably just a vendor model number easily available from WMI) into the OEM installers.  Nothing hard about that. No need to check anything on the internet.  During install, a WMI call is made. If the answer comes doesn't come back or the answer is wrong, then it isn't the specific model computer. Simple. I've never seen the installer locked to an individual computer, just to a specific vendor-model.

I'm not arguing and didn't thing you were either. It is a purely technical question in my mind.  MS **can** choose to limit which systems on which any of their products run, so can you and I.  "Retail" versions of MS-Windows cost $80-$150+ and can be loaded on any PC (within reason). OEM version run about $12-$30, but carry the stipulation that the license is locked to a single computer.  

For 99% of the world, locking the license is not that big of an issue because they would never attempt to install any operating system. When their PC breaks for any hardware or software reason, it is cheaper and easier to just buy a new one.

For you and me, it is a huge hassle, but thankfully, we are able to step away from that use pattern.  1 day a year, I organize and help about 20 new people install Linux. That was yesterday.  We had mostly college students, but a few instructors and a husband and wife team who appeared to be in their late 70s too.  The older couple had accidentally wiped Windows when a few weeks ago when the husband tried Mint, Ubuntu, Fedoria and ChromeOS.  We had to tell them the bad news after looking at the 3 partitions on the system - 2 were formatted ext4 and the other was a linux-swap.  This was before we'd touched anything.

For most of the college kids, we struggled with SecureBoot, Windows8 if they wanted to dual boot. A few times, we failed and couldn't get passed the BIOS settings.  For their CS and engineering classes, Windows is expected by the school. NOT having Windows would cause most of them to fail their courses.

It was sad to see a kid with a brand new computer, but with a low-end processor, not be able to run VirtualBox well, then not be able to dual-boot.  At least we didn't harm anyone's system.

---

### Post by Bucky Ball on 2013-09-16
You would do so much better asking this on a Windows forum.

---

### Post by buzzingrobot on 2013-09-16
I've only tried with full installs, not OEM's. Repeated installation on the same machine is no problem. Installing on another machine while an install from that DVD is still on the first machine will prompt an activation failure. If the first machine has been wiped for some time, the second machine will activate via Microsoft's phone activation system. Microsoft, then, can associate specific machines with specific intstalls once, of course, networking is up.

This is activation, of course, not the actual install.  If memory serves, though, Windows will eventually disable itself if it isn't activated.

---

### Post by Kevin_Arnold on 2013-09-16
As far as using an OEM disc that comes with your computer, yes it will only install on that specific model of computer. It isn't JUST for that specific computer though.

For the retail (or system builders) version, they don't restrict the software from being installed on multiple computers. You can install it on as many computers as you can find (technically, not legally) but they will only let a few be activated. MS has no way of keeping Windows from being installed during set up without an internet connection.

Still, just buy the retail version that lets you run 8 on a few machines and be done with it instead of illegally running software.

---

### Post by Elfy on 2013-09-16
Thread Closed.

This is not the place to look into evading Windows restrictions.

---

