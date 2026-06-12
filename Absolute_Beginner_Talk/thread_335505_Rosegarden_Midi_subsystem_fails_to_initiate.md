---
title: "Rosegarden Midi subsystem fails to initiate"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2007-01-10
Okay, so I've installed Rosegarden, and it looks decent. But when I try to play a midi file, it tells me the subsystem has failed to initiate. This leads me to think that I may not have a proper codec installed. Am I close?

---

### Post by Centx on 2007-01-25
Bump...

---

### Post by jonny on 2007-01-25
Rosgarden is great.  I'm no musician but my kids spend hours loading up their favourite music and composing new stuff.

However, it's not remotely intuitive to get Rosegarden working.  It depends on two things:

 - a working midi setup (this isn't included in a default Ubuntu installation due to space constraints on the CD-ROM)
 - The Jack audio daemon.  Most Linux programs aimed at musicians rely on Jack, as it offers a high-quality, low latency sound transport mechanism.

The Ubuntu Wiki has advice on getting midi going - note that the instructions differ according to the type of soundcard that you have.  If you're in doubt you probably need to go down the software synthesis route.  The wiki recommends using Timidity, but I've found that the alternative Qsynth / Fluidsyth give better results.  The easiest way to get Jack working is to install QJackctl and Jackd.

Before starting up Rosegarden you need to first use qjackctl to start jack (note that you won't get sounds from any other program while Jack is running), next start your midi synthesiser and then, finally, fire up Rosgarden.  One further tip - one of my motherboards thinks that it has a hardware midi port that doesn't actually exist.  As a result, the first bank of instruments in Rosgarden doesn't make any noise.

All this is a little complex to set up the first time, but it's reasonably well documented if you google a little.

---

