---
title: "48 bit photos on Linux?"
date: 2010-12-23
forum: Art &amp; Design
---

### Post by outofsync on 2010-12-23
Do you know of any Linux tool which would allow me to open a 48bit (16/16/16) RGB image and would let me to do basic work with it? (by "basic work" I mean reading pixel values (as 16 bit values) as well as adjusting brightness/contrast, gamma correction, and dithering while converting it to 24bit. (I guess ImageMagik might be capable of doing this, but it doesn't have a GUI, and I need a GUI).

TIA

---

### Post by prokoudine on 2010-12-25
Actually ImageMagick has a basic GUI. Some of that can be done also on Cinepaint. And you can also use nip2, if you don't mind a scientific UI that looks like a cross between Excel and Photoshop.

---

### Post by gustavomazza on 2010-12-25
I think UFRaw read the values and allow the controls, at least some of them, that you are looking for.

---

### Post by prokoudine on 2010-12-25
> **gustavomazza said:**
> I think UFRaw read the values and allow the controls, at least some of them, that you are looking for.

You cannot possibly be serious about UFRaw opening "48bit (16/16/16) RGB image" :)

---

### Post by JustinR on 2010-12-25
Gimp?

---

### Post by mcduck on 2010-12-25
> **prokoudine said:**
> You cannot possibly be serious about UFRaw opening "48bit (16/16/16) RGB image" :)

Actually yes, that's exactly what it does. :D

Cinepaint will of course handle the job easily, if you just get it installed somehow...

..and then there's Luminance HDR, which while being mainly intended for HDR imaging and tonemapping, might have the tools you want. (I'm not sure about that, it's been a while since I used it last time). If you want to try this, you should know that the version in Ubuntu repositories might still use the old name, Qtpfsqui.

---

### Post by gustavomazza on 2010-12-25
I think Krita have interesting color management options too, work on 16 bit and allow adjust of RGB curves and color balance

UFRaw handle 16 bit images, but I'm finding difficult to find a ICC profile for 7D and 500D photos, even without it I get good results.


The tool depends a lot on the level of results to be anchieved, for creative photography the tools already describe should do the job well, for absolute accuracy (products photos) you will need accurate color calibration could take hours of work.

---

### Post by prokoudine on 2010-12-26
> **mcduck said:**
> Actually yes, that's exactly what it does. :D

Actually no :) UFRaw works on Raw images. None of them are 48bit and definitely not RGB :) And you cannot open a regular TIFF or PNG file there. Check :)

> **mcduck said:**
> ..and then there's Luminance HDR, which while being mainly intended for HDR imaging and tonemapping, might have the tools you want.

I seriously doubt it. All it has re processing is tools to merge exposure stacks to HDR images and then tonemap them. Additionally you can crop an HDR image and adjust levels for a tonemapped (LDR) image. That's it.

---

### Post by ralfowen on 2010-12-26
thanks for  help
 
i have same proplem

---

### Post by outofsync on 2010-12-27
> **prokoudine said:**
> Actually ImageMagick has a basic GUI. Some of that can be done also on Cinepaint. And you can also use nip2, if you don't mind a scientific UI that looks like a cross between Excel and Photoshop.
I just installed nip2. I think it can be just what I need. Regarding Cinepaint, I tried it years ago, but it was always on a alpha-like status. I hope Gimp will implement 48 bit color soon!!

If anybody is aware of other alternatives, please tell!!

---

### Post by prokoudine on 2010-12-27
> **outofsync said:**
> I just installed nip2. I think it can be just what I need. Regarding Cinepaint, I tried it years ago, but it was always on a alpha-like status. I hope Gimp will implement 48 bit color soon!!

If anybody is aware of other alternatives, please tell!!

Well, there is [Pixel]("http://www.kanzelsberger.com/pixel/"), but after 10 years it's still a rough beta with final release not anticipated by anyone anymore (at least that's my impression).

---

### Post by outofsync on 2010-12-27
> **prokoudine said:**
> Well, there is [Pixel]("http://www.kanzelsberger.com/pixel/"), but after 10 years it's still a rough beta with final release not anticipated by anyone anymore (at least that's my impression).
Thanks a lot, installed it. Looks nice, but has serious bugs when working in 48 bit mode. For example, the gradient tool fills half image only, and the TIFF saved files are damaged (at least when saving with LZW compression, which was what I tried).

---

