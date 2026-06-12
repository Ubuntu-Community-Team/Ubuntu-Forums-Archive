---
title: "Macbook Pro 3,1 - Black screen start - will not boot Live"
date: 2011-07-25
forum: Apple Hardware Users
---

### Post by Fictitious1 on 2011-07-25
Ok so I am open to suggestions and comments.  I know there are a few questions [COLOR=Red](in red)[/COLOR] so just answer what you are able if you happen to read through this. Here's the situation,

I've got a macbook pro 3,1 that will not boot - period.  I am guessing its a kernal panic somewhere caused by a faulty piece of hardware.  It will also not boot into OSX - Kernal panic after verbose stops me at like Yukon Adapter or DSMOS - I pulled the Yukon from kext and still could not get it to boot so ? Also pulled the sleep image from /var/ that I read some suggest - Still no boot into OSX - So I said I am going to put ubunutu on it let me try to boot the live and see what happens.  I've done the reset PRAM thing as well, [COLOR=Red]would it matter if PRAM is reset before a Ubuntu LIVE Boot?[/COLOR]

No go, cd comes up option menu (says Windows? strange)  but when it spins up it turns screen black with backlight and keeps spinning up but never boots or shows anything, not even the deb linux top bar.  I took cd to other macbook pro, worked fine.  So read something to get the mac specific nightly  11.10. Burned it, no go.  Read get rEFIit got it. booted to the rEFIt menu fine and tried to boot a "installed" Ubunutu on a USB stick "legacy mode" but it said it could not -- so still no go.  I read some reports on other dell's with the nvidia and black screens had to change something, but I never get anywhere to change and it should be in VGA mode so never even load those drivers... tried hooking up to external monitor..no go.  Tried other RAM no go..

[COLOR=Red]So how to I find out where / if it is kernal panic in Ubunutu? Would installing it via target disk/ or to an external USB and booting make a difference?  **_Can I isolate a possible malfunctioning piece of hardware ie the lan adapter and keep it from checking? _**How does Ubunutu even do that? will it skip something that gives an error?  [/COLOR]

[COLOR=Black]Thanks for any suggestions etc. I need to walk away from it because its one of those frustrating things that you feel so close but just can't get it to go.


[/COLOR]

---

