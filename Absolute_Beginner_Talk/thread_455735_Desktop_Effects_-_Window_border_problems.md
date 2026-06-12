---
title: "Desktop Effects - Window border problems"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-05-26
I decided to post this because I think a lot of people have this problem and are unable to find any useful help else where on the internet.  I hope this can help you!
I don't know how many other people have this problem, but I'm guessing a lot because it's experimental, but here's the situation:

You've just installed 7.04 and want to give desktop effects a try, or you've tried them, then looked at beryl and used it instead.  Either way...

The problem (for some):
When the effects are enabled, everything seems fine, but the window borders (top bar ans sides) disappear!

The Solution:
You can go [here]("http://klamstwo.org/evad/archives/5") for a slightly more in-depth discussion, but the fix that worked for me was this:

1. open your /etc/X11/xorg.conf file as root (so you can save it)
[COLOR="Red"]*   *   *   *   *!mportant Note: this is a fairly harmless change, but it's still a good idea to backup this file first!*   *   *   *   *[/COLOR]

2. add this line under the category "screen"
        The line is:
> Option &#8220;AddARGBGLXVisuals&#8221; &#8220;True&#8221;
not exactly, make sure the space between the "option" and the ""add..." is a tab not a space and that they are really quotes, not some random symbol.  If it doesn't start x properly, check these things!

3. save and exit the editor

4. restart the X server (log off first, then do Ctrl + Alt + Backspace)

5. log back on, and try the effects out again

:KS They should work 100% now! :KS

---

### Post by rich.bae on 2007-05-28
You really helped me :-D
Thank you so much.

---

### Post by voam on 2007-06-17
This also worked for me. It was a little tricky because I could not use xterm so had to go in terminal mode. 

Thanks!

---

