---
title: "gutsy fglrx and ati radeon 9250"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by okkie on 2007-12-22
i have now done weeks of reading on every possible forum regarding the above ,tried quite a few suggestions and re-installed gutsy 3 times in the process.my 9250/256 card worked perfectly in feisty.it does not with gutsy.i came to realise this is a huge problem in our and other communities.
is something through someones kindness being done or should we buy new cards or go back to feisty.the problem seems to affect various computers in a different way.thanks

---

### Post by shae on 2007-12-22
The problem you are experiencing is that AMD removed support for the 9200/9250 and lower from their driver releases.  You should use the open source driver, or recompile an older kernel and use an older version of fglrx.  If you would like more help doing this, please PM me.

---

### Post by eldepeche on 2007-12-22
Does it not work out of the box? I have a 9250 and I remember it working perfectly under Gutsy. Did you try glxgears and glxinfo before messing with the video drivers?

---

### Post by john.nicholls on 2007-12-22
My 9250 worked fine out of the box with Gutsy and the Ubuntu-supplied driver.

---

