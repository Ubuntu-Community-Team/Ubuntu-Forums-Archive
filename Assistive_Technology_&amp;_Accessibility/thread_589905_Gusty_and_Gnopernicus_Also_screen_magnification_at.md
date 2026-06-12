---
title: "Gusty and Gnopernicus? Also screen magnification at login?"
date: 2007-10-24
forum: Assistive Technology &amp; Accessibility
---

### Post by joann on 2007-10-24
Hello all,

I just installed Ubuntu Gusty Gibbon 7.10. I must say that the installation was a breeze. I was able to use full screen magnifications and speech synthesis from the live CD! This made installation of linux possible and quite frankly a pleasure. Also, the improvements made to the Universal Access are nice and enable further customizations that was previously not available. I had a few questions regarding making my new installation even more accessible.
First, I noticed that gnopernicus was not installed by default. So, I installed it using apt-get install gnopernicus. However, when I ran gnopernicus I only got speech output and the screen magnifier did not seem to work. I would like to get gnopernicus working with the magnifier because gnopernicus allows the user to set hot keys that will enable dynamic changes such as zooming in or zooming out. I am not aware that orca has this feature. Does any one know how I can use gnopernicus to enable full screen magnification?

Second, I would like to have some sort of magnification software or speech synthesis running at login time when GDM starts. Can this be accomplished?

Any help would be great,
Joann

---

### Post by joann on 2007-10-26
Hello again,

I found a "quick" solution to the gnopernicus problem, that seemed to work on my computer.

I first started orca, and then I started gnopernicus. I had to disable speech in gnopernicus, since orca was still talking. 
 (Startup modes, uncheck speech). After that I went ahead and set up a few keyboard shortcuts by going to Preferences -> Command Mapping -> User Defined tab -> Add. I was presented with a window that allowed me to select a keyboard combination. After confirming my keyboard selection another window showed up that asked me to select a command (such as increase x, decrease y, invert on, ...) to be mapped. That was it. This seemed to work well for me and now I can zoom in and out, or turn inverse on and off with the keyboard combinations I set up.

Also, any suggestions or ideas on how to enable screen magnification and speech synthesis at the login time (when I am prompted for my user name and password) would be greatly appreciated.

Joann

---

