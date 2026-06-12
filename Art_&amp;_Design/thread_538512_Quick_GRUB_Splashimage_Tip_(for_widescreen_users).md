---
title: "Quick GRUB Splashimage Tip (for widescreen users)"
date: 2007-08-30
forum: Art &amp; Design
---

### Post by DEMONIIIK on 2007-08-30
Ok. I would have included this with a little tutorial in response to someone wanting to know how to do a splashimage, but after I lost the hour's worth of writing, let's face it, I'm not doing it. :evil:

Anyway, I'm sure you smarties out there who make custom images have thought of this, but here it is, loud and clear:

So you have a widescreen monitor and all those cool new splash images for GRUB look distorted. Easy easy easy fix.

You can't edit the resolution of the file (640x480 14-bit color), so sorry, but you can change the picture around a bit.

What I would do is, assuming you make your own image, edit the canvas size in your favorite photoeditor to be your desktop size (don't lock aspect ratio when putting that in). Mine would be 1440x900, so I'd put that in for size (make sure pixels is the unit used, or you may end up with a pretty big image, ie 1440 ft x 900 ft... :shock:). Then, lock aspect ratio and change the second (usually smaller) value to be 480. You should have Ax480 for the canvas size, A being a number most likely bigger than 640.

Make your image normal. Nice and pretty. Done? If you didn't already, make it 14-bit color and touch up the mess-ups. Now, go and change the canvas size again (don't crop!) to 640x480. (Make sure lock aspect ratio is off, so that you end up with exactly 640x480).

"It looks skinny!" Yep. But, notice that your perfectly fine 4:3 image gets stretched out when GRUB loads it? So, we applied the same concept in reverse. Now, GRUB will stretch out your image for you so that it looks to be 16:9 again!

Here's a bad example (that I haven't tested, I'll admit, but the concept is there, which I'm positive will work.) attached.

(easy way, set this bad image of mine as your wallpaper and use "stretch to fit". There, I win.)

---

### Post by DEMONIIIK on 2007-08-30
Oh, and my plea to developers is this. Please, perhaps put in an actual splashimage with grub when installing so newbies don't have to deal with this to keep Linux reminding them of DOS...

Also, perhaps have several splashimages made, and have the installer detect/ask the user what their default resolution/aspect ratio is and install the necessary one (or all, to allow easy switching if a part upgrade/downgrade occurs) for them, so distortion isn't even there.

Sure, GRUB is only a momentary part of everyone's boot-up, but splashes add a (guess it) splash of personality! Ubuntu's goal is to make Linux easy, fun, and pretty, so that all humans can use it, why not extend that an additional 30 seconds for GRUB splash?

---

