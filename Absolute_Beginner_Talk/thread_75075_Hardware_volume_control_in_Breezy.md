---
title: "Hardware volume control in Breezy"
date: 2005-10-13
forum: Absolute Beginner Talk
---

### Post by bengtfalke on 2005-10-13
I have a couple of buttons (keys) on my laptop for controlling the speaker volume. If I try to use them a small box shows up where the slider moves right and left without any change to the volume. If I instead move the slider in the speaker icon on the top row of the screen all works OK.

If I open the volume control program with a lots of sliders in it, I can see that the buttons affect the overall volume slider. But it is the slider named Headphone that controls the volume in reality. Is there a way to map these hardware keys to control the correct slider?

regards/falke

---

### Post by sean.smithson on 2005-10-15
I have the exact same problem, I'm on breezy with an Acer Aspire 5002WLCi.  If anyone knows a solution I'd sure like to hear it :)

Sorry for not answering your question though...

---

### Post by sean.smithson on 2005-10-15
Well, I lied, I do have an answer for your problem, possibly.  I assume you're soundcard uses the snd_intel8x0 module, right?  If so, just do this, touch a new file in /etc/modprobe.d, call it intel8x0 or something, and add to this file the following line:

options snd_intel8x0 ac97_quirk=hp_only

Next time your modules are loaded everything should work fine, this'll get rid of the headphone volume control, and master will act as headphone used to.

---

### Post by bengtfalke on 2005-10-15
Thank you , mate! That did the trick! :p 

People like you are absolute invaluble!

Tricks like this really should be included in the documentation or collected in the WIKI or something.......

regards/falkeThank you , mate! That did the trick! :p

Though I had to save the file in my home directory and then change to **root user** with **sudo su** in the terminal window to have the rights to copy to that directory with the command: **cp intel8x0 /etc/modprobe.d** and then **ctrl-d** out to my default user.

People like you are absolute invaluable!

Tricks like this really should be included in the documentation or collected in the WIKI or something.......

regards/falke

---

