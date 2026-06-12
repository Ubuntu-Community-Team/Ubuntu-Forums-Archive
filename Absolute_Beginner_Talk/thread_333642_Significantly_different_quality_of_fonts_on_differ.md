---
title: "Significantly different quality of fonts on differing resolutions with an LCD screen"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by vf514 on 2007-01-07
I do not understand why the quality of fonts on Ubuntu 6.10 changes such a substantial amount at different resolutions. At 1024 x 768, the fonts appear almost flawless. This not the case, however, at a resolution of 1280 x 1024 on my LCD screen; typeface edges seem very rough and the width of the lines vary a large amount.

Why does this occur, and is there a way to display fonts at the same quality as in lower resolutions?

---

### Post by kebes on 2007-01-07
Hmm... I've never noticed what you describe. Is it just fonts or is it everything that becomes slightly blurry?

Some things to try:

-What is your monitor's native resolution? For LCD if you run at anything but the native resolution, there will always be blurry edge artifacts (especially noticeable for fonts).

-If you're sure you're running at the native LCD resolution, there is often an "auto" button on the LCD that causes it to make sure it lines up the image with the LCD array. After this is done the image usually goes back to being 'crips' the way you expect it to be.


(I apologize if these are things you've already tried...)

---

### Post by vf514 on 2007-01-07
> **kebes said:**
> Hmm... I've never noticed what you describe. Is it just fonts or is it everything that becomes slightly blurry?

Some things to try:

-What is your monitor's native resolution? For LCD if you run at anything but the native resolution, there will always be blurry edge artifacts (especially noticeable for fonts).

-If you're sure you're running at the native LCD resolution, there is often an "auto" button on the LCD that causes it to make sure it lines up the image with the LCD array. After this is done the image usually goes back to being 'crips' the way you expect it to be.


(I apologize if these are things you've already tried...)

I appreciate your reply. Interestingly enough, my fonts appear quite similar to those depicted in the Wikipedia article concerning native resolution (to a lesser extent):

[http://en.wikipedia.org/wiki/Native_resolution](http://en.wikipedia.org/wiki/Native_resolution)

The variations in the widths of the lines are somewhat similar. However, according the manual supplied by the manufacturer, there are indeed 1280 x 1024 pixels on my screen, and Windows XP displays the fonts perfectly at either resolution. In addition, adjusting the phase tracking to very high or very low values significantly improves the appearance of fonts (as well as making visual elements a bit blurry), but these settings are lost when the "auto" switch is pressed.

---

### Post by po0f on 2007-01-07
vf514,

Do you experience the problems if you use 1280x960 instead of 1280x1024?  The former is a 4:3 ratio, the latter 5:4.

---

### Post by vf514 on 2007-01-07
> **po0f said:**
> vf514,

Do you experience the problems if you use 1280x960 instead of 1280x1024?  The former is a 4:3 ratio, the latter 5:4.

There is marginal improvement using 1280 x 960, but the difference is too minute to be noticeable. In addition, the display appears proportionally incorrect at the resolution. Fonts seem to look better at lower resolutions in my current situation.

---

### Post by kebes on 2007-01-07
You could try changing the default font set and/or playing with the font anti-aliasing featurs (and sub-pixel font rendering). Maybe some of those settings got turned on by mistake?

Go to System > Preferences > Font

Try using a different rendering style, for LCDs you also have the option of controlling the subpixel smoothing (the right pixel order of course depends on your monitor... you can usually see it with a magnifying glass).

---

### Post by Waappu on 2007-01-07
Hi

You might look this
[https://launchpad.net/ubuntu/+source/fontconfig/+bug/63403](https://launchpad.net/ubuntu/+source/fontconfig/+bug/63403)

I changed settings Subpixel Smoothing on System->Preferences->Fonts

---

### Post by vf514 on 2007-01-07
I have extensively experimented with the font dialog.

I apologize; I have looked at screenshots of other Ubuntu configurations found the fonts depicted were were exactly the same as how the fonts appeared on my LCD screen. Thus I conclude that the fonts on Ubuntu simply don't display very well on my particular screen at 1280 x 1024 resolution. For one reason or another, fonts on Windows appear much better on my monitor at high resolutions.

---

### Post by konungursvia on 2007-01-08
> **vf514 said:**
> I have extensively experimented with the font dialog.

I apologize; I have looked at screenshots of other Ubuntu configurations found the fonts depicted were were exactly the same as how the fonts appeared on my LCD screen. Thus I conclude that the fonts on Ubuntu simply don't display very well on my particular screen at 1280 x 1024 resolution. For one reason or another, fonts on Windows appear much better on my monitor at high resolutions.

I have the same problem, and found this thread because I was checking before starting my own. My fonts don't look very good, now that I added my NVIDIA driver to use the monitor's native 1280X1024, particularly in Firefox, where the k is almost like a < with the left side stroke almost missing in the default font size. Can we install Windoze fonts here? I have a whole CD full of them.

---

### Post by vf514 on 2007-01-08
> **konungursvia said:**
> I have the same problem, and found this thread because I was checking before starting my own. My fonts don't look very good, now that I added my NVIDIA driver to use the monitor's native 1280X1024, particularly in Firefox, where the k is almost like a < with the left side stroke almost missing in the default font size. Can we install Windoze fonts here? I have a whole CD full of them.

I apologize for replying to you so long after you have posted your message. It is in fact possible to install some Microsoft fonts from Ubuntu repositories. You will initially need to add either the universe or multiverse repositories (I do not recall which one specifically, it is possible to add both), and subsequently update your package manager:

$ sudo aptitude update

To install the fonts, run the following command:

$ sudo aptitude install msttcorefonts

However, even Microsoft-supplied fonts appear to be rendered better on Windows then Ubuntu.

Please let me know if you have further questions related to installing Microsoft fonts. You do seem somewhat experienced, so I apologize if you already knew any of this.

---

### Post by luvinit on 2007-01-08
I find my fonts only work well in the 1024x768 resolution too, on my AOC LCD.  I can't remember exactly what I did to my fonts but I know I used this info

[http://ubuntuforums.org/archive/index.php/t-4456.html](http://ubuntuforums.org/archive/index.php/t-4456.html)

contrary to what many say, my display is much clearer in Ubuntu than windows. I think the current Nvidia drivers just don't seem to work well with my card. The display has become even sharper since installed Beryl.  Monochrome, no smoothing, full hinting seems to work best for me.

---

### Post by vf514 on 2007-01-08
> **luvinit said:**
> I find my fonts only work well in the 1024x768 resolution too, on my AOC LCD.  I can't remember exactly what I did to my fonts but I know I used this info

[http://ubuntuforums.org/archive/index.php/t-4456.html](http://ubuntuforums.org/archive/index.php/t-4456.html)

contrary to what many say, my display is much clearer in Ubuntu than windows. I think the current Nvidia drivers just don't seem to work well with my card. The display has become even sharper since installed Beryl.  Monochrome, no smoothing, full hinting seems to work best for me.

Yes, installing Beryl did make a slight difference. Running the color balance function on my LCD screen may have also slightly improved contrast. I am beginning to get more and more used to it, actually. However, it may be something for Ubuntu developers to look into for future releases, provided enough people are experiencing this issue.

---

