---
title: "[SOLVED] playing MIDI files"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by jrlii on 2007-04-15
Is there a simple way to play the MIDI (.mid) files which are used on many music sites as a shorthand for tunes?

I've installed all the stuff Ardour recommends, but haven't been able to figure out how to play a MIDI file yet.

For that matter is there a good tutorial on how to use Ardour?

My apologies if this is not the appropriate forum for the question.

---

### Post by ramjet_1953 on 2007-04-15
There is a package called [COLOR="Blue"]timidity[/COLOR], which should fill the bill.

You can download and install it using Synaptic.

Regards,
Roger :cool:

---

### Post by jrlii on 2007-04-16
Thanks, I'll give it a try,

---

### Post by ramjet_1953 on 2007-04-16
If you want a graphical interface, make sure that you have downloaded the following:

timidity
timidity-interfaces-extra
freepats
mozplugger

I don't think that it puts an item in the Applications>Sound and Video menu, though. (Slack Programming)

However you can edit that in Alacarte Menu Editor, or start the GUI in a terminal by typing

timidity -ig &

Regards,
Roger :cool:

---

