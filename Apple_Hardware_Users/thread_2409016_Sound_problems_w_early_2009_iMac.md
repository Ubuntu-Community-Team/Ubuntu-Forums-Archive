---
title: "Sound problems w/ early 2009 iMac"
date: 2018-12-26
forum: Apple Hardware Users
---

### Post by henry-j-spare on 2018-12-26
I have an early 2009 iMac running Ubuntu 18.04. The audio quality was poor because there are two speakers per channel, and it was only using the "tweeter" and not the bass drivers. After a lot of fiddling, I realized I could set it to quadraphonic surround, and it would use the bass drivers as rear speakers.

The issue now is that some content seems to have the front channel audio "mapped" to the rear (or it's actual surround), but some stereo content doesn't use the rear channels, resulting in tinny sound. Is there a way to send the front audio to the "rear" channels, so it can use both drivers per channel?

---

### Post by wildmanne39 on 2018-12-26
*Thread moved to **Apple Hardware Users for a more appropriate fit**.*

---

### Post by gsahli on 2018-12-30
Install pavucontrol - you can use this gui to tell you what is different.
Does changing volume help? Is there an impedance-matching issue with speakers? (Are you supposed to connect them that way?)

---

### Post by jamolver on 2019-01-03
You can try this:
Fix iMac sound in Ubuntu
Open a Terminal
Type ‘alsamixer’ (without quotes) and hit ‘Enter/Return’
The following 1980’s style display will appear: –
[IMG]https://aozoeky4dglp5sh0-zippykid.netdna-ssl.com/wp-content/uploads/2011/06/joey@joey-iMac-_008-500x366.png[/IMG]
Tinny sound in Ubuntu on your iMac? Solve it


Using the navigation keys on your Keyboard select the fourth pillar from the left called ‘Front Speaker’
Increase the volume of the ‘Front Speaker’ by pressing the ‘Up’ navigation key
Now navigate to the first ‘Surround Speaker’ entry
Un-mute it by pressing the ‘M’ key
Nudge across to the second and press the ‘Up’ key to increase its volume
Press CTRL+C to exit the ‘alsamixer’

---

