---
title: "after update. No sound using firefox"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by impakt on 2006-06-23
when i watch any video or try and play a sound clip i hear nothing when using firefox. All system sounds and music/downloaded video works fine. Anything i can do to get it back? thanks

---

### Post by nitricacid on 2006-06-23
Find and use a plugin for w\e media device you use to play in firefox, such at totem-gstreamer or Mozilla-plugin-vlc.
I found VLC is better at streaming video from the net.
VLC is (in my opinion) better at playing media that is directly on your computer aswell.

---

### Post by impakt on 2006-06-23
i downloaded mozilla-plugin -vlc with synaptic. not sure what to do after i installed them(that plugin came with a bunch of others) sound is still not working. Video is, just no sound. 

Thanks again

---

### Post by nitricacid on 2006-06-23
[QUOTE=impakt]i downloaded mozilla-plugin -vlc with synaptic. not sure what to do after i installed them(that plugin came with a bunch of others) sound is still not working. Video is, just no sound. 

Thanks again[/QUOTE]

Rite click on the speaker that is on the Menu BAR and Open Control Panel.
Go Volume Controls>Edit>Prefrences
Check All the boxes.
Under the PLAYBACK tab there should now be Master, Master Mono, Head Phones, & PCM (if they weren't there already)
Try turning them up while you are watching a streaming video on firefox.

My Sound is on the PCM line so when I try to adjust the volume from the menu speaker it doesn't change the volume, i have to manually go into the Volume Control panel and change the PCM, master, & sometimes Headphone volumes.

---

### Post by vigleik on 2006-06-23
What do you mean "using firefox"? For example, if you mean watching videos with flash, you should know that flash audio doesn't play well with other programs using audio at the same time. (It's an oss-alsa issue I think.) In that case, try the following. Make sure no other programs are using sound. Don't just pause the sound in your favorite music player, turn it off. Then *restart firefox*. It sounds silly, but it sometimes helps. Now try again.

I guess there could be a number of other problems, but this is how I solved my problem when I got no sound with flash.

Vigleik

---

### Post by nitricacid on 2006-06-23
[QUOTE=impakt]when i watch any video or try and play a sound clip i hear nothing when using firefox. [/QUOTE]

I assumed you mean you were trying to watch streaming mpeg,etc... on firefox.

[quote=NitricAciD]Rite click on the speaker that is on the Menu BAR and Open Control Panel.
Go Volume Controls>Edit>Prefrences
Check All the boxes.
Under the PLAYBACK tab there should now be Master, Master Mono, Head Phones, & PCM (if they weren't there already)
Try turning them up while you are watching a streaming video on firefox.[/quote]
I simply suggested trying to mess around with the Volume Controls and see if one of the channels (such at PCM) were muted for that particular media that you were trying to stream.

---

### Post by enix on 2006-06-25
I have the exact same problem with the sound in firefox after upgrades. The video is not in flash format, btw. I don't know of a solution yet ( which is why i'm here), just thought maybe others have experienced this also.

---

