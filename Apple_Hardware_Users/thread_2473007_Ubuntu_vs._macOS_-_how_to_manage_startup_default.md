---
title: "Ubuntu vs. macOS - how to manage startup default?"
date: 2022-03-20
forum: Apple Hardware Users
---

### Post by mendiculus on 2022-03-20
[COLOR=#000000][FONT=Helvetica]After 34 years in the Macintosh environment (never used Windows), reading about  Linux for ~15 years (wanting to get into it but slowed by chronic illness), I'm finally starting to learn about it. So I've installed Ubuntu 20.04 LTS in a partition on my second MacBook Pro (13" 2014, 11,1), alongside several versions of macOS (using 10.12 Sierra as my primary). [/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]I've also installed rEFInd, started learning about it, but ran into some trouble, so removed it. [/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]I know I can switch between macOS and Ubuntu by pressing [FONT=&amp]&#8997;[/FONT] option during startup, then selecting whichever I want. For now I'm still mostly working in macOS, so have it set in Startup Disk Preference Pane as the default startup. [/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]However, if I start up in Ubuntu, then restart or shut down and start again, it defaults to Ubuntu. (In rEFInd terminology, a "boot coup".) I've experimented, repeatedly resetting macOS in Startup Disk, but every time I start Ubuntu, it takes over the default spot. (I'm not sure if it was doing this before I installed rEFInd, or started doing it only after I began using rEFInd. Anyway it's continued after I deleted rEFInd.) [/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]Is there some way I can tell Ubuntu not to do this? [/FONT][/COLOR]

---

### Post by linus-xu on 2023-01-30
Have you tried control-selecting Macintosh HD in the boot manager screen? Haven't installed Ubuntu physically in a while but this worked for me when some other distributions messed up the boot order.

---

