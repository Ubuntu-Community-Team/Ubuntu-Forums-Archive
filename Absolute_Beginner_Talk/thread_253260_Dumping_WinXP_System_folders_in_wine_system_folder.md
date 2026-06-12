---
title: "Dumping WinXP System folders in wine system folders??"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-09-08
Will dumping my windows xp system and system32 folders in the Wine system and system32 folder help me at all in anyway, with getting win apps to work in wine?

---

### Post by orb9220 on 2006-09-08
Nope it will totally hose your wine install. Do not do that!. Wine is not intended to run everything from windows. You can't force it to work. 

You need to go to [http://www.winehq.com/](http://www.winehq.com/) to check for the apps you would  like to use. If wine can't run it then wine can't run it.

That is why many including myself have a dual boot system. For those few programs we need and games.

Which programs do you want to run?

---

### Post by bodhi.zazen on 2006-09-08
> **WalmartSniperLX said:**
> Will dumping my windows xp system and system32 folders in the Wine system and system32 folder help me at all in anyway, with getting win apps to work in wine?

Yes. But I would do it selectively.

One thing you should know about wine, Wine is updated frequently and each version is unique. What is broken in 1 version may work in another and visa versa.

another is it depends on how you configure wine. winecfg is a minimal configuration, minimal microsoft code. Sidenet and Winetools are other methods. I use sidenet although winetools is most popular on Ubuntu.

Some windows native dll's will either not run or conflict with wine. Let me show you...

type winecfg in a terminal....

In the "applications" tab select "default settings" then click on the "Libraries" tab.

This is a list of dll's and how wine will use them by default. Builtin = Provided by wine. Native=Taken form windows.

If you copy a dll you will configure this tab, possible per application.

How do yo know what to do? WineHQ -> search for application.

HTH. 8)

Edit: Wine native dll's can conflict with windows dll's.

---

### Post by WalmartSniperLX on 2006-09-08
> **orb9220 said:**
> Nope it will totally hose your wine install. Do not do that!. Wine is not intended to run everything from windows. You can't force it to work. 

You need to go to [http://www.winehq.com/](http://www.winehq.com/) to check for the apps you would  like to use. If wine can't run it then wine can't run it.

That is why many including myself have a dual boot system. For those few programs we need and games.

Which programs do you want to run?

Ive been trying hard to get SonicStage to run so I can put music on my sony walkman mp3 player

---

### Post by WalmartSniperLX on 2006-09-08
> **bodhi.zazen said:**
> Yes. But I would do it selectively.

One thing you should know about wine, Wine is updated frequently and each version is unique. What is broken in 1 version may work in another and visa versa.

another is it depends on how you configure wine. winecfg is a minimal configuration, minimal microsoft code. Sidenet and Winetools are other methods. I use sidenet although winetools is most popular on Ubuntu.

Some windows native dll's will either not run or conflict with wine. Let me show you...

type winecfg in a terminal....

In the "applications" tab select "default settings" then click on the "Libraries" tab.

This is a list of dll's and how wine will use them by default. Builtin = Provided by wine. Native=Taken form windows.

If you copy a dll you will configure this tab, possible per application.

How do yo know what to do? WineHQ -> search for application.

HTH. 8)

Edit: Wine native dll's can conflict with windows dll's.

Ok thanks Ill do the winecfg config :D

---

