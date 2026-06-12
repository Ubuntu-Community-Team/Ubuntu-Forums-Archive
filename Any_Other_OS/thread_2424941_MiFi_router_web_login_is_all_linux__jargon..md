---
title: "MiFi router web login is all linux  jargon."
date: 2019-08-17
forum: Any Other OS
---

### Post by orbitmipi on 2019-08-17
Hi

I'm a noob to linux. MyFi router is not giving me my default log in page. I get msg ;

 [COLOR=#000000]/usr/lib/lua/luci/dispatcher.lua:582: bad argument #1 to 'pairs' (table expected, got nil)[/COLOR]stack traceback:
	[C]: in function 'pairs'
	/usr/lib/lua/luci/dispatcher.lua:582: in function 'createtree'
	/usr/lib/lua/luci/dispatcher.lua:230: in function 'dispatch'
	/usr/lib/lua/luci/dispatcher.lua:195: in function </usr/lib/lua/luci/dispatcher.lua:194>


What does all this mean ?

I have had homeinvashion with evidence of person('s) at pc desk. I have had lots of cyber attacks.

---

### Post by TheFu on 2019-08-17
Which version of Ubuntu are you running?

---

### Post by orbitmipi on 2019-08-18
> **TheFu said:**
> Which version of Ubuntu are you running?
I'm not. But I can if it help's

---

### Post by The Cog on 2019-08-18
So you are asking here because what you see looks like Linux stuff. Makes sense.

It may well be Linux stuff, because I see linux-like error messages referring to stuff in /us/lib. Lua is a scripting programming language. The error messages indicate that whatever script is being run (presumably the one that issues the home page) is misbehaving somehow. It appears that some of the scripts inside the router (or the data they deal with) have become corrupt.  Without knowing a lot more about your router, I don't think we will be able to help more than that. A knowledge of Linux is not going to be enough to tell what's wrong inside the router.

---

### Post by jeremy31 on 2019-08-18
Moved to any other OS as I doubt there is a way to determine what exactly the router is running

---

### Post by DuckHook on 2019-08-18
> **orbitmipi said:**
> …I have had homeinvashion with evidence of person('s) at pc desk. I have had lots of cyber attacks.
Here's what I would suggest:

[LIST=1]
[*]Even if your router is running Linux, it is not running Ubuntu (no commercial router does), so this forum will be of limited help to you.
[*]If there is even the slightest chance that your router has been compromised, get a new router. Throw the old one in the river—well—not literally in the river, but you know what I'm saying.
[*]If you run any Windows boxes at home, make sure they have anti-malware installed out the yin-yang. If possible, back up all crucial data, nuke Windows and reinstall.
[*]If you run Ubuntu boxes, back up all critical data, then nuke the Ubuntu OS and reinstall virgin OSes from scratch.
[*]Ditto with all mobile devices.
[*]Do all of the above concurrently so that your HW cannot reinfect each other.
[/LIST]
What do you mean by cyber attacks? How do you know you've been attacked? What do these attacks look like?

---

