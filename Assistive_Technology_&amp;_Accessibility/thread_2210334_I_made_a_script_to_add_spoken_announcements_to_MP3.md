---
title: "I made a script to add spoken announcements to MP3s files for blind/VI people"
date: 2014-03-10
forum: Assistive Technology &amp; Accessibility
---

### Post by aoakley on 2014-03-10
Hi, I've created a Perl script to automate the adding of speech-synthesis spoken announcements to the start of MP3s files.

Scenario: Visually impaired / partially sighted father waiting for cataracts operation; wants to listen to radio plays / radio comedies; has hi-fi / music player with USB MP3 support; cannot read the display; cannot easily navigate through a long list of files.

Solution: my script: [http://aoakley.com/misc/annmp3.txt](http://aoakley.com/misc/annmp3.txt) (change .txt to .pl)

This adds a short speech-synthesis announcement to the start of each MP3 file, announcing track number, series name, episode number and episode name. Currently it takes metadata from the filename, but if there's enough interest I could improve the script to take metadata from the ID3 tags. For example, dad likes spy thrillers, and I have my home recordings of BBC Radio 4's John le Caré radio plays sitting around, so if the file is named:

001 Complete Smiley e01 A Call for the Dead.mp3

...then it adds the spoken phrase "One, Complete Smiley, episode one, A Call for the Dead" to the start of the track.

In making this script, I had to solve a number of non-trivial problems, not least of which is how to add to an existing MP3 file *without* losing quality through decoding and re-encoding. Many radio plays, being very long, are archived at low bitrates and low frequency ranges, such as 92kbps at 32kHz rather than the more common 160 or 320kbps at 44.1kHz - there are even super-low bitrate libraries of very old mono radio plays such as The Goon Show at 24 or 32kbps, 20 or 24kHz - so decoding and re-encoding them is particularly prone to quality loss and extremely noticeable audio artefacts, especially the spoken word (mobile-phone like garbling and noise around "S" sounds, for starters). Decoding and re-encoding also uses considerable CPU power, whereas working directly with MP3 frames is doable on even a Raspberry Pi.

You can use mp3cut to concatenate two MP3 files with identical bitrate, frequency range and stereo mode, but finding the frequency information reliably is non-trivial (the "file" utility doesn't always work and mp3info doesn't output frequency range by default). If you try to concatenate two MP3 files with identical bitrates but different frequency ranges, it fails. Two MP3 files with identical bitrates but one mono (espeak speech synthesis outputs mono by default) and one stereo, it fails. It took me quite a while before digging through the mp3info documentation to discover I could get it to report the frequency range.

I am now wondering if anyone else might have a use for this script. If so, I will invest some time in improving it to add, for example:

* Use of getopts to process extended command line arguments
* Option to get album/artist/title/track information from ID3 tags rather than just the filename
* Option to add a year (e.g. for very large archives such as "The Goon Show" or "Just a Minute")
* Option to change the speech synthesis engine easily (reading through a few other visually impaired Linux user reports, neither espeak nor festival are apparently not top choices, with many VI users preferring to use a commercial speech synthesiser).
* Option to change the order of the announcement (e.g. track name first rather than track number)
* Packaging it into a .deb and putting it up on a ppa or similar to make it easier to install properly

---

### Post by Jonor on 2014-03-10
I have sometimes thought how useful it could be to get MP3 metadata in audio 
when doing things that would have to be interrupted to read the player display.
For instance the player is under my hat when out jogging so the routine now would be to stop jogging, 
remove cap and player wrapper (protects player from wet/salt),
put strong spectacles on to see tiny display, carefully reassemble player and earphone cables atop noggin, 
catch up with the five runners who have since passed me.
Although music streaming is becoming popular there should still be a lot of people with burgeoning 
MP3 collections who would find this an enjoyable way to learn all the new names.

---

### Post by aoakley on 2014-03-11
Yeah, I must admit that I (fully sighted other than heavy colour-blindness) found it a lot easier to navigate my own MP3 player after filling it with these announced files.

I may try it in the car with regular music - maybe just the first track of each MP3 album folder. Who knows, it could prevent crashes.

---

