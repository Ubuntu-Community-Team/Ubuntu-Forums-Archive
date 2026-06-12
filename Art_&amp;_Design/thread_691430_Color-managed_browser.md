---
title: "Color-managed browser"
date: 2008-02-08
forum: Art &amp; Design
---

### Post by pjvolders on 2008-02-08
Hi,

i just calibrated my monitor using Argyll and I'm enjoying my fresh ICC profile. But I am still looking programs that can use these profiles, so far i'm only using GIMP. What I need the most is a webbrowser (or a firefox plugin) so i can see correct colors on my favorite websites. Anyone an idea? Or a list of linux software that support ICC profiles?

Cheers,
PJ

---

### Post by Gen2ly on 2008-02-08
Well, I could tell you that xcalib can uses a monitor Icc to calibrate the screen.  As for as that goes I think Icc profiles are mainly used in the Apple community.

---

### Post by jcornuz on 2008-02-11
Hi there,

Welcome to the wonderful world of color management :)

xcalib and an ICC profile will allow you to tweak your video card's output to best match a "known neutral" behavior (gamma of 2.2, color temperature of 64k).

From there, programs like The Gimp, Cinepaint, etc use this same profile to match as closely as possible how they display colors on your screen with the "original file colors".

Obviously, it would be cool to have a color aware browser (so you are sure your pictures are seen with the right colors). Apart from Safari (which already supports that at least in Mac - don't know about the window version), it is coming in Firefox 3.0 - and on Ubuntu :)

If you want to test if how your browser behaves, see [here]("http://www.color.org/version4html.xalter")

If you want to know more about color management and Linux, have a look at [my blog]("http://jcornuz.wordpress.com/category/tutorials/").

Take care.

Joel

---

### Post by pjvolders on 2008-02-11
Hi

i do know your blog, i used your how-to to use the spyder and argyll :-)
So i downloaded fire fox 3 for gutsy [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue77#head-a6374841abe919d98d21b17146e8d6ebba61f955](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue77#head-a6374841abe919d98d21b17146e8d6ebba61f955)
but now, how do i use my icc profile with it? The test-link you provided with the strange image looks the same in both browsers. Is icc support only available in the  final release?

Cheers,
PJ

---

### Post by jcornuz on 2008-02-11
Hi there,

enter about:config as an URL and then set gfx.color_management.enabled to true.

Firefox is now icc v4 compatible (according to the testpage).

:guitar:

Joel

PS: now let's add an ICC profile embedded in every image on the web to make sure we take advantage of this new feature...

---

### Post by pjvolders on 2008-02-11
It works!

Thanks a lot, i also set my monitor profile in gfx.color_management.display_profile and the colors are perfect now! 

Cheers,
PJ

---

### Post by FFred on 2008-02-12
So who says colour is difficult in Linux ?

---

### Post by JPorter on 2008-04-22
Be careful not to double-profile your monitor.

If the ICC/ICM is loaded using xcalib, you do NOT need to load it in Firefox.  If you do both, you will double-calibrate and screw up the display colors in Firefox, correcting well beyond the target.

---

### Post by pjvolders on 2008-04-23
> **JPorter said:**
> Be careful not to double-profile your monitor.

If the ICC/ICM is loaded using xcalib, you do NOT need to load it in Firefox.  If you do both, you will double-calibrate and screw up the display colors in Firefox, correcting well beyond the target.

Are you sure?
I thought xcalib only uses the vcg tag and the "color management" part is done by the program...

Cheers,
PJ

---

### Post by JPorter on 2008-04-29
> **pjvolders said:**
> Are you sure?
I thought xcalib only uses the vcg tag and the "color management" part is done by the program...

Cheers,
PJ

When I load my custom ICM profile with xcalib, the colors on my monitor immediately change.  That indicates that the whole OS environment is then color-corrected, and further profiling in an individual application will double-profile the display output of that application.

Color-managed apps like FF3 can output proper color balance if you load the ICM profile into them directly... and that's WITHOUT xcalib being loaded for the OS at large.  You don't even need the xcalib package installed to do that.  Xcalib is not needed for FF3.0 to do its thing, so using them both to "calibrate" will result in incorrect colors.

---

### Post by jcornuz on 2008-04-30
Hi there,

I would stand on PJVolker's side about that. Monitor calibration is:
[LIST]
[*]loading VGC Tags to put the monitor in a "known" state (typically gamma 2.2 and 65K color temp)
[*]loading the monitor profile on a per-application basis (if
supported) for "proper" color management.[/LIST]
my 0.2 cents :)

Take care,

Joel

---

### Post by pjvolders on 2008-05-02
> **JPorter said:**
> Color-managed apps like FF3 can output proper color balance if you load the ICM profile into them directly... and that's WITHOUT xcalib being loaded for the OS at large.  You don't even need the xcalib package installed to do that.  Xcalib is not needed for FF3.0 to do its thing, so using them both to "calibrate" will result in incorrect colors.

This [http://hea-www.harvard.edu/~maxim/personal/nkoren/Gamma_black_new.png](http://hea-www.harvard.edu/~maxim/personal/nkoren/Gamma_black_new.png) is a good one to see if your monitor is correctly calibrated... If I look at it without loading the profile in xcalib(but in a color managed environment), I can see that my gamma is terribly wrong(my monitor has an awful gamma). But when I load it both in xcalib and in an colormanaged program, my colors and gamma are perfect. Xcalib is just a extended version of xgamma, it just sets your gamma for RGB right. Loading the profile in a program like FF3 is like a finishing touch, setting the details of your colors right.
(this is how I see it, and how my monitor responds best to the calibration...)

Cheers,
PJ

---

### Post by JPorter on 2008-05-07
> **jcornuz said:**
> Hi there,

I would stand on PJVolker's side about that. Monitor calibration is:
[LIST]
[*]loading VGC Tags to put the monitor in a "known" state (typically gamma 2.2 and 65K color temp)
[*]loading the monitor profile on a per-application basis (if
supported) for "proper" color management.[/LIST]
my 0.2 cents :)

Take care,

Joel

Wait, so you're saying that xcalib **does NOT** load the full ICM profile and gamut?  That it only loads the basic gamma information from the supplied ICM profile, and discards the rest of the profile information without applying it to the display?  

That's not how I understood it at all.  I thought that's what a LUT (look-up-table) was supposed to do.  Also, the [Readme over at the developer's website for xcalib]("http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/README.html") isn't clear on this either.


Maybe I'm way off base here, but it seems as though the colors are either correct or they're not.  If the OS is color managed and a properly calibrated profile is loaded, then every application within it will be displaying "corrected" colors to the screen.  On the other hand, if the OS is not color managed, and you load a calibrated display profile into an individual application, that application will do the correction within its own display area to display "corrected" colors to the screen based on the profile.  If you have *both* the OS and the application trying to use a profile, it seems as though you'd double-correct and end up with over-corrected color targets (double LUT application).  I know that's the case in Windows applications when color profiles are loaded globally via the XP Color Powertoy, why should it be different in an X environment?

I guess the only way to accurately test this is to use a digital color card of some type and measure screen output manually (and calculate deviation from target) with each scenario.  Does anyone know of a place online that offers such a card, maybe in sRGB?

---

### Post by pjvolders on 2008-05-07
Hi,

I do not know what program you used to create your profile, but I used [Argyll]("http://www.argyllcms.com/"). Argyll is platform indep. so you can use it under Linux + it supported my spyder. In argyl creating an ICC profile consists of a few steps:
First: do monitor calibration, creates a .cal file. You can use this .cal file with dispwin or xcalib to load your calibration in your hardware.
Second: Measure some patches for the profiling part. The .cal file is used here so that argyll knows what had already been done in the first step!
Third: Combine the 2 to the final .icc profile. The first step provided the data for the 'vcgt'-tag, making sure your gamma/white/black points are right and the second step take care of some color perfecting. 

So a profile created with argyll consist clearly of 2 parts. Xcalib can not use whole of your profile, only the 'vcgt'-tag. On the other hand FF3 or gimp ect. can not use the 'vcgt'-tag but use the actual profile. 
For me, there is very little difference between programs that support .icc profiles and the ones that don't. Only the browns are a little bit better. Loading it with xcalib is a whole difference, meaning that this is clearly the most important step for my profile and display.

Cheers,
PJ

---

### Post by JPorter on 2008-05-08
pjvolders,

I am using a custom profile created with Spyder2express, on XP.  It is a full .icm profile.

I am loading the profile using xcalib.  The documentation for xcalib indicates that it loads both the vcgt (Video Card Gamma Tag) and the LUT (Lookup Table) from the profile.  
[INDENT]Link: [http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/README.html](http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/README.html)[/INDENT]

---

### Post by SDoehla on 2008-05-09
Hi!

I was just nudged that there's some discussion going on whether xcalib alone is enough or not. Frankly speaking, xcalib's documentation is little bit misleading here - maybe it's time to revise it. Anyway, the intended usage of xcalib is:

read the calibration data of a monitor ICC profile (the *vcgt*) and apply it to the system (to the LUTs of the video card)

Obviously, xcalib only covers the calibration part, hence the remaining color work (converting color spaces, etc. ) needs to be done in the application (GIMP, FF3, Cinepaint, ...).

On the other hand, the profile was typically created with the calibration data applied - therefore a tool like xcalib MUST be used for color-managed display. 

Cheers
- Stefan

---

### Post by pjvolders on 2008-05-09
Thanks a lot for clearing it out!
(Stefan Doehla is the programmer of XCalib, I mailed him for clarification) 

Cheers,
PJ

---

### Post by JPorter on 2008-05-11
> **SDoehla said:**
> Hi!

I was just nudged that there's some discussion going on whether xcalib alone is enough or not. Frankly speaking, xcalib's documentation is little bit misleading here - maybe it's time to revise it. Anyway, the intended usage of xcalib is:

read the calibration data of a monitor ICC profile (the *vcgt*) and apply it to the system (to the LUTs of the video card)

Obviously, xcalib only covers the calibration part, hence the remaining color work (converting color spaces, etc. ) needs to be done in the application (GIMP, FF3, Cinepaint, ...).

On the other hand, the profile was typically created with the calibration data applied - therefore a tool like xcalib MUST be used for color-managed display. 

Cheers
- Stefan
Stefan,

Thanks for your participation!

The root of the argument is whether one should use both Xcalib to load a custom ICM profile... AND load that same profile into your image editing application as the display profile.  In GIMP this is called the "Monitor" profile.

Will double-loading the "Monitor" profile in this way cause incorrect image display on-screen within the color-managed application?

---

### Post by SDoehla on 2008-05-20
> **JPorter said:**
> 
The root of the argument is whether one should use both Xcalib to load a custom ICM profile... AND load that same profile into your image editing application as the display profile.  In GIMP this is called the "Monitor" profile.

Yes, of course! xcalib will handle the calibration part of the profile, whereas the application (e.g. GIMP) will do color-conversion from one color space to another (i.e. sRGB->display).
> **JPorter said:**
> 
Will double-loading the "Monitor" profile in this way cause incorrect image display on-screen within the color-managed application?
No, since the profile was created (at least nowadays) with calibration applied. GIMP can not handle this (applying the calibration) since it is the part where the entire system is tweaked (i.e. for all applications!) - hence the need for xcalib.

Cheers
- Stefan

---

