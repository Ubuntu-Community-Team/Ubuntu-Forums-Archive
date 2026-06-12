---
title: "How can I stop Skype making crackling noises?"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by gummylindz on 2006-05-02
Please help... I'm a new Ubuntu user and after being pampered by Windows, it's quite a new experience. I'm having a few problems... including this Skype one.

When I make a call on Skype, it's fine for about a minute, and then it starts making these horrid crackling noises that don't let me hear the other person on the line. They get more frequent and longer each time. It never happened on Windows. I've tried restarting the program and also reinstalling it but it doesn't work...

:confused:

---

### Post by gummylindz on 2006-05-02
OY YOU!! 

I just posted something against your post in another thread........

I start threads on here to get help, not for some random person to do publicity of something....... this is a help forum and it's not fair cus nobody's helping me!!!!!!!!!!!!!!!!!!!!!

---

### Post by gummylindz on 2006-05-02
please help with my problem, both now actually, 1. skype and 2. this annoying person

---

### Post by Kimm on 2006-05-02
gummylindz, I'm pretty sure that was a Forum bot, its spam and its very uncommon on these forums, I'm sure someone will take care of it.

Anyway, on your issue, I get something similar, although it starts right away...
open a terminal and type:

alsamixer

go to the side and look for "Mic Boost" (might just say "Mic Boos"), if it sais MM under the bar, then your good, then go to the bar next to that one and make sure Mic is as far up as it goes. This reduses the crackling noises for me, my Mic volume goes down but its barable.
If it doesnt work, you can allways change the settings back.

Edit:
on the Spam dude, he sure was extremely annoying, I'm reporting it on IRC now...

---

### Post by gummylindz on 2006-05-02
but surely that'll just reduce the noise like you say........ the problem is, the crackling doesnt let me hear the other person, and so its extremely annoying because it just stops the conversations.... i'll try what you said though, thanks :)

and i sure hope that guy got chucked or something :mad:

---

### Post by gummylindz on 2006-05-02
i tried what you said, and i get the weirdest screen...... something like this:

[AlsaMixer v1.0.10 (Press Escape to quit)]
Card: ATI IXP Modem
Chip: Conexant id 30
View: [Playback] Capture  All
Item: Caller ID [Off]  

And then, down the bottom:

      MM                                        MM
<Caller 1>                            <Off hook>

:confused: im very muddled up now.....

---

### Post by gummylindz on 2006-05-02
[QUOTE=gummylindz]
      MM                                        MM
<Caller 1>                            <Off hook>[/QUOTE]

that's meanta be, MM and underneath <Caller 1>, and then further along MM anbd underneath <Off hook>

---

### Post by gummylindz on 2006-05-02
heeeeeeeeeeeeeeeeeeeeeeeeelp

---

### Post by cornellfinch on 2006-05-02
Just a question:  Is it always with the same person at the other end?  Could the problem be their end?

---

### Post by gummylindz on 2006-05-02
hmmm..... maybe you're right, because it is always the same person....

but the thing is, the problems only started when i began with ubuntu, about a month ago, and it had happened before on windows but the solution was to uninstall/reinstall skype. i tried that on linux and no luck.....

it's the only thing i have against ubuntu for the time being, but it bugs me a lot :(

---

### Post by physcsdrk on 2006-05-02
I have a question....(you'll be able to tell how new I am to linux with this one)  

How do you install skype?

---

### Post by gummylindz on 2006-05-02
ah well..... i believe if you search in the synaptic package manager (im that far :D) you'll find it....... (under system - administration), if not, go to [http://www.skype.com]("http://www.skype.com") and there, on downloads or something, there should be a linux button somewhere........ i believe i did it that way :)

---

### Post by Jason_25 on 2006-05-02
[QUOTE=physcsdrk]I have a question....(you'll be able to tell how new I am to linux with this one)  

How do you install skype?[/QUOTE]
If your on i386 ubuntu grab the skype deb.  If your on AMD64 ubuntu grab the static binary.

---

### Post by r4ik on 2006-05-02
And last but not least dont eat chips.

---

### Post by debernardis on 2006-07-14
The new skype version (1.3) does not crackle :p

---

