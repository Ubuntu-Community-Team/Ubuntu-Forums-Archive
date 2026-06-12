---
title: "Mp3 playlist to CD audio. gnomebaker, serpentine, rhythmbox"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by vector on 2006-06-12
If only this were easier to explain. bu t read on as it has a happy ending

summary:
I managed to convert mp3s. to cd audio and burn an adio cd. using
gnomebaker, serpentine, rhythmbox.. but....

I made a playlist using serpentine because it bosted it could create CD audio.
after wading thru various files and directories I got my list and hit the burn button..Nothing, no error , no indication it was doing anything just nothing. In a hurry now and frustrated I saved the playlist. 
I imported playlist into gnomebaker it said it couldnt find the files. I assumed the playlist format was different and kept moving. Next I used rhythmbox to import the playlist hoping I could save it as a differnt type of playlist. At this point i missed the Create Audio CD in the menu ;(. I saved the playlist. it looked a little different (whilst viewing it with  a text editor) than the previous but gnomebaker still didnt want to find the fiiles.
I started a new audio cd in gnomebaker and dragged a couple of files and hit burn. Seemed to work perfectly, it converted, then asked for a cd. 
Damn but I already had a playlist, it was going to take a while to find where all the files were again. :(
wondering if i could find the original serpentine problem I started it from a CLI and sure enough I got 

  File "/usr/lib/python2.4/site-packages/serpentine/audio.py", line 297, in on_finished
    if self.isWavPcm:
AttributeError: 'IsWavPcm' object has no attribute 'isWavPcm'
Segmentation fault
surfing thru some posts I found what might have been a similar problem. Serpentine can only go from wav to cd audio.

Ok I have a playlist I need to convert to wav or find something that will convert the playlist into something gnomebaker could work with.
I went back to rhythmbox and blow me down I came across the create audio cd. which just worked, found the files converted them and burnt the cd. yay!

now if only I could print the titles of the playlist.. you cant be serious, no print or save playlist as text file...commmooooonnnnnn. I tried to select all but was unable to paste to a text file.aggghhhh

ok your going to say "what are you running"  I dont know. Can we please have a little button  under the system menu that tells us if we are in breezy or whatever, what version and updates we are running so noobs can help you to help us!!

---

### Post by Drakkor on 2006-06-14
My "create audio cd" in rhythmbox is greyed-out and there's no help in the
help section. Any ideas?  Thanks :(

---

### Post by watsoncj on 2006-10-06
If you add the songs to the queue you will be able write them to CD.

To do this, right click the songs and select "Add to Play Queue". Then click the "Queued songs" icon. The "Create Audio CD..." button will now be enabled.

---

