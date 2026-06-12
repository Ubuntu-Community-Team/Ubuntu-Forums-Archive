---
title: "Strange Red Light In Headphone Jack MacBook 4,1"
date: 2010-05-31
forum: Apple Hardware Users
---

### Post by ArtemT on 2010-05-31
I was fooling around with 10.04 last night and noticed some strange red light to the side of my macbook (left). I look over and there's a red light glowing inside of the headphone jack. Insanely confused. It's not a laser so it can't be an optic headphone jack, right? Thoughts?

---

### Post by tgalati4 on 2010-06-01
It's either a digital outlet port or a miniturized version of HAL 9000.

"Open the Door, HAL"

Get a TOSlink cable and plug it into your stereo system.  It might actually work.

---

### Post by sha.goyjo on 2010-06-01
> **tgalati4 said:**
> It's either a digital outlet port or a miniturized version of HAL 9000.

"Open the Door, HAL"

Get a TOSlink cable and plug it into your stereo system.  It might actually work.

It's a digital port. It's standard, dude.

EDIT:
Sorry, that came off sassier than I meant. Yes, confirmed, it is a digital port. Also, the only thing scarier than full size HAL 9000 is miniature HAL 9000

....or perhaps maybe just HAL.

---

### Post by linuxopjemac on 2010-06-01
digital audio port. You can disable the light with alsamixer, it's something with IEC958... I don't remember. mute it with "m". If you insist, I check it on my MacBook, I am working on my Pismo now.

maybe this will work too
```
amixer set IEC958 off
```

---

### Post by Craig Magner on 2010-06-01
Think its something to do with drivers on the macbook. Itll be fine :)

---

### Post by funkwurm on 2010-06-01
I have this happen under Mac OS X sometimes, if you put the jack not all the way in, a connection is made that triggers a "this must be an optical wire"-handler which produces the red light. And sometimes when you pull the jack out again, it stays.

Fully inserting the jack and removing it should do the trick. Repeat a couple times if necessary, try it slower, or faster. Maybe twist a little... Okay maybe I'm describing a different insert-remove-insert-remove activity here ;)

---

### Post by quickridge on 2010-06-09
> **linuxopjemac said:**
> digital audio port. You can disable the light with alsamixer, it's something with IEC958... I don't remember. mute it with "m". If you insist, I check it on my MacBook, I am working on my Pismo now.

maybe this will work too
```
amixer set IEC958 off
```
This worked for me on a macbook pro 3,1 running Lucid.

[QUOTE=funkwurm]
I have this happen under Mac OS X sometimes, if you put the jack not all the way in, a connection is made that triggers a "this must be an optical wire"-handler which produces the red light. And sometimes when you pull the jack out again, it stays.

Fully inserting the jack and removing it should do the trick. Repeat a couple times if necessary, try it slower, or faster. Maybe twist a little... Okay maybe I'm describing a different insert-remove-insert-remove activity here 
[/QUOTE]

Since the red light only appeared when running Ubuntu, not OS X, this did not appear to be the problem for my case (i.e. there was not some switch that become stuck within the headphone jack since the problem seems to be software related).

---

### Post by Zookalicious on 2010-08-13
Success on a 5,1 running 10.04. Thanks :)

---

### Post by Oliver Cardoso on 2010-09-29
> **linuxopjemac said:**
> 
```
amixer set IEC958 off
```
It works with 10.04 on MackBook 6,1

Thanks,

---

### Post by taryneast on 2010-10-01
I have a MacBook 5,2 and alsamixer worked for me.
The one to disable (with the 'm' key) was labelled:   S/PDIF

---

### Post by MattFinck21 on 2010-10-17
worked for me too! Macbook 2,1 Ubuntu 10.10

---

### Post by MisterGaribaldi on 2010-10-17
> **funkwurm said:**
> Fully inserting the jack and removing it should do the trick. Repeat a couple times if necessary, try it slower, or faster. Maybe twist a little... Okay maybe I'm describing a different insert-remove-insert-remove activity here ;)

No, *really?* :P

---

### Post by maffix on 2010-12-01
I'm on macbook pro 4,1 and ubuntu maverick but the solution:
> amixer set IEC958 off

does not fix the issue permanently!
Every time I started ubuntu red light comes up from my jack input!
Also:
```
# alsactl store
```
does not fix the problem.

Is there a solution for fix that permanently?

Thanks a lot for any advices;)

---

### Post by quickridge on 2010-12-01
> **maffix said:**
> I'm on macbook pro 4,1 and ubuntu maverick but the solution:


does not fix the issue permanently!
Every time I started ubuntu red light comes up from my jack input!
Also:
```
# alsactl store
```does not fix the problem.

Is there a solution for fix that permanently?

Thanks a lot for any advices;)

There's probably a better way, but I just added a script with that command to my start-up applications.

i.e.

turnOffLight.sh:
```

#!/bin/bash
amixer set IEC958 off                      

```And added the command 
"bash /yourPathToFile/turnOffLight.sh" 
to your start-up applications (found in System/Preferences). If someone has a better solution let me know.

---

### Post by maffix on 2010-12-01
> turnOffLight.sh:
Code:

```
#!/bin/bash
amixer set IEC958 off
```

And added the command
"bash /yourPathToFile/turnOffLight.sh"
to your start-up applications (found in System/Preferences). If someone has a better solution let me know. 

Thanks a lot quickridge :D!
It perfectly works.
I know that it would be a better way to solve this issue but for now is a smart solution.
It was very annoying to make that every time on starting ubuntu system.
Good luck for you!
Bye.

---

### Post by Zookalicious on 2010-12-08
The non-restoring on start-up seems to be related to Ubuntu overriding the stored alsa settings at login, although I have no idea how that happens. I'm gonna keep looking into it but for now, running the brief startup script as suggested by quickridge is probably the simplest solution. If I ever figure out how to fix this in a more traditional manner I'll post it here.

---

### Post by yugnip on 2010-12-18
> **quickridge said:**
> There's probably a better way, but I just added a script with that command to my start-up applications.

i.e.

turnOffLight.sh:
```

#!/bin/bash
amixer set IEC958 off                      

```And added the command 
"bash /yourPathToFile/turnOffLight.sh" 
to your start-up applications (found in System/Preferences). If someone has a better solution let me know.

This works perfectly on my Macbook Pro 3,1. Thanks so much.

---

### Post by mgoodwin6 on 2011-01-22
I have this issue right now.  I wonder if it has something to do with the fact that I get no sound out of the headphone jack.  Only sound on computer is through regular speakers.  CPU is Macbook 2007 model 2.0ghz C2D 1.5gb RAM.  Please help

---

### Post by roysatx on 2011-11-07
amixer set IEC958 off

Worked on my Macbook7,1  -   and glad of it too!!

---

### Post by WonderWoofy on 2012-04-06
I just want to mention that this also worked for me as well with 11.10 on my MacBook 2,1

---

### Post by valroadie on 2012-10-07
Macbook 2.1, ubuntu 11.10 was having problem with no sound through the headphone jack, this worked thank you!

---

### Post by will1982 on 2012-10-08
I think strange red lights are cool.

---

### Post by techabyte on 2012-10-09
Works on 12.04, Would like it to be perm without running scripts....

---

