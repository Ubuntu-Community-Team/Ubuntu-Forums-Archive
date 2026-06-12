---
title: "Playing windows games in Cedega"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by SlyReaper on 2007-12-20
OK, I just forked out over 10 quid so that I could use Cedega, because I understood that was the only way to get windows games to run under linux.  

But it doesn't work!

So far, I've tried two games: Deus Ex and Eve Online Classic (both fairly old games, so shouldn't be a problem, right?)

Well when I try to run Eve, it tells me I don't have sufficient privileges to install the required D3DX thingamywhatsit.  It's **my** bloody computer!  One of the reasons I'm trying to break away from windows is to get away from that kind of BS!  Rant over.  Anyway I keep clicking "yes" as it suggests, and that error message just keeps popping up until I click "no" and the program closes.

When I try to run Deus Ex, it shows the "Sold Out Software" splash screen for a while, and my CD tray makes encouraging noises, but then it just closes without any error message.

Have I forgotten some vital step in getting Cedega to work properly?  I'd really like to be able to run my games under ubuntu - that way, I can finally break away from having to use Microshaft operating systems.  Thanks for any help.

---

### Post by moocow1452 on 2007-12-20
Wait, who told you that Cedaga was the ONLY way to run Windows programs in Linux. There is the old standby Wine, based on the same archetecture as Cedaga, and completly open-source. I myself haven't had many problems with it, and none that I couldn't fix with some Foruming.

Edit: Forgot the Website...
[http://www.winehq.org](http://www.winehq.org)

---

### Post by SlyReaper on 2007-12-20
I tried Wine before trying Cedega.  Again, it told me I didn't have sufficient privileges to install the d3dx thingy.

---

### Post by moocow1452 on 2007-12-20
It would seem you have a privliges problem more than anything else. Try running the Program through the terminal with a sudo on the front. 

I'm new with Ubuntu, too. So I'll do the best I can on my end.

---

### Post by SlyReaper on 2007-12-20
If i try and run it through the terminal with the line "cedega eve.exe" or "sudo cedega eve.exe", it comes up with a different error message:  Windows 2000 SP2 or higher required. :confused:

---

### Post by LowSky on 2007-12-20
your issue is DirectX. DirectX is a Windows only application  that most games run on. OpenGL being the other... Since DX is a propietary program that Microsoft owns, it is hard to get some windows games to play on linux. There are some work arounds and some games can emulate DX and use openGL. This has to be set up in Wine/Cedega  to the correct version if availible (i think wine can fake DX8 and DX9 but not DX10). All of this can be set up in ther config files. Since your paying for Cedega go to their website and see if they ave any instrunction for installing hte games.

---

### Post by moocow1452 on 2007-12-20
Never mind...

---

