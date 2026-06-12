---
title: "Can you move fonts from your HFS+ drive?"
date: 2011-04-03
forum: Apple Hardware Users
---

### Post by Leopoguin on 2011-04-03
I went digging into my OS X partition to see if I could bring over some fonts. 

When I got into /Library/Fonts and /System/Library/Fonts, I found that, oddly, most of the fonts were listed as 0 bytes and would not open in the Ubuntu Character Map.  And indeed they didn't work when I copied them to my ~/.fonts folder on the ext4 partition.  

There were a small number of exceptions where the font was a substantial size and did in fact work when I copied it to my Ubuntu system, but these were obscure fonts.

Although I don't use it, the Mac4Lin project has some Mac fonts packaged with it, from which I picked up Lucida Grande.  

I'm just curious if anyone knows why most (though not all) Mac fonts are not recognized in Ubuntu. Apple's not still using resource forks in its files is it?

---

