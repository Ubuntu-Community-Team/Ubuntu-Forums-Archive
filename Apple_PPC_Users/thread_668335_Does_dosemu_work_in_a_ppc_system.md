---
title: "Does dosemu work in a ppc system?"
date: 2008-01-15
forum: Apple PPC Users
---

### Post by kansas_plainsman on 2008-01-15
Just a quick question: Does dosemu work in linux for ppc?

---

### Post by PaganHippie on 2008-01-16
Is dosemu even in the PPC repos?  Let me look....  Nope, not there.  So, my suspicion is that the answer to your question is 'no.'

Oddly, though, there is another DOS emulator that is in the PPC repositories -- dosbox.  It claims to not only emulate DOS but also the x86 processor.  I'm installing it on a G3 now to see whether it works....  And, somewhat to my amazement, it does!

If dosbox will do for you what you wanted from dosemu, you're in luck.  I've used both on the x86 side, and found that often one will run a given program better than the other.  If you don't mind my asking, what are you wanting to run?

---

### Post by kansas_plainsman on 2008-01-16
> If you don't mind my asking, what are you wanting to run? 

Recently I've started taking notes and maintaining a journal on an old compaq LTE running DOS and an old favorite: "Boxer", a programmers text editor (a Brief clone).  That got me interested in some of the other software titles in my archives - Quatro Pro, several Borland 'Turbo' titles, even Sidekick...

Anyway, if I could get DOS to run in some fashion on a ppc-based ubuntu, I could move some of those to one of my old Mac laptops.

It was really more curiosity than anything else - the main reason I liked the compaq running DOS was that it powered up and was ready to go in about 20 seconds - and powering down is a matter of saving the file and hitting the switch.  Running the same editor in dosemu in linux would loose most of that utility.  But.. The compaq's battery pack is shot, and it uses a size of NIMH battery cell which has become impossible to find.  Works great as long as I'm in extension cord reach of AC.  (A neat side trick: I'd pulled the 20MB laptop drive out of it, and replaced it with a 1 gig CF card and IDE adapter; now it boots VERY fast).

Another problem is the compaq's keyboard was getting balky and sticky, and I've never had good luck cleaning laptop keyboards sufficiently to fix that.

My solution was direct: I bought a modest modern laptop, and installed FreeDos on the first two gigs of the drive, and Kubuntu on the rest.  Now when I want to make a journal entry, I'm up and running in less than 30 seconds, but I also have Linux for more serious work, but on the go.

---

### Post by stmiller on 2008-01-16
qemu runs fairly good on powerpc Linux. Install qemulator for a nice interface.

---

### Post by VidiotGeek on 2008-01-16
> **kansas_plainsman said:**
>  (A neat side trick: I'd pulled the 20MB laptop drive out of it, and replaced it with a 1 gig CF card and IDE adapter; now it boots VERY fast).

.....

My solution was direct: I bought a modest modern laptop, and installed FreeDos on the first two gigs of the drive, and Kubuntu on the rest.  Now when I want to make a journal entry, I'm up and running in less than 30 seconds, but I also have Linux for more serious work, but on the go.

First, the CF card HD replacement is genius! That's an awesome mod. I don't know any CLI well enough to use it as a primary OS, but that sounds like a damn good setup once I know my way around better.

---

### Post by stream303 on 2008-01-17
The boxer editor - who'd have guessed this would come up on the PPC forum, as I loved boxer as well.

For journals, especially for keeping notes and clippings of info found right here, I tend to just use a Firefox addon: SCRAPBOOK.  I couldn't use the Ubuntu forums without it.

When I discovered Linux back in 95 the only editor I found to be dos-like was JOE, but I finally gave in and actually learned to like VI - but no need to start a boxer vs VI flamewar. :)

I actually ran a Fidonet BBS on a Mac-Plus for several years in the early 90's and wished for a mac version of boxer!  Alas.....

Brought back some good memories guys....

---

