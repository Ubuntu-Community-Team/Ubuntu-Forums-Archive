---
title: "Careful when updating, serious ATI bug in Dapper"
date: 2006-05-31
forum: Apple PPC Users
---

### Post by goofyheadedpunk on 2006-05-31
For those of you, like me, that happen to have ATI cards in your Apple machines please take note of bug [#47775]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/47775"). I'm currently bitten by it and my iBook is now pretty much unusable.

As usual, be careful when upgrading and happy hacking!

---

### Post by acorn22 on 2006-05-31
[QUOTE=goofyheadedpunk]For those of you, like me, that happen to have ATI cards in your Apple machines please take note of bug #47775[1]. I'm currently bitten by it and my iBook is now pretty much unusable.
[/QUOTE]


Does this apply to all ati cards? I think I have the ati card in my iBook (G4)

---

### Post by goofyheadedpunk on 2006-05-31
[QUOTE=acorn22]Does this apply to all ati cards? I think I have the ati card in my iBook (G4)[/QUOTE]

I don't know. My video card is an ATI FireGL Mobility T2e.

---

### Post by autocrosser on 2006-05-31
The desktop cards are pretty much OK--I was pleased when after the Xorg 7.0 upgrade was done that my 9600Pro even had acceleration--glxgears went from 170/200 to 850/950 with the radeon driver--had to setup the accelerator as "EXA" & run xcompmgr to get it---

---

### Post by Rxke on 2006-06-01
the olde ATIRage128 (first gen iBooks) seems unaffected, my iBook runs ok...

---

### Post by JackosKing on 2006-06-01
iBook G4 1Ghz, works fine.

---

### Post by asabjorn on 2006-06-01
I can confirm that this bug is also apparent on my HP compaq nc6000 laptop with an ATI Mobility 9600 graphics card. The computer freezes when running the screensaver for a few minutes in random picking mode.  Even ctrl+alt+backspace has no effect. This problem started on may 29th.

Thanks
Andreas

---

### Post by zojas on 2006-06-01
[QUOTE=goofyheadedpunk]For those of you, like me, that happen to have ATI cards in your Apple machines please take note of bug [#47775]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/47775"). I'm currently bitten by it and my iBook is now pretty much unusable.
[/QUOTE]

so what version of xserver-xorg-driver-ati do you have on your system? the bug entry isn't quite clear. is it version  1:6.5.7.3-0ubuntu7 which has the bug?

---

### Post by goofyheadedpunk on 2006-06-01
[QUOTE=zojas]so what version of xserver-xorg-driver-ati do you have on your system? the bug entry isn't quite clear. is it version  1:6.5.7.3-0ubuntu7 which has the bug?[/QUOTE]

I apologize. I've been ill for the last week or so and, as a result, my actions are a bit muddled (hence the two posts in the bug report with the same content an hour apart).

The ati driver is currently 1:6.5.7.3-0ubuntu7

---

### Post by goofyheadedpunk on 2006-06-01
[QUOTE=JackosKing]iBook G4 1Ghz, works fine.[/QUOTE]

How long have you been updated (1:6.5.7.3-0ubuntu7 ati driver and all that)? I've gone for nearly 12 hours once without a system freeze.

---

### Post by zojas on 2006-06-01
does it only lock up on you when you are running some GL application (3d) or xrandr or such? or have you had it lock up on you when you were websurfing or something like that?

I'm running the same version as you on my 700MHz g3 ibook. the only lock up I've had is that 3 times (out of about 25) it locks up when I try to wake it up from sleep.

---

### Post by jamessp007 on 2006-06-01
The ATI 7500 for eMacs is working in 1024x700 for 10.5 but not 6.06.   What has changed?

---

### Post by goofyheadedpunk on 2006-06-01
[QUOTE=zojas]does it only lock up on you when you are running some GL application (3d) or xrandr or such? or have you had it lock up on you when you were websurfing or something like that?

I'm running the same version as you on my 700MHz g3 ibook. the only lock up I've had is that 3 times (out of about 25) it locks up when I try to wake it up from sleep.[/QUOTE]

It locks up under normal use, not 3D work. In fact, given that the last time I fiddled with it the open source ATI driver couldn't do hardware 3D acceleration, xorg doesn't load glx. So, nope, nothing involving GL. xrandr I do not know about.

Lockups occur during all sorts of usage. Coding, typing papers for finals, reading pre-prints and so on and so forth.

---

### Post by kellogs on 2006-06-02
In my case I've got xserver-xorg-driver-ati version 1:6.5.7.3, Ive got DRI disabled and NO direct rendering under a powermac G5 radeon 9600. I would like to have 3d acceleration but....


[   63.592535] agpgart: Putting AGP V3 device at 0000:f0:0b.0 into 4x mode
[   63.592550] agpgart: Putting AGP V3 device at 0000:f0:10.0 into 4x mode
[   63.639420] [drm:radeon_do_init_cp] *ERROR* Cannot initialise DRM on this card
[   63.639423] This card requires a new X.org DDX

and glxinfo says:

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2

---

### Post by Ptero-4 on 2006-06-03
> The ATI 7500 for eMacs is working in 1024x700 for 10.5 but not 6.06. What has changed?
Did you mean 5.10? b/c 10.5 is the upcoming OSX release and 5.10 is breezy.

---

