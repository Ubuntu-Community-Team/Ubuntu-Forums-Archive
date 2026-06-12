---
title: "perlbox"
date: 2008-03-11
forum: Assistive Technology &amp; Accessibility
---

### Post by djbsteart1 on 2008-03-11
I installed perbox on my system and I can now talk to it, a command like desktop-next switches to next desktop, desktop-firefox launches firefox, I feel that this is something that should be included in Ubuntu, the software is not perfect, but it does make using the computer very easy and adds new dimensions to the user experience at all levels, not to mention the cool factor.

---

### Post by designwiz on 2008-03-17
i must agree perlbox is one good app... im working on an interface for the visually impaired students 
Its a simple GUI with an audio interface by which updates, accessiblity feature etc can be accessed wit ease also installls the neccessary components
(installs perlbox, screen reader, scanner interface, magnifier, on screen keyboard!)

needed some help with emacpeak...

any ideas/suggestions would be greatly appreciated.. Thanks

---

### Post by djbsteart1 on 2008-04-09
Perlbox was one of those little gems that you stumble on, I can't help with anything other than recommending it. I can see why this program would be so useful for what you are doing. I would greatly appreciate updates on any progress that you make, as I live/work in a community that cares for people with mental/physical disabilities, and something like this would be very useful. 

Donald.

---

### Post by masterchief324@gmail.com on 2008-05-03
> **djbsteart1 said:**
> I installed perbox on my system and I can now talk to it, a command like desktop-next switches to next desktop, desktop-firefox launches firefox, I feel that this is something that should be included in Ubuntu, the software is not perfect, but it does make using the computer very easy and adds new dimensions to the user experience at all levels, not to mention the cool factor.

Hi guys,
My dad is dyslexic and he can't read or write. Where would I find said software?

---

### Post by djbsteart1 on 2008-08-12
[http://perlbox.org](http://perlbox.org), sorry for the lateness of the response, haven't used ubuntu in a long time.

Nice sig.

---

### Post by dchurch24 on 2008-08-21
Hi all,

I too am very insterested in Perlbox, but when I run the .deb file it tells me that I have the wrong architecture (which I do) - I am using Heron 64.

Is there a 64bit version available, or a way to run the 32bit version under 64bit OS?

---

### Post by djbsteart1 on 2008-08-23
I haven't got a clue if you can do this with ubuntu, but with Mandriva, you can install support for a 32bit system on a 64 bit system. 

Google will tell you.

---

### Post by Sef on 2008-08-23
> I haven't got a clue if you can do this with ubuntu, but with Mandriva, you can install support for a 32bit system on a 64 bit system.

That is possible to with Ubuntu.  Read [Cappy's thread]("http://ubuntuforums.org/showthread.php?t=474790").

---

### Post by djbsteart1 on 2008-08-28
Thanks Sef, will forget that now.

---

### Post by MaxVK on 2009-05-23
Sorry to resurrect an old thread, but has anyone actually managed to get this software to work? I ask because I'm talking myself into a sore throat trying to persuade the thing to recognize anything at all.

Iv had trouble on one machine with the mic, but on this machine the microphone, recording and playback is excellent and very clear, and yet Perlbox flatly refuses to recognize anything, and if it does it usually gets things totally wrong - for example recognizing the word "Mail" as "Home".

I read somewhere that you don't train this software, it trains you, but Iv not found any information on exactly how this might work!

Can anyone give me any tips on this please?

cheers

Max

---

### Post by Glaciusor on 2009-05-30
I'm not sure if this will help as I'm currently trying to get perlbox set up myself, but you need sphinx2 on your system as well, and I believe festival needs to be installed too but I am not sure. I hope this helps ^_^.

---

### Post by MaxVK on 2009-05-31
Yes, the instructions on the web site show that you need to have all three installed, and I have - it still doesn't work though and Iv given up trying unless someone comes up with something that Iv not tried.

In the meantime Iv been looking at [Julius]("http://julius.sourceforge.jp/en_index.php"); Information is there and Iv got this working, and working quite well at recognition in fact, but I'm now trying to pinpoint the reason for a delay between speaking and recognition.

cheers

Max

---

### Post by mofrikaantje on 2009-06-01
Hi MaxVK, I'm also using Perlbox-voice now, I set it up today and it works like a charm - when I speak REALLY clear, that is. Julius has a way better voice recognition system (follow the readme to test it yourself), just like gnome-voice-control has a more accurate system. Gnome-voice-control uses Pocketsphinx, the follow-up of Sphinx2, and I'm trying to get Perlbox to use the new Pocketsphinx (which I installed) in stead of Sphinx2. No succes, as I can't seem to locate the Pocketsphinx installation on my computer (Ubuntu 8.04). Does anyone know where it's installed? I know, it sounds noobish, but I really can't find it :(

---

### Post by mofrikaantje on 2009-06-01
> **MaxVK said:**
> I'm now trying to pinpoint the reason for a delay between speaking and recognition.
I thought that was due of the processing and can't be helped (for now)...? Correct me if I'm wrong, I'm also interested in knowing how to get it to work faster...

---

### Post by MaxVK on 2009-06-02
I went through the Gnome-Voice + Sphinx and then Pocketsphinx - Both compiled okay, but neither worked at all well, and if I remember correctly I had the same problem as you - Locating Pocketsphinx once it was installed.

As for speaking clearly: I never got Gnome-Voice to recognise a single word and I gave up on it pretty quick. Spinx and Perlbox were poor at best, which is why I tried Julius, however, the delay I'm talking about is not something that is normal:

During a test (as from the readme etc), it will recognised a word, but I have to wait for at least another 3-5 seconds for the (correctly) recognised voice to actually register.

As it is, with that delay, its useless. I posted a query on this behavior at the VoxForge forum ([Here]("http://www.voxforge.org/home/forums/message-boards/speech-recognition-engines/julius---time-taken-to-recognise-commands#jglel8hjkkJdofaff-chzQ")) but so far there has been no reply and I have currently given up on any kind of decent voice recognition/control.

If I find anything out Ill post again here to let you know, but Id suggest not holding my breath!

---

### Post by mofrikaantje on 2009-06-02
> **MaxVK said:**
> I went through the Gnome-Voice + Sphinx and then Pocketsphinx - Both compiled okay, but neither worked at all well, and if I remember correctly I had the same problem as you - Locating Pocketsphinx once it was installed.

As for speaking clearly: I never got Gnome-Voice to recognise a single word and I gave up on it pretty quick. Spinx and Perlbox were poor at best, which is why I tried Julius, however, the delay I'm talking about is not something that is normal:

During a test (as from the readme etc), it will recognised a word, but I have to wait for at least another 3-5 seconds for the (correctly) recognised voice to actually register.

As it is, with that delay, its useless. I posted a query on this behavior at the VoxForge forum ([Here]("http://www.voxforge.org/home/forums/message-boards/speech-recognition-engines/julius---time-taken-to-recognise-commands#jglel8hjkkJdofaff-chzQ")) but so far there has been no reply and I have currently given up on any kind of decent voice recognition/control.

If I find anything out Ill post again here to let you know, but Id suggest not holding my breath!

Aha, well with Julius I'm not having that problem, sometimes it even responds *too* quick - but it still recognizes commands way better than perlbox-voice. Gvc wasn't very succesful with me either: it recognised most of the commands, but the functionality is too limited for me - and changing the source and then compiling keeps giving me errors.
As for the Pocketsphinx issue: apparently, it's derived from Sphinx3 and not Sphinx2, so you can't just switch Sphinx2 for Pocketsphinx.. :( The installation directory of Pocketsphinx btw: /usr/local/share. I guess I'll have to learn C or Perl now if I want something changed on Perlbox-voice, or having commands being executed with Julius..
For the sake of demonstration, I posted a screencast of perlbox-voice on YouTube: [http://www.youtube.com/watch?v=1Q7lEXYqUyk](http://www.youtube.com/watch?v=1Q7lEXYqUyk)

---

