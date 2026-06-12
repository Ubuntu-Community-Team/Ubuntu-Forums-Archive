---
title: "OpenOfiice.org Icons &amp; Dark Themes"
date: 2009-11-02
forum: Art &amp; Design
---

### Post by AlphaLexman on 2009-11-02
I know that OpenOffice.org [OOo] has long had bug issues with dark themes. So I decided to find out exactly where the issues begin. Apparently anything under 15% (darkness) will force OOo to use the high contrast icon theme.

This translates to exactly 38.4/256...

Therefore background RGB values of 38,38,38 (#262626) the icons will be forced into high contrast mode.
Whereas background RGB values 0f 39,39,39 (#272727) the icons will maintain the 'Human' icon theme, or other (untested) icon set.

If your Gtk or Qt4 desktop theme can be manually adjusted without upsetting the overall look of the theme, just set the background color to 39,39,39 or greater.

---

