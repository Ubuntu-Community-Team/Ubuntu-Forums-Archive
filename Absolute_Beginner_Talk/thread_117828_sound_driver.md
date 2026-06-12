---
title: "sound driver"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by allenyake on 2006-01-15
I have recently installed Ubuntu linux on my old P2 computer and everything went perfectly,except I have no sound.Everything else works fine,how do I get it to recognize my sound card.I have a soundblaster AWE64 soundcard.I am absolutly new to linux,this is my first ever expirience with it.I would appreciate any help.
Thanks Allen

---

### Post by lha on 2006-01-16
I remember once fighting with a SB AWE32. but I can't remember how we got it to work. Those isa PnP cards can be nasty. Your card is supported by Ubuntu, it just isn't detected automatically, so you can make it work. You might need to work for it, though. Hopefully Ubuntu wiki has correct info, because in that case things get easy.

The following advice was taken from [https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards]("https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards").

"Type 'sudo gedit /etc/modules' in terminal, then add 'snd-sbawe' at a separate line, save, quite, restart."

---

### Post by allenyake on 2006-01-16
thanks for the advice,it worked perfectly,I now have sound
allen

---

