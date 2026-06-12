---
title: "Of what kind is the ubuntu / linux operating system?"
date: 2012-05-15
forum: Any Other OS
---

### Post by abijosh on 2012-05-15
windows is an event *driven operating system*.. 

what kind of operating system is a linux based operating system?

---

### Post by rai4shu2 on 2012-05-15
Linux is a highly modular, monolithic system. (see [the wiki]("http://en.wikipedia.org/wiki/Linux"))

---

### Post by abijosh on 2012-05-15
Thanks for clearing my doubt..

---

### Post by TeamRocket1233c on 2012-05-15
What about BSD?

---

### Post by abijosh on 2012-05-16
it must be a monolithic kernel type.. am i right.. correct me if i'm wrong.. :D

---

### Post by rai4shu2 on 2012-05-16
It's rather unusual to see a microkernel design like MINIX. Most OSes tend to be at least mostly monolithic in nature. It reflects the monolithic nature of the hardware it's run on.

see [http://en.wikipedia.org/wiki/Comparison_of_operating_systems](http://en.wikipedia.org/wiki/Comparison_of_operating_systems)

---

### Post by QIII on 2012-05-17
Oh. Yes.

There are no choice but Unity.  A shame really.  I'd like to use KDE and XFCE.  Oh, wait! I do!

Gun to head.  Unity or nothing.  Maybe you think it's crap.  You see it everywhere on the web, right?  What you have to ask yourself is this:  knowing human nature, how many people get on the web to complain when things work just fine and please them?  What you see is called "referral bias" and any conclusions reached from data suffering from that condition is invalid.  Some people certainly DON'T like it.

Maybe Shuttleworth IS listening to the user base and not the web bloviators.

Unity is different, to be sure.  Things change.  Maybe they shouldn't.

[IMG]http://upload.wikimedia.org/wikipedia/en/1/15/Windows_3.0_workspace.png[/IMG]

---

### Post by billyseth on 2012-05-17
I am giving Unity another chance, mainly because I cinnamon is still a bit buggy. Also, Xubuntu didn't detect all my hardware as flawlessly as Ubuntu did (which seemed pretty strange to me). Either way, Unity is growing on me a bit, and hopefully as gnome3 matures more, there will be more theme/customization options.

---

### Post by QIII on 2012-05-17
I didn't like Unity at first.  I detested it.  It ticked me off so much that I started using my Debian box almost exclusively.  I thought it looked like a tablet rather than a desktop.

But then I realized that such might have been the point.  It's where the market is moving.

"Ah!  Wait a minute.  Let me look at it from the standpoint of tomorrow, not today!"

Fits right in.  Ahead of the curve.  Microsoft has even seen the future with Win8.

I still don't use it most of the time, but I do for a couple of the servers I run apps like BOINC and some @Home type projects on where the graphical interface is easier to use.  Just connect with Nomachine NX and it's like you're really there.

I think there was an initial reaction that people just didn't get over.

OK.  Enough of the off-topic chatter for me.

I'm out.

---

### Post by rai4shu2 on 2012-05-17
> **QIII said:**
> ... Gun to head.  Unity or nothing. ...

I think you're posting in the wrong thread, there. This thread is about the basic design of the kernel (unless I misread something).

---

### Post by QIII on 2012-05-18
> **rai4shu2 said:**
> I think you're posting in the wrong thread, there. This thread is about the basic design of the kernel (unless I misread something).

No, I actually posted here on purpose.  A post above mine, now removed, contained questionable language content.

The poster described what sort of an OS he thought Ubuntu was -- based on his clear distaste for the Unity DE -- in somewhat "colorful" language.

---

### Post by rai4shu2 on 2012-05-18
Ah. That explains it.

Well, at the risk of using a "colorful" metaphor, that post's owner was dancing alone (so to speak). :D

Back on topic: I really like the idea of microkernels, and the Amiga was a particularly brilliant design. Haiku seems to be moving in a similar direction.

---

### Post by LeGasp on 2012-05-19
Something interesting about BSD (which was mentioned a few posts up) is that it is a true descendant of the original UNIX of Bell Labs. Its kernel has been ported to Debian, but I'm not sure why anyone would use it outside of its native userland, besides the fact that it's interesting.

---

### Post by abijosh on 2012-05-21
Ur discussions are going too far from what i can understand :O too bad for me.. :(

---

### Post by abijosh on 2012-05-21
> **QIII said:**
> 

[IMG]http://upload.wikimedia.org/wikipedia/en/1/15/Windows_3.0_workspace.png[/IMG]

what is this screen shot doing here? any explanation please.. as far as i can understand. *'is it showing the development from old ... very old desktop environment to the current one?? '*

---

### Post by roelforg on 2012-05-21
> **abijosh said:**
> what is this screen shot doing here? any explanation please.. as far as i can understand. *'is it showing the development from old ... very old desktop environment to the current one?? '*

It's a shot from the win3.x series (pre-1995), it shows how windows has taken monolithic up a step by putting the gui in the kernel (though technically windows was itself little more then a de running on msdos back then but it did have it's own drivers and everything so it did almost everything the msdos kernel did (didn't linux start out similar to this as well?)).

---

### Post by rai4shu2 on 2012-05-21
Windows *was* just a DOS shell until Windows 2000. In Windows 98, you could still drop down to DOS and run applications without all that low level overhead.

It wasn't really until Windows XP became relatively stable (around 2005) that you could safely disregard DOS on a PC. :D

---

### Post by Morbius1 on 2012-05-21
> Windows *was* just a DOS shell until Windows 2000.
A minor point in the grand scheme of things but I think you meant Windows NT.

---

### Post by abijosh on 2012-05-23
> **rai4shu2 said:**
> Windows *was* just a DOS shell until Windows 2000. In Windows 98, you could still drop down to DOS and run applications without all that low level overhead.

It wasn't really until Windows XP became relatively stable (around 2005) that you could safely disregard DOS on a PC. :D
one of the mistakes they did is to let dos simply go off.. its one of a very stable os as far as i know..

---

### Post by abijosh on 2012-05-23
> **roelforg said:**
> it shows how windows has taken monolithic up a step by putting the gui in the kernel 

can u explain clearly.. pls.. thanks :D

---

### Post by Morbius1 on 2012-05-23
> **abijosh said:**
> one of the mistakes they did is to let dos simply go off.. its one of a very stable os as far as i know..
The NT branch of Windows from WinNT 3.? to Windows 7 ( WinNT 6.1 ) could always run dos programs because of the NT Virtual DOS Machine ( NTVDM.exe ) which is a virtual machine that actually runs on top of Windows. Correction: That's the 32 bit version of Win7.

Don't know how well it actually works in Win7 as I can't seem to find any DOS programs around to test it :)

---

### Post by rai4shu2 on 2012-05-23
For the older systems (P3 or older) the DOS box was a signficant amount of overhead. Since P4 and newer, it's barely noticeable. The bigger problems always revolved around the ever-changing APIs and undocumented APIs and the nonexistent documentation for all that. Being a Windows developer over the past ten years has been a scary ride (especially if you worked on hardware at all).

---

