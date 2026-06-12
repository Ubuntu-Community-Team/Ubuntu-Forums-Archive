---
title: "Macbook air and videoprojector"
date: 2010-06-29
forum: Apple Hardware Users
---

### Post by (Julien) on 2010-06-29
Hello everyone,

Has anyone managed to have his macbook air 2,1 work with a videoprojector in ubuntu ? I've read forums and blogs and it seems that basically the wonderful apple adaptator VGA/mini-displayport is not transferring the EDID information of the videoprojector to the nvidia drivers. The later thus only allow for resolutions up to 640x480, which is far from enough to give a talk.

I've read a couple of solutions to extract the EDID file from the projector, give them to xorg and reboot, but that's not practicable in a conference where any speaker taking more than 30 sec to set up his laptop starts to receive tomatoes :o)

Anyway, if anyone has some advice, that would be great.

cheers

Julien

---

### Post by buntuLo on 2010-06-30
my experience is different: the apple adapter IS transferring EDID infos, while most of the extension cables i found do NOT.
basically this meant that i never had problems in small conferences, where the beamer is usually sitting in the middle of the room and directly connected (with its own vga cable + apple adapter) to the laptop; while i never got it to work properly whenever a large beamer was hanging from the ceiling, and connected to a switch box between beamer and laptop.
i still do not understand how macosx and mswin deal with such situation. but somehow the do it brilliantly :~(

---

