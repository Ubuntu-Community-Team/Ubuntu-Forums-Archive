---
title: "alsa"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by guyraz on 2007-05-15
I've installed skpye for my feisty and the sound capture (microphone) doesn't work
checked under sound from the system preference menu, and it says it use ALSA for sound capture, by testing it there is no beep.
using eikiga as well there is no recording
need help please

---

### Post by mahy on 2007-05-15
install the gnome-alsamixer and mark all the checkboxes about recording and capturing. that's what worked for me.

---

### Post by guyraz on 2007-05-21
did that, but still won't work, gave the following massage when opening application
any idea?

Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Master": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Master": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Headphone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Headphone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Bass": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Bass": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Treble": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Treble": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-3D_Control_Sigmatel_-_Depth": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-3D_Control_Sigmatel_-_Depth": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-PCM": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-PCM": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Front": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Front": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Surround": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Surround": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Synth": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Synth": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Wave": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Wave": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Wave_Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Wave_Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Wave_LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Wave_LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Wave_Surround": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Wave_Surround": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Line": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Line": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Line_LiveDrive": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Line_LiveDrive": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Line2_LiveDrive": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Line2_LiveDrive": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-CD": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-CD": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Mic": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Mic": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Video": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Video": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Phone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Phone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-IEC958_Coaxial": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-IEC958_Coaxial": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-IEC958_LiveDrive": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-IEC958_LiveDrive": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-IEC958_TTL": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-IEC958_TTL": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-PC_Speaker": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-PC_Speaker": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Aux": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Aux": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Capture": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Capture": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-AC97": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-AC97": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-Headphone_LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-Headphone_LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-Headphone_Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-Headphone_Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-Tone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-Tone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-3D_Control_-_Switch": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-3D_Control_-_Switch": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-Mic_Boost___20dB_": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-Mic_Boost___20dB_": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-Mic_Select": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-Mic_Select": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-IEC958_Optical_Raw": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-IEC958_Optical_Raw": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-Mix": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-Mix": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-Mix_Mono": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-Mix_Mono": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-External_Amplifier": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-External_Amplifier": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-SB_Live_Analog_Digital_Output_Jack": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-SB_Live_Analog_Digital_Output_Jack": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-Sigmatel_4-Speaker_Stereo": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-Sigmatel_4-Speaker_Stereo": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-Sigmatel_Surround_Phase_Inversion_Playback_": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-Sigmatel_Surround_Phase_Inversion_Playback_": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/SigmaTel_STAC9721,23": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_names/SigmaTel_STAC9721,23": `,' is an invalid character in key/directory names

---

### Post by JediSpam on 2007-05-21
ugh looks like a mess. do you have onboard audio?

---

### Post by guyraz on 2007-05-21
yes, is it a problem?

---

### Post by sickpuppet on 2007-06-16
Hi guyraz - 

This is a bug in gnome-alsamixer. See [http://bugzilla.gnome.org/show_bug.cgi?id=429012](http://bugzilla.gnome.org/show_bug.cgi?id=429012)

regards
Ben

---

