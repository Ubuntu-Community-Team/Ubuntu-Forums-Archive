---
title: "Need to figure out whats broke this time..."
date: 2011-08-12
forum: Any Other OS
---

### Post by memilanuk on 2011-08-12
Okay... bought this HP desktop PC in summer 2009.  Since then I've upgraded the video card, replaced the power supply when it tanked on me, and now I'm wondering if the HDD is going T.U. also.

This particular machine is running straight Windows Vista 64-bit (got Ubuntu on the laptop that I use most often, and on an old PC masquerading as a 'server') as it gets used mostly for games, and watching some movies, etc.  No linux anywhere on it.  

I hadn't used it for a while and when I went to make sure it was off, not just sleeping, before summer vacation, I found it was really 'off' - as in DOA!  Fired it back up, started looking around as for what caused it to turn off and - it just powered off.  No warning, no nothing.  One second its on, the next nothing.  Black screen, all power lights on the main chassis are off, dead to the world.  

I checked the fan(s) on the back to see if they were moving spinning/ moving air, which they appear to be.  I'm not really sure what to try next - the dang thing bombs out in the middle of any diagnostics I try running from Windows.  Previously, I had gotten a warning from some diagnostic software bundled with the machine that there was a bad sector or two on the HDD, which is pretty much the only reason I'm even looking that direction.  Otherwise, it kinda seems like something with the PSU or another fan/cooling issue...

I'm probably going to burn a Ubuntu 11.04 live CD just to boot off of and see if it stays running - hopefully isolating whether its a HDD problem or not.  Are there any purpose-built trouble-shooting live CDs out there that are more oriented around diagnostics?  I'm familiar (in passing) with System Recovery CD - not sure that its come to that just yet - then again I'm under the impression its mainly for backing up / restoring disk info, not necessarily figuring out whats going gunnybags on a running system...

TIA,

Monte

---

### Post by mips on 2011-08-13
Micro-Scope Diagnostic Suite

---

### Post by memilanuk on 2011-08-13
While I'm sure thats very good stuff... just for the sake of discussion, how about products that are FOSS? ;)

---

### Post by 23dornot23d on 2011-08-13
Can you try it in another machine ...... 

also [Smartmon]("http://www.google.com/search?hl=en&client=ubuntu&hs=lRw&channel=fs&q=smartmon+linux&aq=f&aqi=g1g-v1&aql=&oq=") tools .... for the drive will let you know
if its failing or not .....

---

### Post by memilanuk on 2011-08-13
> **23dornot23d said:**
> Can you try it in another machine ...... 

Not easily.

> 
also [Smartmon]("http://www.google.com/search?hl=en&client=ubuntu&hs=lRw&channel=fs&q=smartmon+linux&aq=f&aqi=g1g-v1&aql=&oq=") tools .... for the drive will let you know
if its failing or not .....

According to smartmon (the short/quick test) the drive is healthy.  If I try running the extended/long test the machine is b0rked by the time I come back.  In Vista, its just shut off.  Using a Linux live CD (either Ubuntu 11.04 or Debian 6.01) the display goes wacko and the system is unresponsive.  

Kinda getting the feeling it may *not* be the drive... almost acting like something runs til it gets hot, then quits.

---

### Post by 23dornot23d on 2011-08-13
What graphics card did you put into it ..... and is the PSU man enough for the job ...

Sometimes when adding graphics cards you have to be careful you do not push the

PSU beyond its limits ...... 

You could possibly remove the Graphics card and use the onboard vga if it has it
and just test to see if its that ......

Another thing is memory ..... that would lock it up ..... check its clean and seated properly .....

not got a real lot to go on here  .... but the fact it died at some point yet came back to
life ...... may mean a component somewhere is failing ..... could be on the motherboard

could be on the graphics card .... ( but you may be able to isolate the problem )

could be a piece of bad memory ..... but doubtful ....

PSU ..... quite possible ..... if its only when its been run for a while .... and if you
start loading it more with some thing graphic intensive too ..... then that could be 
the problem with both the graphics card wanting more power and the PSU not being able to supply it ......

Who knows ...... :confused:

---

### Post by Kromgol on 2011-08-14
Did it just turn off directly? Without going through the POST screen or anything? If so, it's not a HDD problem.

Possible reasons are PSU, GPU or the motherboard.

---

