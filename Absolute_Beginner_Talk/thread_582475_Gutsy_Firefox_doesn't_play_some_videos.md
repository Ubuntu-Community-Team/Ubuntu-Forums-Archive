---
title: "Gutsy Firefox doesn't play some videos"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by AkiraBergman on 2007-10-19
G'day Gutsy lovers,

I got Gutsy working on 386 by updating from Feisty. Download took long but it works nicely indeed. So thank you very much Ubuntu community. By the way, the update package asks for the CD at some stage but it does not use it, as far as I can see. Seems to be a bug.

Some videos that used to play on Feisty Firefox won't play on Gutsy. For example the videos on the online paper 'theage.com.au'. I get 'no video' message, and it hangs. I did all of the instructions in the following Ubuntu post here;

''Enabling Multimedia in Feisty (HOW-TO)'

Maybe I forgot something I did in Feisty.

---

### Post by dcstar on 2007-10-20
> **AkiraBergman said:**
> G'day Gutsy lovers,

I got Gutsy working on 386 by updating from Feisty. Download took long but it works nicely indeed. So thank you very much Ubuntu community. By the way, the update package asks for the CD at some stage but it does not use it, as far as I can see. Seems to be a bug.

Some videos that used to play on Feisty Firefox won't play on Gutsy. For example the videos on the online paper 'theage.com.au'. I get 'no video' message, and it hangs. I did all of the instructions in the following Ubuntu post here;

''Enabling Multimedia in Feisty (HOW-TO)'

Maybe I forgot something I did in Feisty.

Here is a small "HOWTO" I have used to get some streaming content working in Firefox:

[LIST=1]
[*]Remove the **totem-mozilla** package
[*]Install the **mozplugger** package
[*]Shut down and then restart Firefox
[*]Load sites that didn't work in Firefox, Totem should start and prompt you to install any required codecs
[*]Install all necessary codecs - content should now play
[*]If you want multimedia to play in the Browser - then reinstall totem-mozilla plugin and remove mozplugger
[/LIST]
Totem is now smart enough to know what is missing and then offer the solution to you, unfortunately the browser plugin will only work with what codec is already installed.

---

### Post by mcmakin50 on 2007-10-20
Thanks DCSTAR!  Your solution finally solved my video problem!  I could not figure out how o get it working.  Using Kubuntu 7.10, HP A250Y, Nvidia 128mb video card, 1gb mem, 2.4ghz P4 processor.

Thanks again for your help.

John McMakin :)

---

### Post by AkiraBergman on 2007-10-20
Thank you for your kind reply David.

Unfortunately I still have the same problem. Do you think the following link is still relevant to this?

[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)

I can't remember but the last time I may have done this. But that file is not availableanymore. So the command does not work.

---

