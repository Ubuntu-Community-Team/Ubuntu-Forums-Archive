---
title: "Accelerrated graphics driver for Macbook Air?"
date: 2008-06-22
forum: Apple Hardware Users
---

### Post by Brightbelt on 2008-06-22
Hi, 
This thread is a long shot maybe. I feel certain there's no answer for this, but here goes.

Btw, I've done a search etc too already. 

All graphics with gradients in them (this means a smooth, gradual blend between 2 colors), have broken bands for gradients on my Macbook Air. I know of no other name to call this except 'broken bands'. This means you can see the separate progression of a gradient because the changes in the blend are actually seen broken into separate bands.

I know from my past experience on other computers with Linux that installing the accelerated graphics driver is what fixes this problem.

Doing lspci shows me that this laptop has an Intel GMA X3100 graphics set up. 

I don't know where to begin to even think about finding an accelerated graphics driver for that card, if it's even possible.

Does anyone have any ideas?

Many Thanks, Frank B.

---

### Post by BladeMelbourne on 2008-06-23
Is your colour depth 24 bit (not 8 or 16 bit)?

---

### Post by MichaelSwengel on 2008-06-23
This phenomenon is known as "color banding." Unfortunately, it is quite common in Apple's newer notebook computers. This is due to the fact that Apple is now using 6-bit LCDs in their computers instead of the original 8-bit LCDs.

6-bit panels will display some measure of banding - as you have seen.

This page: [http://www.lagom.nl/lcd-test/](http://www.lagom.nl/lcd-test/)  has some good test images that you can use to see what kind of panel you have.

If it's too pronounced, I would take it to an Apple Store and tell them you're not happy with it. See what they suggest. They've come through for me many times with my Macbook Pro.

---

### Post by Brightbelt on 2008-06-23
Thanks Michael and Blade. Maybe Apple would help, but would they do so on a Linux OS? For that, I'm not too sure, but maybe they would.

I should note that on the Apple OS Leopard (this being a dual boot), there seems to be no color banding at all. Their driver seems to iron this problem out I guess. 

Btw, Michael says this is a 6-bit display. As far as Ubuntu goes, I don't know where or how to look that up. I can check the Apple OS to make sure that's what I have.

I certainly trust Michael's word, however. ;)

Again, Many Thanks to you both.

Frank B.

---

### Post by BladeMelbourne on 2008-06-23
Open /etc/X11/xorg.conf in a text editor (nano, kedit, anything)...

Search for "DefaultDepth" and let us know what is to the right of this (it should be a number).

- Mike -

For example, my Mac Mini has:

```
Section "Screen"
        Identifier      "Screen"
        Device          "Radeon9200"
        Monitor         "BenQ"
        **DefaultDepth    24**
        SubSection "Display"
                Modes           "1280x1024"
        EndSubSection
EndSection
```

---

### Post by stream303 on 2008-06-23
Is there an option for your intel card to do dithering?

Although I'm using the nv driver, I always turn on the FPDither option with lcd's.  Here's what my man nv says about it:

>        Option "FPDither" "boolean"
              Many digital flat panels (particularly  ones  on  laptops)  have
              only  6  bits per component color resolution.  This option tells
              the driver to dither from 8 bits per component to 6  before  the
              flat panel truncates it.  Default: off.

Although this is particular to my setup, I wonder if there is something like this for your card?

---

### Post by Brightbelt on 2008-06-24
Thanks Ya'll. Blade I'll give that a try first. :)

---

### Post by Brightbelt on 2008-06-24
Okay, the Default Depth didn't change anything, Thanks for the suggestion there, Blade. 

Stream303, your suggestion seems helpful, but I need to know what file your code is in and how to access it. Is it a file related only to your nv driver? If so, what file could I access that relates to dithering for my driver (intel gma X3100) ?

Are you perhaps implying that some dithering could be set up in my xorg.conf file? I'll google that in the meantime.

Many Thanks, Frank B.

---

### Post by BladeMelbourne on 2008-06-24
Are you saying your default depth wasn't 24?
Did you change it to 24? If so, did you reboot/restart (after saving xorg.conf)?

---

### Post by stream303 on 2008-06-24
> **Brightbelt said:**
> Are you perhaps implying that some dithering could be set up in my xorg.conf file? I'll google that in the meantime.

Perhaps.  That FPDither option can be used with the NV driver regardless of architecture - it was only shown as something to look into that might be similar for the intel card.

Since I'm not a video expert, I hope I am not leading you down the wrong path..

Update: I tried searching for dithering option with the Intel driver and am coming up short...

---

### Post by Brightbelt on 2008-06-24
Yes, Stream303, I googled & came up short as well.

And Blade, yes I did change the file by adding 
```
DefaultDepth     24  
```

I saved the xorg.conf file. I made a backup of xorg.conf first.

And I rebooted, but no luck.

Many Thanks for your suggestions,
I'm still open to ideas. Frank B.

---

