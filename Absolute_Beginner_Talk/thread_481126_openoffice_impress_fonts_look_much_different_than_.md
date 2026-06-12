---
title: "openoffice impress fonts look much different than MS office in feisty"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by avilella on 2007-06-22
Hi,

When I open ppt presentations with ooimpress, the fonts look bigger than they should, so the slides are awfully unscaled.

Does somebody know how to make ooimpress show a font type similar to the font used in powerpoint?

---

### Post by Pconfig on 2007-06-22
I think you need to install the microsoft fonts before OOo can use them.

Try this:

```
sudo apt-get install msttcorefonts
```

The fonts you install with this package are:
    *  Andale Mono
    * Arial Black
    * Arial (Bold, Italic, Bold Italic)
    * Comic Sans MS (Bold)
    * Courier New (Bold, Italic, Bold Italic)
    * Georgia (Bold, Italic, Bold Italic)
    * Impact
    * Times New Roman (Bold, Italic, Bold Italic)
    * Trebuchet (Bold, Italic, Bold Italic)
    * Verdana (Bold, Italic, Bold Italic)
    * Webdings

If your presentation uses a font on this list, you should search for the right package to install.

---

### Post by jw5801 on 2007-06-30
Cheers! Amazing how quickly typing "Arial" into the search function and looking at the first few threads can find you what you're looking for.

---

