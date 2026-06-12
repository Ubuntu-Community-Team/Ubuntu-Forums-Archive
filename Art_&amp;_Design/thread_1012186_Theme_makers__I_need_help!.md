---
title: "Theme makers:  I need help!"
date: 2008-12-15
forum: Art &amp; Design
---

### Post by Giant Speck on 2008-12-15
Hello,

I'm fairly new to the whole making GTK themes thing, and I need a little help.

Normally, I use only the Murrine engine to make themes.  This is mainly because the engine options are so readily available on the Murrine website:

> - **glazestyle** (change general look, i.e. buttons)
    * 0 = flat hilight
    * 1 = curved hilight
    * 2 = concave style
    * 3 = top curved hilight
    * 4 = beryl/emerald style
- **roundness** (set roundness of buttons and other widgets)
    * 0,1,2,3,4,5,6,7,8 = From flat till too rounded =). 
    Few notes more: 
    1.  concave style (glazestyle = 2) is supported just with roundness = 0,1.
    2.  clearlooks-like default (nice) roundess is "3".
- **gradients** (enable or disable gradients on all widgets)
    * TRUE = enable gradients
    * FALSE = disable gradients
- **menubarstyle** (change style of the menubar)
    * 0 = flat
    * 1 = glassy (it follows selected glazestyle)
    * 2 = gradient
    * 3 = striped
- **menuitemstyle** (change look of menuitems)
    * 0 = flat
    * 1 = glassy (it follows selected glazestyle)
    * 2 = striped
- **menubaritemstyle** (change look of menubar items)
    * 0 = menuitem look
    * 1 = button look
- **listviewheaderstyle **(change look of listviewheaders)
    * 0 = flat
    * 1 = glassy (it follows selected glazestyle)
    * 2 = raised
- **listviewstyle** (change separators of listviews)
    * 0 = nothing (completely flat)
    * 1 = dotted separators
- **sliderstyle** (enable extra features on sliders) [NEXT RELEASE]
    * 0 = nothing added
    * 1 = handles
- **scrollbarstyle** (enable extra features on scrollbars)
    * 0 = nothing added
    * 1 = circles
    * 2 = handles
    * 3 = diagonal stripes
    * 4 = diagonal stripes and handles
    * 5 = horizontal stripes
    * 6 = horizontal stripes and handles
- **animation** (enable or disable animations on progressbars, radios and checks)
    * TRUE = enable animation
    * FALSE = disable animation
- **colorize_scrollbar** (enable or disable colorization of the scrollbar, using bg[SELECTED]) [NEXT RELEASE]
    * TRUE = enable colorization
    * FALSE = disable colorization
- **scrollbar_color** (set the color of the scrollbar) [DEPRECATED]
    * #HEX_COLOR = set custom color
- **hilight_ratio** (set the amount of buttons or widgets hilight)
    * e.g. hilight_ratio = 1.1 for more hilight (useful on dark themes)
    * e.g. hilight_ratio = 0.909090 for a flat looking theme!!!
    * set it to less for a concave theme
- **contrast** (set the contrast of the theme)
     * e.g. contrast = 0.8 for less contrast or more than 1.0 for more contrast on borders!

However, I want to start incorporating aspects of other engines into my themes, including Nodoka, Clearlooks, and Pixbuf.

However, I can't find documentation about engine options for other engines besides Murrine. 

I was wondering if anyone knew where I could find documentation so that I can find out how to theme using the three engines I mentioned, along with any engines I forgot to mention.

Thanks in advance!
Jesse

---

### Post by GrouchoMarx on 2008-12-15
Unfortunately the source code is the best documentation for most gtk engines. Murrine SVN has options that are deprecated and others that aren't listed on the website. Download the source code. It's the only way to know for sure. A less effective alternative is to download a theme for the particular engine and figure out settings that way.

---

