---
title: "No sound"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by x-ray vision on 2007-04-04
I just downloaded Ubuntu the other day and I have no sound. This is my first time using Linux so I'm totally new at this. I have a six year old Gateway computer with Sound Blaster Live!<br /><br />
----------------------------------------<br />

----------------------------------------<br />

---

### Post by oilchangeguy on 2007-04-04
open a terminal and type alsmixer then press enter. and see if the sound is set on mute.

---

### Post by x-ray vision on 2007-04-04
I got "command not found".

---

### Post by oilchangeguy on 2007-04-04
ok, try this. go to applications, add/remove. check show unsuported, then click on sound & video and install alsmixergui.

---

### Post by DaDave on 2007-04-04
x-ray --- it isn't alsmixer, it's alsamixer. Just go to your termianal and type alsamixer

---

### Post by x-ray vision on 2007-04-04
Okay, I installed alsmixer and I still have no sound. I tried typing alsmixer in the terminal again and pressing enter and I still got "command not found".

---

### Post by x-ray vision on 2007-04-04
okay, checking alsamixer now.

---

### Post by x-ray vision on 2007-04-04
I tried bring up the levels of everything that was set to 00 and that didn't work.

---

### Post by j002 on 2007-04-04
Go to Help-Ubuntu book excerpt-Problems with Ubuntu (or something like that) and read down about 2/3rds "Soundcards".

---

### Post by x-ray vision on 2007-04-04
I don't see "Ubuntu book excerpt" under Help.

---

### Post by finisdiem on 2007-04-04
Here dude this link should help [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Punker on 2007-04-04
hi I had the same problem for weeks try this post what it says I hate not haveing sound 
```

aplay -l

```
you can also try this you should here you speakers click if you do then that's good but their is still more to do just a bit and if ya don't here your speakers click the chip set is wrong and you'll have to search
```

sudo /sbin/modprobe snd-ca0106

```

also this sight will tell you the card's chip set you have to search
[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410,+P17&module=ca0106](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410,+P17&module=ca0106)

---

### Post by x-ray vision on 2007-04-04
Thanks for trying to help guys, but this crap is way over my head. Back to Windows.

---

### Post by Punker on 2007-04-04
:confused:

---

### Post by x-ray vision on 2007-04-05
> **finisdiem said:**
> Here dude this link should help [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
Thanks, bro! I decided to keep trying and that webpage helped me fix it. I had to un-mute a a selection in Alsamixer by pressing 'M'.

---

### Post by Punker on 2007-04-05
> **x-ray vision said:**
> Thanks, bro! I decided to keep trying and that webpage helped me fix it. I had to un-mute a a selection in Alsamixer by pressing 'M'.


good now go and write a book about it

---

