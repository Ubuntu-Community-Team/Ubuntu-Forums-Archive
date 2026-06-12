---
title: "grub dictates winxp bootup --- don't want that"
date: 2007-06-22
forum: Apple Intel Users
---

### Post by willnight on 2007-06-22
when i had vers. 6 of ubuntu installed on my macbook pro (not c2d), refit opted me with 3 icons: apple, linux and winxp.

when i click on winxp, i go directly there. and same with the other 2 oses.

i've just successfully installed ubuntu vers 7 (woot!).

grub installed successfully. however, it took over. when i click on the winxp icon at the startup refit menu, the screen goes blank and nothing happens.

after reboot, i click on the linux icon in refit and grub comes up with the linux boot choices, and also the winxp. when i select winxp, (with great joy) i return to the exact instance of windows where i left off (i.e. from hibernation). so essentially, i can still get to winxp without *any* disruption, but in an indirect way.

here's why i post: can someone show me how to fix this so that i can just click on the winxp in refit and go straight into windows? similarly, clicking on linux will go straight in, bypassing grub (i think i know how to do this part).

this forum is filled with so many smart people, and has been sooo indispensably helpful, that i am confident someone will have a solution for me ;)

thank you very much in advance.

---

### Post by ronocdh on 2007-06-22
Yes, this sucks. I believe the only thing you can do to achieve the desired results (rEFIt directly to WinXP) is to configure a bootloader like ELILO. This should allow you to go straight into Ubuntu without the GRUB screen even appearing. Since ELILO is EFI aware, it should be referencing the GPT, leaving the MBR free for Windows XP. Once ELILO is configured and running well, insert your WinXP installation disc and run the **fixmbr** command. This should reclaim the MBR for WinXP, allowing you to boot into it immediately from rEFIt.

This is how I understand it, but my knowledge is purely theoretical and not at all experiential; it's just too much work for me. ;) I just downloaded the WMWare Fusion beta to virtualize XP, and that runs pretty solidly. I'll have to check out how the "experimental 3D acceleration" holds up.

---

