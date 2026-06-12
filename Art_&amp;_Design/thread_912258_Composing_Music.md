---
title: "Composing Music"
date: 2008-09-06
forum: Art &amp; Design
---

### Post by jfhutton on 2008-09-06
My wife is a choir director and is looking to do some music notation.  While I have done a little poking around, Muse Score and NoteEdit didn't seem to be very intuitive to use.  Have some more things to try, but I thought I would test this forum.

There are several how-tos on doing acutal audio composition in Ubuntu (Ubuntu Studio, etc), but this is not quite what I'm looking for.

What I would like:
- Music Notation software which supports
  - 4-6 staff composition (SATB + right-left hand piano)
- Simple note entry
- Future input through MIDI keyboard
- Finished printing capability

While I'm starting to think that we could try to do audio entry into something like Rosegarten for piano and all of the voices and then see if that would be able to give me actual sheet music (she makes learning CDs for her choirs as well, so it wouldn't be wasted work), that is not where I'm hoping to go today.

Any ideas?

---

### Post by lyceum on 2008-09-06
RoseGarden?

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

---

### Post by V for Vincent on 2008-09-06
Yeah, I think rosegarden is what you're looking for.

---

### Post by MadsRH on 2008-09-06
I've been using an older version of Finale, witch runs just fine under Wine.

I love open source, but I can't live without Photoshop, M$ Word2007 and Finale ;-)

[B]
//MadsRH[/B]

---

### Post by smartboyathome on 2008-09-06
Check [here]("http://en.wikipedia.org/wiki/List_of_scorewriters") for a list of what I think you are looking for (scorewriters). Personally, I think Denemo looks like the easiest to use.

---

### Post by UbuWu on 2008-09-08
NtEd is very nice and new features keep getting added all the time, I think it supports most features you mentioned. It is in the ubuntu repositories but a more up to date version is available from the website at [http://vsr.informatik.tu-chemnitz.de/staff/jan/nted/nted.xhtml](http://vsr.informatik.tu-chemnitz.de/staff/jan/nted/nted.xhtml) (look for the debian package)

---

### Post by loell on 2008-09-08
I have the latest Nted in my [PPA]("https://launchpad.net/~loell/+archive"), :)

or you can just install this package ( for hardy heron)

[http://launchpadlibrarian.net/17041344/nted_1.0.6-1%7Ehardy1_i386.deb]("http://launchpadlibrarian.net/17041344/nted_1.0.6-1%7Ehardy1_i386.deb")

---

### Post by UbuWu on 2008-09-08
> **jfhutton said:**
> 
What I would like:
- Music Notation software which supports
  - 4-6 staff composition (SATB + right-left hand piano)
- Simple note entry
- Future input through MIDI keyboard
- Finished printing capability


For nted, currently 4-6 staff composition is no problem. Note entry is as simple as it could be, point and click. Midi input is planned but not yet implemented. Printing is possible although it is very basic, probably better to export to lilypond and print from that.

---

### Post by matdombrock on 2008-09-09
You might get better answers in the Multimedia forum, but i would recommend Rosegarden.

---

### Post by Bucky Ball on 2008-09-09
[quote=MadsRH]I love open source, but I can't live without Photoshop, M$ Word2007 and Finale[/quote]

Try The Gimp (Photoshop), OpenOffice (MSWord). Different GUI but that is about it.

Very experienced with music notation software (currently doing a bachelor of music and writing for orchestra, but have been composing and using music notation software for years) and I hate to say this but ... Sibelius is unbeatable and the only thing I use my Windoze boot for. Doesn't run well under wine and Sibelius 5 not at all. Nothing open source comes close. :(

If you don't require playback of instruments or voice (one thing the open source community lacks - at this point - is some serious and complete soundfonts), Muse Score is as good as it gets. Rosegarden is actually for recording (Linux equivalent to ProTools, Cubase etc) and incorporates Lilypond, the music notation component. Rosegarden per se is not a music notation editor. And like its Windoze counterparts, the notation component is not quite up to it (IMHO).

But having said all that, you might find something that fits the bill for you. You could always run windoze virtually from within Linux.

:)

---

### Post by MadsRH on 2008-09-09
> **Bucky Ball said:**
> Try The Gimp (Photoshop), OpenOffice (MSWord). Different GUI but that is about it.

You said it yourself - "Nothing open source comes close."


[B]
//MadsRH[/B]

---

### Post by smartboyathome on 2008-10-01
> **loell said:**
> I have the latest Nted in my [PPA]("https://launchpad.net/~loell/+archive"), :)

or you can just install this package ( for hardy heron)

[http://launchpadlibrarian.net/17041344/nted_1.0.6-1%7Ehardy1_i386.deb]("http://launchpadlibrarian.net/17041344/nted_1.0.6-1%7Ehardy1_i386.deb")

Loell, can you get NtEd 1.3.0 in your PPA? That'd be great. :)

Smartboy

---

### Post by loell on 2008-10-01
> **smartboyathome said:**
> Loell, can you get NtEd 1.3.0 in your PPA? That'd be great. :)

Smartboy

done. :)

---

### Post by Crafty Kisses on 2008-10-02
I've heard RoseGarden is pretty solid, I'm not sure but Audacity might be good too if you want to edit music and what not.

---

### Post by smartboyathome on 2008-10-02
> **loell said:**
> done. :)

Fantastic! Thanks loell! :D

---

### Post by UbuWu on 2008-10-02
> **loell said:**
> done. :)

Thanks (btw. version name is wrong: 1.0.30 instead of 1.3.0)

Oh and 1.3.1 is out ;-)

---

### Post by loell on 2008-10-02
> **UbuWu said:**
> Thanks (btw. version name is wrong: 1.0.30 instead of 1.3.0)

Oh and 1.3.1 is out ;-)

uploaded and version bump corrected. ;)

---

### Post by Bucky Ball on 2008-10-03
Loell, I installed Nted to try it out and couldn't find it anywhere, including the terminal. What am I missing? Is it just called 'nted'?

* Update: Don't bother, found it! Just having a look. :)

---

### Post by mondoUNC on 2008-10-06
I've found Rosegarden to work well for most of my composing needs, Its easy to edit music as a score, but you can also edit your notation as midi.

---

### Post by smartboyathome on 2008-10-16
Well, loell, NtEd 1.4.1 is out! Now I can change the scale so that if I want my music to be on one sheet, it can be! :D

I also have a problem with your NtEd debs. I can't get my music to play on Ubuntu from inside NtEd. I have to export it as a midi and then play it in Totem to get it to work.

---

### Post by loell on 2008-10-17
> **smartboyathome said:**
> Well, loell, NtEd 1.4.1 is out! Now I can change the scale so that if I want my music to be on one sheet, it can be! :D

I also have a problem with your NtEd debs. I can't get my music to play on Ubuntu from inside NtEd. I have to export it as a midi and then play it in Totem to get it to work.

updated to 1.4.1 :)

have you check timidity configuration? since that will mostly be the sound backend for nted.

---

### Post by smartboyathome on 2008-10-17
I got NtEd to play now loell. It seems that NtEd is dependant on Timidity to play, which in turn needs jack up in order to output any sound. After installing jack and configuring it according to [this howto]("http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/") (which works on a standard Ubuntu), with just a change to the Frames/Period from 128 to 512 so that there wasn't any flickering, and then starting up timidity with this command using GNOME's run dialog (starting it in a terminal renders that terminal useless because it never ends, even with an & at the end of the command):
```
timidity -iA -B2,8 -Oj -s 44100
```
I can get music to play with aplaymidi with the first port it outputs (for me it is 128:0). To get NtEd to work, just open it up, go to configure > configure midi, and then select the port on which aplaymidi was able to play.

---

### Post by ace214 on 2008-10-17
I've actually contemplated learning Lilypond because of the lack of notation editors that I liked.

Two advantages I see to this:
1) Platform independent, software independent: If I'm working on any machine with a text editor, I can work on the score. I may not be able to see it until I can use the program, but at least I can input notes
2) May be faster: I can type a c''4 a lot faster than I can scroll to that C and use whatever number a quarter note is. That is *if* the program has keyboard entry and isn't just mouse.

The only problem is, I don't really have the time during the school year to learn it...

ADD: You know what would be wonderful? An online Lilypond converter. Upload your .ly file and download the pdf... Like that mediaconvert website.

---

