---
title: "PCMCIA Services...Fail"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by KJB on 2006-05-05
As the title suggests when i try to run the Livecd and it fails.

first saying PCMCIA Services .... [fail]

then later saying -     "- bash: no Job control in this shell"

i am attemting this on my laptop:  Advent 7088: AMD sempron 2800+


i am a complete beginer at this linux stuff, i have just had enough of windows, and the useless programs and files that i have absolutly no use for.

i really just want to get familiar with a linux operating system before i build my new PC in coming months.

any help resolving this livecd issue will be greatly appreciated.

---

### Post by cgjones on 2006-05-05
Do you have any PCMCIA cards plugged into the laptop when you try to boot from the live CD? If you do, you might want to try and remove them, then boot from the live CD, then plug them back in once the live CD is fully up and running.

---

### Post by KJB on 2006-05-05
no i do not have any PCMCIA plugged in.

---

### Post by archis on 2006-05-26
This might be a bug introduced by upgrading pcmciautils. It was reported by users who noticed it on machines that don't have PCMCIA devices. It is apparently caused by a duplicate file in /etc/default/. 

See Launchpad bugs [#37631]("https://launchpad.net/distros/ubuntu/+source/pcmciautils/+bug/37631") & [#38368]("https://launchpad.net/distros/ubuntu/+source/pcmciautils/+bug/38368")

Daniel Silverstone writes in a comment:

[INDENT]
[B][COLOR="DarkSlateBlue"]re. Spurious failure message on systems which don't have PCMCIA hardware
[/COLOR][/B][/INDENT]

[INDENT]It looks like you have spurious [FONT="Courier New"][COLOR="DarkSlateBlue"]**/etc/default/pcmciautils**[/COLOR][/FONT] files.

Those files come from the preinstall of pcmciautils and are a copy of [FONT="Courier New"][COLOR="DarkSlateBlue"]**/etc/default/pcmcia**[/COLOR][/FONT]  if it was present. (this copy is only done if installing from scratch or upgrading from a pcmciautils from months ago)

I recommend you [COLOR="DarkSlateBlue"]**remove the /etc/default/pcmciautils**[/COLOR] file and see if this goes away.[/INDENT]

I would suggest checking for the existence of [COLOR="DarkSlateBlue"]**pcmciautils**[/COLOR] alongside [COLOR="DarkSlateBlue"]**pcmcia**[/COLOR] in /etc/default/ and safely remove it with

[COLOR="DarkSlateBlue"][FONT="Courier New"]sudo rm -iv /etc/default/pcmciautils[/FONT][/COLOR]

---

