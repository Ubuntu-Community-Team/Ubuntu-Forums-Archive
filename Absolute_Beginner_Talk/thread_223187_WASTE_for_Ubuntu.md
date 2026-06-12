---
title: "WASTE for Ubuntu?"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by limberlegs on 2006-07-26
Hello,

I'm wondering if anyone in the Ubuntu community could help me install and configure the [WASTE]("http://waste.sourceforge.net/") protocol.  I've successfully installed this on Windows before, but I'm a Linux noob and don't know the first thing about compiling, etc.  Alternatively, is there a  package out there that I could install instead?

I've heard that getting WASTE to work on Linux is more of a hassle than getting it to run under WINE.  I tried to run the exe file under WINE, but it just closed mysteriously after the first few configuratoin screens.  

I figured it would be best to try to get the Linux version working first, but if i have to settle for WINE, then so be it.

Thanks for your help!

---

### Post by RavenOfOdin on 2006-07-26
take it from me. . .Wine is a WASTE.  Half the programs in its repository are at "Garbage" status. 

:p

---

### Post by limberlegs on 2006-07-26
Heh... I suppose wine is kind of a "waste."  Seriously, though, has anyone ever used WASTE for linux, and if so, what do I need to do to get this working?

---

### Post by fallingcow on 2006-07-28
I've been trying to install it today, but no dice.

I tried the binary, but it seems to be compiled against wxWidgets 2.5, which is NOT in the repositories (2.4 and 2.6 are, I'm guessing that 2.5 was a development release).

Then I tried the source for the same thing.  The .configure stage went fine, but during compilation I got wxWidgets errors that seem strikingly similar to some that I ran in to when trying to learn Python+wxWidgets a few weeks ago.  My problem then was that even the demo code on tutorial sites would kick out erros.  I couldn't compile *any* of the wxPy code that I could find.

The problem?  Ubuntu inexplicably makes ONLY the Unicode-enabled version of wxWidgets available, and gives NO WARNING that very, very little source code will compile with it.  The vast majority of the tutorial demo code and actual project code written to work with this library are written WITHOUT Unicode support, and WILL NOT compile against a Unicode-enabled library.

Apparently, Waste, like almost everything else, is meant for the non-Unicode wxWidgets library.

You can probably go get the non-Unicode library and install it manually, but it's too much work for me.  I've given up.  There's a well-deserved bug report in the bug tracking system already, but I don't know if anyone's doing anything about it.

This is the only problem I've ever had with Ubuntu, but it really annoys me because it almost seems deliberate :-x

---

### Post by nalmeth on 2006-07-28
Come on Raven, that's not a very nice thing to say. :o

I've had a lot of great success with wine, and naturally a lot of frustration and failure. Of course, it's best to stay native, but I really appreciate what the WINE guys are doing. 

A LOT OF STUFF REALLY DOES WORK, AND WORKS WELL

Sorry to OP, I don't know what WASTE is, what it does, or how it works.

---

