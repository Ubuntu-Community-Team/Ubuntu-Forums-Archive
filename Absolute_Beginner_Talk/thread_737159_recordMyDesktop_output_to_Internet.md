---
title: "recordMyDesktop output to Internet?"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Nutopia on 2008-03-27
Hi,

I want to use recordMyDesktop and put the resulting video on my website. I have to make a 'training' video of sorts. Unfortunately, I don't know how to convert the output into something that can be put online (in fairly good quality.)

Can anyone help?

---

### Post by northern lights on 2008-03-27
As most distros Ubuntu ships with "mencoder", check out [http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide]("http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide") and [http://www.mplayerhq.hu/DOCS/HTML/en/mencoder.html]("http://www.mplayerhq.hu/DOCS/HTML/en/mencoder.html")

---

### Post by Nutopia on 2008-03-27
Thanks! I ran this command:

```
mencoder <INPUT_FILE_NAME.ogg> -ovc lavc -oac lavc -ffourcc DX50 -o <OUTPUT_FILE_NAME.avi>
```

And it worked like a charm.

---

### Post by Nutopia on 2008-04-03
Hi again.

So this encoded my .ogg to .avi -  everything is working fine on Ubuntu, but my friends on Windows can't play the video. Does anyone know of any reason? I've had a few people try it and none of them were able to get it to run. I've tried viewing it in WinAmp and QuickTime and neither of them will work. 

Any advice?

Thanks!

---

