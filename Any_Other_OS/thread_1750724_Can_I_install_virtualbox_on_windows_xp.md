---
title: "Can I install virtualbox on windows xp?"
date: 2011-05-05
forum: Any Other OS
---

### Post by jfloydb on 2011-05-05
I have never used VirtualBox before. But a friend wants me to install VirtualBox on his Windows XP machine, so he can try Ubuntu. While installing VirtualBox (on Windows XP), I encountered a warning stating that "The software you are installing has not passed Windows Logo testing to verify its compatability with Windows XP". My questions are: Should I ignore this warning? Is it safe to install and run VirtualBox on Windows XP. Have you installed Virtualbox on a computer running Windows XP. Thanks...

---

### Post by Telengard C64 on 2011-05-05
I don't know what you downloaded or where you downloaded it from. I can't recommend trusting the software.

The *Windows Logo testing* dialog would be a normal warning when installing uncertified drivers on Windows. VirtualBox does include drivers needed for (IIRC) directing network and USB access toward virtual machines. I would expect to see such a warning dialog when installing Virtualbox.

Having said all that, I know that I used Virtualbox on Windows for years with no trouble.

---

### Post by wojox on 2011-05-05
I've run it on XP and Vista with no problems. I never got that dialog box before. Did you download from the Virtualbox website?

---

### Post by Telengard C64 on 2011-05-05
> **wojox said:**
> I've run it on XP and Vista with no problems. I never got that dialog box before. Did you download from the Virtualbox website?

Had you [disabled signature checking](http://www.ehow.com/how_6869760_do-microsoft-signatures-windows-2000_.html)?

@OP, did you check your downloaded file against the MD5 and SHA256 hashes provided on the [VirtualBox Downloads page](http://www.virtualbox.org/wiki/Downloads)?

---

### Post by jfloydb on 2011-05-05
Thanks for the replies. I downloaded from [http://www.virtualbox.org/]("http://www.virtualbox.org/"); it seems like the right place. I'm surprized that no one else has (so far) encounter the same warning. But I don't think that I want to disable anything on someone elses computer. I'll check back later. Thanks again.

---

### Post by Telengard C64 on 2011-05-05
> **jfloydb said:**
> But I don't think that I want to disable anything on someone elses computer.

Nor should you.

So did you check the hash of the downloaded file or not?

---

### Post by wolfen69 on 2011-05-07
> **jfloydb said:**
> Thanks for the replies. I downloaded from [http://www.virtualbox.org/]("http://www.virtualbox.org/"); it seems like the right place. I'm surprized that no one else has (so far) encounter the same warning. But I don't think that I want to disable anything on someone elses computer. I'll check back later. Thanks again.

If you know you are on a safe site, then go ahead. It's not like windows has a package manager to download stuff. Last time I checked, you either *download* your apps or use an install cd for windows. And yes, virtualbox.org is the right place.

But on a side note, I had to use my windows 7 install that I use just for games, as my main OS for a couple days because my ubuntu drive died. Anyway, being in windows for me is like a fish out of water. I installed vbox in windows and installed ubuntu as a guest. Mind you, until this point, my win7 install worked perfectly with games and what ever else I did with it. But it choked on vbox. I have a pretty darn nice computer and windows couldn't handle it. I can run 2 guest OS's at the same time in linux with nary a hiccup. Anyway....

---

