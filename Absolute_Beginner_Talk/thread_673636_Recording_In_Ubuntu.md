---
title: "Recording In Ubuntu"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by anderskitson on 2008-01-20
I have recently got midi working where I can record off my keyboard in rosegarden. I also have been making some beats in Hydrogen. I would like to mix the two, but play the keyboard on the fly with the drums playing. I have tried importing Hydrogen files into rosegarden, via midi, rosegarden file and wav, and nothing sounds how it should and wave doesn't work.

Update: If your not sure what i can do, does anyone know how to get a midi file otu fo rosegarden in any playable format, most preferbale wav or mp3

---

### Post by eric71 on 2008-01-21
I've had problems using Hydrogen MIDI output in Rosegarden too. Using GM soundfonts, things are always a bit mixed up. Hydrogen claims to export GM midi files, but something is off (although I haven't tried this in a long time). 

The wav export should definitely work, so I'm  not sure what is going on. If you have audacity installed, try opening the Hydrogen wav output file and see if it is playable. If it is, maybe convert it into an ogg or even re-save it as a wave, and then import that into Rosegaren with it's Audio File Manager. I have a lot of drum loops in ogg format and it converts those fine. If I recall correctly, Rosegarden and Hydrogen use different wav formats, and aren't exactly compatible. I haven't used Hydrogen in a while, but I can remember Ardour using it's exported wav files with no complaints, but having to do a little extra work to get Rosegarden to use them.

To get your midi file into wav or mp3, it depends what you are using for midi output with Rosegarden. I only do mostly audio on Rosegarden (it's interface is just easier for me than Ardour), with one or two midi tracks for keyboard or strings. For this using DSSI or VSTi plugins via DSSI-VST is most convenient. This way everything is internal to Rosegarden. I can just create a new audio track with Master selected as input. This captures the full mixdown of all the other tracks into one new audio track. Then open this new track (by double clicking on it) in whatever external editor you have selected, and save it to whatever file type you want.

If you are running your midi tracks out to Qsynth or Timidity, then you'll have to use QJackCtl's connections dialog to route your output form Qsynth (for instance) into the Jack compatible recording program of your choice (Audacity, Ardour, Time Machine, etc.

---

