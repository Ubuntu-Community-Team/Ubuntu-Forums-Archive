---
title: "Change default font to Ubuntu Font from command line in Gnome"
date: 2010-10-10
forum: Art &amp; Design
---

### Post by clockworkpc on 2010-10-10
Hi,

I know that we can change the default font from "Appearance Preferences > Fonts" but I'd like to do it from the command line.
Also, given that the new Ubuntu Font doesn't have a fixed-width font yet, I'd like to do it as follows:

Application font: Ubuntu : 11
Document font: Ubuntu : 11
Desktop font : Ubuntu : 11
Window title font: Ubuntu Bold : 11
Fixed width font : Monospace : 10

Besides enjoying command line configuration, my reason for asking this is I've started making a regularly remastered, redistributable DVD of Ubuntu Lucid with all the updates, etc., and whatever I can do by command line just saves me doing it post-installation.

Thanks to anyone who can help me.

---

### Post by ljungkvist on 2011-09-22
I know this is quite late, but still...

The first two ('Application font' and 'Document font') can be changed using

```

gconftool-2 --set --type string /desktop/gnome/interface/font_name "Ubuntu 11"

```

and

```

gconftool-2 --set --type string /desktop/gnome/interface/document_font_name "Sans 10"

```

respectively, and the 'Fixed width font' can be changed using

```

gconftool-2 --set --type string /desktop/gnome/interface/monospace_font_name "Monospace 9"

```

I still haven't found any way to change the other two though. Anyone else have any idea?

---

