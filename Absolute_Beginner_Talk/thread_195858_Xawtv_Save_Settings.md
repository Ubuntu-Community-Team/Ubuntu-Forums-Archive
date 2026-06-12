---
title: "Xawtv Save Settings"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-06-13
I have it working,but everytime I bring it back up, I have to set the whole thing up again eg: PAL to NTSC,mono to stereo,and frequency table europe-west to us-cable,and Capture from overlay to grab display,these settings are lost when I shut Xawtv down. Anyway to make these settings stick?  Thanks :)

---

### Post by William Pickett on 2006-12-22
Here is the fix:
Code: Sudo nano  ~/.xawtv config

Then, you will see the basics, commented out with a # sign,; and as you look down at defaults, you will see what each channel should look like.
What I did was look online to get the tv channel info off my cable supplier, for me its comcast- look under TV Guide followed by your city name in Google or whichever browser you use.
This will give you the name and channel lists.

All you do is make each channel that you want, such as [MSNBC]
next line would have channel = "x", and the other data as shown.

WHen you are finished, press ctrl x to exit- it asks for y/n response, say y for yes, then system will show save to file which will be this ~/.xawtv config, and press ctrl x again to return to the prompt- any Q email me at wkpickett0154'at'comcastdotnet, subject Ubuntu help Q.

William Pickett

---

