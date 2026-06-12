---
title: "How to rip shoutcast radio?"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by orange2k on 2007-06-13
Allright Im listening to shoutcast stations in AmaroK, and sometimes I like what I hear and I want to record it and burn in to a CD. Is there a way to do that?

---

### Post by arunkv on 2007-06-13
[StreamRipper]("http://streamripper.sourceforge.net/") allows one to rip Shoutcast streams. There's also a GUI front-end called KStreamRipper. Both can be installed using apt-get or aptitude.

---

### Post by ccfjeff on 2007-06-13
> **orange2k said:**
> Allright Im listening to shoutcast stations in AmaroK, and sometimes I like what I hear and I want to record it and burn in to a CD. Is there a way to do that?

I've also used the Windows version of [Audacity]("http://sourceforge.net/softwaremap/trove_list.php?form_cat=113") and really liked it.  You can also edit the sound files and save it in different formats.

---

### Post by orange2k on 2007-06-13
Is there some kind of additional repository I need to add? It doesn`t seem to be working...
I tried: sudo apt-get streamripper and sudo apt-get kstreamripper - no success...

Audacity you say? How do I rip a shoutcast stream with Audacity? Step by step please...

---

### Post by ccfjeff on 2007-06-13
> **orange2k said:**
> Is there some kind of additional repository I need to add? It doesn`t seem to be working...
I tried: sudo apt-get streamripper and sudo apt-get kstreamripper - no success...

Audacity you say? How do I rip a shoutcast stream with Audacity? Step by step please...

I have just been able to click on the red "record" button when I am listening to anything online.  

There is a drop down menu for the input source and I have mine set to "stereo mixer".

I do recommend "saving" the file before starting to record if possible, however.  I first used it to record college basketball games and I had it crash a couple of times after it had recorded for a long time.  It may have been I didn't have enough memory to store the temporary files, however.  I didn't have those problems when I had already saved it as it stores the incoming files as they come in and the temporary buffer or whatever is used is smaller.

Saving it before hand may not be an issue for you, however, if you are only ripping a song or two at a time.  I think I had an hour or more recorded before it would crash.  They do have a utility, by the way, to recover the audio from files still in the temporary folder.

---

### Post by ccfjeff on 2007-06-13
Here is a link to a copy of a Q&A session from an online radio broadcast that I exported as an mp3:

[www.esnips.com/doc/3549d57e-921a-4389-9d16-29db07b889bc/QA.re.interview.re.new.job]("http://www.esnips.com/doc/3549d57e-921a-4389-9d16-29db07b889bc/QA.re.interview.re.new.job")

You can play around with different sampling rates etc. but sound quality isn't much of an issue for talk radio.

---

### Post by orange2k on 2007-06-13
Audacity doesn`t work for me...
It doesn`t record anything, and Ive tried setting all available record sources...
Still doesnt work...
Thanks for trying though...

---

### Post by orange2k on 2007-06-13
ALLRIGHT, i figured out how to rip shoutcast streams!!!
All I had to do was choose "file" as output in Amarok...
Now it works - it saves my streams - I only cannot listen to it while it rips...:(

---

### Post by ccfjeff on 2007-06-13
> **orange2k said:**
> ALLRIGHT, i figured out how to rip shoutcast streams!!!
All I had to do was choose "file" as output in Amarok...
Now it works - it saves my streams - I only cannot listen to it while it rips...:(

Glad you figured out a way to rip it.

I am able to listen to Audacity as it records off of the sound card, however.  I may not have given an accurate description of my setup so I took a picture of the screen as I don't know how to do printscreens or whatever in Windows.  If interested, see the attachment below.

One possibility might be the sliders for the microphone or volume.  I had moved one of them one time to a lower setting and it took me awhile to figure out why my sound didn't work on my computer anymore.

The version of Audacity that I am using, by the way is 1.2.5  Their 1.3.X beta version had some nice new features but did not work for me on occasion.

Anyway, at least you have some method of saving those sound files.

---

### Post by orange2k on 2007-06-13
As I see it in the picture, youre recording it in windows...
I was wondering about linux...
No problem....btw is that rebirth on your screen?
I like Rebirth, I wish it would work on linux...

---

### Post by ccfjeff on 2007-06-13
> **orange2k said:**
> As I see it in the picture, youre recording it in windows...
I was wondering about linux...
No problem....btw is that rebirth on your screen?
I like Rebirth, I wish it would work on linux...

I haven't set up my Ubuntu yet, though I hope to soon.

I'm not familiar with rebirth.

I am listening to the Shoutcast on that digital camera pic with Winamp and recording it in Audacity.

I was assuming that the Linux version of Audacity would do the same thing while listening to any player.  I'm sorry it isn't working for you.

---

### Post by ravimannan2002 on 2007-08-30
I use exaile to listen to music and streamripper to rip shoutcast streams. You can get both from the synaptic package manager. Once they are both installed, exaile automatically recognizes streamripper, you have to enable it in exaile using Tools>Plugins. After that, you should see a red record button near the controls.

hope this helps

---

