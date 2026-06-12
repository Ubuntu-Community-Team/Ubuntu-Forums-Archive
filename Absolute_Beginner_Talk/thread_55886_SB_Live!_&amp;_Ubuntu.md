---
title: "SB Live! &amp; Ubuntu"
date: 2005-08-10
forum: Absolute Beginner Talk
---

### Post by grofaz on 2005-08-10
I did a forum search regarding configuring Sound Blaster Live 24 bit cards to work with Hoary but I'm a little green around the edges. Can anyone please explain to me how sound works in Ubuntu ? Why doesn't my Sound Blaster live get configured automatically at Ubuntu installation ? How do I manually configure it ? What is Alsa, OSS, and ESD. What's the difference between them ? Appreciate some guidence, thanks!

---

### Post by pmjdebruijn on 2005-08-10
Hi,

Well, a SoundBlaster Live! 24bit is not a SoundBlaster Live! at all... 

Take a look here:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410%2C+P17&module=ca0106](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410%2C+P17&module=ca0106) 

Try 'sudo modprobe snd-ca0106' and see if it works then...

Regards,
Pascal de Bruijn

---

### Post by poofyhairguy on 2005-08-10
[QUOTE=grofaz]I did a forum search regarding configuring Sound Blaster Live 24 bit cards to work with Hoary but I'm a little green around the edges. Can anyone please explain to me how sound works in Ubuntu ? Why doesn't my Sound Blaster live get configured automatically at Ubuntu installation ? How do I manually configure it ? What is Alsa, OSS, and ESD. What's the difference between them ? Appreciate some guidence, thanks![/QUOTE]

Read this link:

[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)

It should answer most of your questions. Ask what it doesn't answer.

---

### Post by grofaz on 2005-08-10
Actually I'm not sure I have the 24 bit version, I think it's just plain Sound Blaster Live!. Is there a way to check in ubuntu ? I really HATE booting up windows if I can help it. :)

All this OSS, ALSA etc. has me totally confused. So does the info above. Are you guys saying I need to compile my kernel to configure my soundcard properly or what? I don't seem to have any sound issues, was just curious if my card was being used or not. Then again I only have about 88% hearing in my left ear and 0% in my right. Still I love my sound effects!

I'll do some MORE reading but friendly advice is always welcome. Linux is an education not an O/S. I love it!

---

### Post by grofaz on 2005-08-11
OK, so I'm assuming I'm not using my SB card at the moment but that my default sink output is set on ESD and my default source is set on OSS. When I punch the TEST button sink beeps, but when I punch the source test button nada. Is that normal ?

Now reviewing the link in the first reply post above, I'm totally lost. Everytime I try something like that I end up reinstalling ubuntu again. I'd rather not do that! So is that info up to date ?

---

### Post by poofyhairguy on 2005-08-11
[QUOTE=grofaz]OK, so I'm assuming I'm not using my SB card at the moment but that my default sink output is set on ESD and my default source is set on OSS. When I punch the TEST button sink beeps, but when I punch the source test button nada. Is that normal ?

Now reviewing the link in the first reply post above, I'm totally lost. Everytime I try something like that I end up reinstalling ubuntu again. I'd rather not do that! So is that info up to date ?[/QUOTE]

I posted that to explain the different parts. Do you have onboard audio with your motherboard?

---

### Post by grofaz on 2005-08-11
I was scanning through my Device Manager and my SB Live card is EMU10K1. I must have some sort of integrated sound device but where do I look to see exactly what I do have ? I don't see it listed.

---

### Post by pmjdebruijn on 2005-08-15
Please excute 'lspci' on a terminal and paste it in here... then we'll see...

But it's very weird an emu10k1 isn't detect, it works fine for me. It may also be the case that both sound cards are detected, and that your onboard sound card is used as the primary sound card, which effectively makes your soundblaster idle...

Regards,
Pascal de Bruijn

---

