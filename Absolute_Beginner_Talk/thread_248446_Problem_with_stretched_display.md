---
title: "Problem with stretched display"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by g0nzo on 2006-09-01
Hi,

After installing nvidia drivers according to a tutorial, which I found on these forums (I have 7600GT card) I got strange problem with setting correct resolution.

If I set resolution 1024x768 like I had in windows, everything is much bigger (fonts, menu etc). If I set 1280x1024, it's more or less similar to 1024x768 on windows. But the problem is that everything looks like it's a bit stretched horizontally - fonts, buttons, everything, no matter what resolution I choose.

---

### Post by jorn on 2006-09-01
It's important to find the resolutions that fits your monitor best.
And it is correct that some resolutions makes you screen look wierd.
Your monitor manual may be at help here or you can try different resolutions and se what's best. There is a way too to add mor resolutions to your config file.

---

### Post by g0nzo on 2006-09-01
Ok, I was a bit stupid as 1280x1024 is not 4:3 :) 
However when I change to 1280x960 and set any refresh rate, the whole screen is moved to the right. I get something similar in windows, when I change my refresh rate from 85 or a game changes refresh rate to 60.

I've changed my monitor drivers from plug&play to LG Flatron 795FT, but there's no change.

Is there any solution for it?

---

### Post by gn2 on 2006-09-01
What is your monitor make and model, is it a TFT and if so what is it's native resolution?

---

### Post by g0nzo on 2006-09-02
It's LG Flatron 795FT FB795E-EP and it's a CRT. I've found its manual [here]("http://www.fixya.com/support/p397773-lg_flatron_795ft_white_17_crt_monitor/manual-2208"). There's a table of built in resolution/fq settings ([page 20]("http://www.fixya.com/support/p397773-lg_flatron_795ft_white_17_crt_monitor/manual-2208/page-20")) and 1024x960 is not mentioned there.

It works fine in 1024x768x85, but everything is just huge. Much bigger than in windows with the same setting.

---

### Post by gn2 on 2006-09-03
As it's a CRT it will be 4:3 aspect ratio, so 1280x1024 will work.
Other aspect ratios apply to widescreens.
Have you tried using the latest Nvidia driver from the Nvidia website?
It comes with a configuration utility.
You should be able to use this to check the driver is set to 1280x1024
If the screen appears stretched, and extended past the edges of the viewable area, there should be buttons on the monitor to adjust the position.

---

### Post by g0nzo on 2006-09-03
Thanks, I'll try the latest drivers. I tried installing them first, but I got an error, that "ld" (is it linker?) can't be found and I should add it to the PATH variable.

Doesn't 1280x960 have 4:3 aspect ratio? 1280x1024 fits the screen perfectly, it just looks stretched :) 1280x960 looks correctly, but is shifted and it can't be adjusted using monitor position settings.

---

