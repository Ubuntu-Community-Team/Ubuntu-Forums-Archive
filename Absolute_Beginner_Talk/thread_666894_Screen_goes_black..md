---
title: "Screen goes black."
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by wavemaker on 2008-01-13
Gooday all. I have just got this little problem today. Nothing has been changed by me. Have installed updates as they arrive.
When typing a reply to a post on another forum (golf related) if I misspelled a word the little  red line would come up under it. Right click to fix and the screen goes black for a couple of seconds with the dialog showing in white. It then reverts to normal screen with the error fixed. It's no biggy really but more annoying than anything. Any ideas? TiA. Regards, James.

---

### Post by Joeb454 on 2008-01-13
I'm guessing that it's something to do with a dictionary type thing.

I.e. I know that in firefox there's a dictionary

---

### Post by wavemaker on 2008-01-13
Should have mentioned I am using SeaMonkey.

---

### Post by naugiedoggie on 2008-01-13
> **wavemaker said:**
> Gooday all. I have just got this little problem today. Nothing has been changed by me. Have installed updates as they arrive.
When typing a reply to a post on another forum (golf related) if I misspelled a word the little  red line would come up under it. Right click to fix and the screen goes black for a couple of seconds with the dialog showing in white. It then reverts to normal screen with the error fixed. It's no biggy really but more annoying than anything. Any ideas? TiA. Regards, James.

Hello,

Is that the entire terminal screen, not just the browser window?

Assuming that it is, it sounds like a video driver issue.  Something is responding to the mouse event inappropriately.  Some questions worth looking at:  Does it happen in other browsers?  Does it happen in other forums (like this one)?  During your "normal updates," did you get an update to a video driver?  If you are using a proprietary driver, one of the nonstandard ones that ship with Ubuntu but are not installed by default, you might try switching it off.

I would not expect that any event handler in a web page would be able to monkey an entire terminal, but I suppose under certain conditions it might be possible.

Thanks.

mp

---

