---
title: "How important are updates?"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by paydaydaddy on 2007-01-25
:guitar: I have installed Ubuntu several times on the same machine. It works fine until I get the updates, Then pretty much everything breaks. I am pretty sure that it is hardware related. I put Ubuntu on my #2 computer and have kept #1 as a WinXP machine. Some initial diagnostics indicate some RAM problems that may or may not be related to the Motherboard. I plan to start piecing together a "best bang for the buck" machine that will become my linux machine and hopefully things will work better. In the meantime I intend to continue using the initial install without updates just to learn my way around Linux/Ubuntu. Is there any reason that I should be concerned about skipping the updates?

---

### Post by atomic drizzle on 2007-01-25
all the updates ive seen are just to fix bugs, update libraries, and the like.

---

### Post by ardchoille42 on 2007-01-25
Well, if an exploit due to a bug is found.. and you don't update.. you will basically be vulnerable to that exploit until you update. I don't know about you, but I am not comfortable with knowing there is an exploitable app or security hole sitting on my machine just waiting for some script kiddie to catch it. Bugfix and security updates are a necessity, in my opinion.

---

### Post by paydaydaddy on 2007-01-25
> **ardchoille42 said:**
> Well, if an exploit due to a bug is found.. and you don't update.. you will basically be vulnerable to that exploit until you update. I don't know about you, but I am not comfortable with knowing there is an exploitable app or security hole sitting on my machine just waiting for some script kiddie to catch it. Bugfix and security updates are a necessity, in my opinion.

But if bug fixes and security updates break the OS then maybe the risk from script kiddies is not enough to worry about. Based on the past 4 or 5 installs I have done on this machine in the past 2 weeks I have to treat this as a temporary experiment anyway. Any more opinions?

---

### Post by deadgobby on 2007-01-25
I wounder if the Linux Kernal update is making it buggy?
Gobby

---

### Post by ardchoille42 on 2007-01-25
> **paydaydaddy said:**
> But if bug fixes and security updates break the OS then maybe the risk from script kiddies is not enough to worry about. Based on the past 4 or 5 installs I have done on this machine in the past 2 weeks I have to treat this as a temporary experiment anyway. Any more opinions?

I have been using Ubuntu on 11 machines since Warty and have never had anything break due to updates. It's quite possible that you're installing something from a 3rd party repo (or maybe a debian .deb package) that replaces system files, then the updates are breaking because the files they expect aren't present. Are you using 3rd party repos? or maybe .debs that were designed for debian or some distro other than Ubuntu?

---

### Post by 3rdalbum on 2007-01-25
I don't keep my system up-to-date; my core packages are more like 6.06 than 6.06.1.

But, you know what? I still look and see what each update does for each package. If it's a bug fix, and I've been bitten by the bug before, I'll upgrade. If it's a privilege escalation that can only be done with physical access to the machine, then I won't bother. If it's a remote vulnerability that's in a package I rarely use, I don't bother to update. However, if it's a remote vulnerability in something I use all the time, and I've heard of people getting attacked through it, then I'll more than likely upgrade.

I don't think you should be concerned - some of us are still running Breezy systems without problems.

---

### Post by paydaydaddy on 2007-01-25
I have just installed the update that show up when you click the little orange square in the upper right (dapper). Do I need to know what each recommended update is and who it is from? I have looked at the descriptions and with my limited knowledge could not tell what some of them were. There were some that included Dedian in the file name.

---

