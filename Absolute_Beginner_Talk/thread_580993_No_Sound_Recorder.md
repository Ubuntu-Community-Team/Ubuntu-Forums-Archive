---
title: "No Sound Recorder"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by iggyigg on 2007-10-19
[B]BEGINNER'S WOES, NO SOUND RECORDER :confused:
[/B]
I'm using Ubuntu Feisty Fawn (7.04) and a modern good-quality Plantronics Skype-compatible headset.  I'm having problems making voice recordings with it (but no probs in listening to CDs, audio clips etc).
When I try to use the [COLOR="Red"]“SOUND RECORDER”[/COLOR], whatever option I choose (Capture, Microphone, MIC Master, mono, Mix, Line-in etc), I get:
[COLOR="Red"]“Your audio capture settings are invalid.  Please correct them in the Multimedia settings.” 
[/COLOR]
I have followed the Community Doc instructions for Audio Capture. So I went to gnome-volume-control; I ticked [COLOR="Lime"]“Capture”[/COLOR] under[COLOR="Red"] “Preferences”[/COLOR]; I ensured that the microphone and speakers weren't crossed out and I moved the volume on them to maximum.

When I click on[COLOR="Red"] “Recording”[/COLOR] in Volume Control, I have 3 columns with their individual recording slide bars: [COLOR="Lime"]Line- In Capture[/COLOR], [COLOR="Lime"] Microphone [/COLOR][COLOR="Lime"]Capture[/COLOR] and [COLOR="Lime"]Capture[/COLOR].  I've turned the volume to maximum on all three.  I have noticed that I can't activate the microphone clicking on the icon at the bottom of each of the 3 columns.  So for example, when I activate Microphone Capture, Line- In Capture then deactivates (ie the red cross on it appears) and vice-versa.  Is that normal?  Whichever permutation I use, the Sound Recorder still doesn't work.

In the Switches tab, there is only one entry: [COLOR="Red"]Hardware Volume Split[/COLOR] .  I have ticked this too for good measure but it still hasn't made any difference.

Then when I go into [COLOR="Red"]“Sound Preferences”[/COLOR] (in the System menu), and I try to test “Sound Capture”, choosing ESS Solo-1, ALSA or OSS (under the “Audio Conferencing” heading), I get the following message:
[COLOR="Red"]“gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not get/set settings from/on resource.”[/COLOR]
If however, I choose [COLOR="Red"]“Test Sound”[/COLOR] in “Sound Capture” above, then I hear very briefly the high-pitched sound (as below), followed by an equally brief deep base sound.  Does this indicate a problem?  Are the “Multimedia settings” (referred to in the dialog box) these “Sound Preferences” that I've been trying to adjust?

The Sound Playback pipeline test appears to be successful however under each of the “Sound Events”, “Music & Videos” and “Audio Conferencing” headings – I get a high-pitched continuous sound (similar to EG the BBC test page sound on TV) which only turns off when I click on “ok”.
And another question, I have never downloaded any drivers for my modern Plantronics (Audio-90) headset – can you please confirm that this isn't needed for headsets and that this model should work without problems on Ubuntu?!

I'm also having problems with Skype for Linux (the latest package 1.40.118-1).  I hear a loud crackling in the background, causing sound distortions and break-ups on both ends of the line (including when I use the robot test line). 
 
I'm also confused about sound cards.  Am I correct in thinking that[COLOR="Red"] ESS Technology ES1969 [/COLOR](Solo 1) [COLOR="Red"]AUDIODRIVE[/COLOR] (as listed in my “device manager”) is my Sound card?  If that is the case, then why does[COLOR="Red"] ESS ES1938 (Solo-1[/COLOR]) appear in my volume control etc?  I can't find ESS ES1938 (Solo-1) listed in my Device Manager – is that normal?

Thanks for any help!!:)

---

### Post by 001100 on 2007-10-19
im not trying to be unhelpful. is sound recorder really that important?? Just search sound recorder in add/remove programs. The servers are pretty verloaded at the moment so wait a little wile b4 downloading anything.

---

### Post by iggyigg on 2007-10-19
Thanks very much for your reply, 001100 !.  Sound Recorder per se is potentially very useful to me actually.  But the biggest reason is because I'm having problems with Skype and the suggestion from their forum was to check the Sound Recorder....
Are you suggesting that I download a different Sound Recorder program? :confused:

---

### Post by 001100 on 2007-10-19
yes. try using a normal mic. insted of the skipe one. just a suggestion. but yes try downloading a different sound recording program. also it might be your sound card even though you get audio but ubuntu might not support the recording features on your sound card. if the other sound recorder doesn't work then try using a different sound card.

---

