---
title: "control a computer with a piano"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by 900donuts on 2007-06-11
I've been think recently about funny ways to control a computer and i thought is it possible to control a computer by hitting keys on a piano the same way you would use voice commands if so.

1.what software do i use?

2.how do i make this work?

3.and what problems would i encounter?

p.s. just a thought i just realized that I'm trying to make possibly the worlds heaviest wireless keyboard :lolflag:

---

### Post by rich.bradshaw on 2007-06-11
Can't help, but I can point out that you are completely insane!

Midi keyboard would be easier....

---

### Post by Soybean on 2007-06-11
That's a great idea! I think it would be especially useful if you also had a computer-controlled secret passage, so that playing a particular tune on your piano would open the secret door. :D

Anyway, I've never heard of such a thing before, so I'm not aware of any existing software solution. It doesn't seem like it *ought* to be all that hard to implement, though. Piano notes have known frequencies, so you'd just need to be able to read microphone input and answer the question, "is the current sound approximately equal to one of the following frequencies?"

---

### Post by forestpixie on 2007-06-11
That'd be an experiment - especially when the piano went out of tune! Middle C today starts oo - next week it could start firefox.

:D

---

### Post by shen-an-doah on 2007-06-11
If you wanted a properly sophisticated way of doing it using a real piano, you'd have to have a system of (probably) piezo pick-ups, one on each string, like what's used in the Line 6 [Variax](http://en.wikipedia.org/wiki/Variax). This could created MIDI information about each string. A simpler method would be just to use a normal MIDI keyboard.

You could then send this MIDI information to [Pd](http://en.wikipedia.org/wiki/Pure_Data) and do whatever you like with it...

---

### Post by jgrabham on 2007-06-11
Wire up the hammer on one side, and wire up the strings; when you hit a key, it will create a full circuit and be able to do something.

---

### Post by locke.dragon on 2007-06-11
lol!  first, why would you want to do something like this?  second, the midi keyboard idea is your best bet.  as forestpixie pointed out, the tuning would be hideous on a normal piano (especially if you're like me and don't tune your piano more than one every few years).  with a midi keyboard, you wouldn't even need to have the notes be "heard" by the computer, you could just have it read which notes are being pressed.  

i'm definitely gonna follow this project!

---

### Post by lazyart on 2007-06-11
> **forestpixie said:**
> That'd be an experiment - especially when the piano went out of tune! Middle C today starts oo - next week it could start firefox.

:D
LMAO.  It gets better when you're running Exaile/AmaraoK/insert-music-player-here and apps start opening and closing at random.

---

### Post by p_quarles on 2007-06-11
I say we should up the ante here: get the computer to control the piano, then hack a Wii remote so that you can "conduct" the piano. :)

---

### Post by 900donuts on 2007-06-11
my house has a midi keyboard but its in the back the big "analog" piano is practically in the same room

as for tuning if it helps the piano is already out of tune and I'm looking to calibrate my computer to respond to its noise the say way one would calibrate a computer to respond to one's voice

---

### Post by iceportal on 2007-06-11
> **Soybean said:**
> That's a great idea! I think it would be especially useful if you also had a computer-controlled secret passage, so that playing a particular tune on your piano would open the secret door. :D

Like Willy Wonka playing Wolfgang Amadeus Mozart's Overture to the Marriage of Figaro to open the door to his magical candy planet...

(She said it was Rachmaninov, but she was mistaken.)

> **p_quarles said:**
> I say we should up the ante here: get the computer to control the piano, then hack a Wii remote so that you can "conduct" the piano. :)

Brilliant. Simply brilliant.

---

### Post by ncappel1 on 2007-06-11
It would be very difficult, and you would probably have to use a midi keyboard, because even on a real piano (and any intrument, really) individual notes do not resonate at isolated frequencies. Notes and sounds will resonate most strongly at the pitch played, but will continue vibrating at each node in the harmonic series. A midi keyboard would be a way around this, as each key depression is not a frequency, but an electrical signal. 

Be advised that the most annoying problem you would encounter would be after everything works, at which point forum threads, news articles, and conversations would start arguing about wether or not your system were "ready for the desktop," and how "only people who specialize in the field of piano playing can operate that system, what about us average joes who can't tell the white keys from the black?"

---

### Post by 504harry on 2007-06-11
> **900donuts said:**
> I've been think recently about funny ways to control a computer and i thought is it possible to control a computer by hitting keys on a piano the same way you would use voice commands if so.

1.what software do i use?

2.how do i make this work?

3.and what problems would i encounter?

p.s. just a thought i just realized that I'm trying to make possibly the worlds heaviest wireless keyboard :lolflag:

900Dougnuts, ...have you read these replies ? .....and does any come near what you want?....I get the impression you wnt to use a  real Pianoforte...but can't understand why. It might be possible to pick-up the frequency of the note  - but the poster who suggestwedd something using piezo is way-off IMHO since a piano has rich overtones - so sooner or late rthe who thing would be firing off. Individual magnetic pick-ups ( like Guitar) would be more sense...but  whoah! isn't this getting silly - WHY..?

A MIDI keyboard "might" be a lot easier,...but you need to provide some feedback, otherwise this sounds like..... a dead thread...

---

### Post by shen-an-doah on 2007-06-11
> **504harry said:**
> the poster who suggestwedd something using piezo is way-off IMHO since a piano has rich overtones - so sooner or late rthe who thing would be firing off. Individual magnetic pick-ups ( like Guitar) would be more sense...

Actually, that's what I suggested, just take a look at how the Line 6 Variax works: [http://en.wikipedia.org/wiki/Variax](http://en.wikipedia.org/wiki/Variax)

---

### Post by 900donuts on 2007-06-11
and why can't i just use a voice control program?

try saying the same thing twice and making it sound the same to the computer

 is any one getting my point?

---

### Post by Soybean on 2007-06-11
I don't know how well a voice recognition program is going to work with a piano... I think that if you try that, though, you might have more luck with short tunes than with single notes. I've noticed that a lot of modern voice recognition software works best with words with a different number of syllables, or stress on different syllables. So I'd think that your best bet would be to make your piano "commands" have the same properties as good voice command words.

---

### Post by 900donuts on 2007-06-12
now we're geting somewhere

 so if i use a set of notes like "bing" "bang" "bong" it would be like saying "op" "en" "game"(sorta?)

ok then what voice reconition software is out there? because i don't know of any

---

### Post by tdrusk on 2007-06-12
I think it could actually work. Run the output from an  electric keyboard into your line in or mic in. Then assign voice recognition to each note.

middle c opens firefox, etc.

[http://www.linux.com/howtos/Speech-Recognition-HOWTO/software.shtml](http://www.linux.com/howtos/Speech-Recognition-HOWTO/software.shtml)

---

### Post by 900donuts on 2007-06-12
why do peple keep on sujesting i use a electric keyboard i know its easier but it seems to easy to me

any ways kvoicecontrol looks like the best bet i'll be able to get started tomarrow but don't stop keep the sujestions coming :D

---

### Post by Shazaam on 2007-06-12
Piano>microphone>audio to midi converter> midi to pc(midi or usb)> software to convert midi note-on/note-off.

---

### Post by 900donuts on 2007-06-12
a few questions whats a midi converter?

how much does it cost?

and why can't i just use the raw noise coming from the piano???

---

### Post by tdrusk on 2007-06-12
> **900donuts said:**
> why do peple keep on sujesting i use a electric keyboard i know its easier but it seems to easy to me

any ways kvoicecontrol looks like the best bet i'll be able to get started tomarrow but don't stop keep the sujestions coming :D

With a microphone method background noises could become a problem.

---

### Post by CrispyFried on 2007-06-12
rather than speech recognition, a spectrum analyzer may work better but I dont know if any that will output text or data files (instead of displaying on the monitor) exist. it would be able to pick out notes better and also be able to better ignore harmonics. you may not be able to get every key to read different but you should be able to get 15-20 or so with a 1/3 octave analyzer.

it would pick up notes next to each other as the same, ie b, c, and d would read about the same. it would also be pretty forgiving of the piano tune drifting.

---

### Post by CrispyFried on 2007-06-12
> **fuzzyhair said:**
> With a microphone method background noises could become a problem.

depends on the mic, some are very near field and ignore anything off axis. with a mixer and several mics (sure sm-58s maybe) you would only pick up the piano notes and nothing else of importance unless a jet happens to fly 100 feet over your piano.

---

### Post by 900donuts on 2007-06-12
i saw some thing on on makezine.com once

some guys where drawing a spiral on a computer using some acustic sensors and a piece of cardboard the article that was talking about it sujested that it could be done in keyboard form useing one sensor and teaching the computer to reconize some one taping the card board in diferent places

but im trying to do this with out buying anything and with out cables conected to the piano

---

### Post by tdrusk on 2007-06-12
> **CrispyFried said:**
> depends on the mic, some are very near field and ignore anything off axis. with a mixer and several mics (sure sm-58s maybe) you would only pick up the piano notes and nothing else of importance unless a jet happens to fly 100 feet over your piano.

Well if I was him I would at least control it with a keyboard first to make sure everything works fine, then I would make it more complicated.

---

### Post by 900donuts on 2007-06-13
Googleing voice recognition for linux every thing seems to be 7 years old can someone tell me the most developed or popular software available ???

---

### Post by TheOtherShoe on 2007-06-25
Here you go:
[http://www-128.ibm.com/developerworks/library/os-whistle/index.html?ca=dgr-lnxw97whistlework](http://www-128.ibm.com/developerworks/library/os-whistle/index.html?ca=dgr-lnxw97whistlework)

That tutorial is for setting up whistle-control; but I'm guessing it would work even better with a piano.

---

