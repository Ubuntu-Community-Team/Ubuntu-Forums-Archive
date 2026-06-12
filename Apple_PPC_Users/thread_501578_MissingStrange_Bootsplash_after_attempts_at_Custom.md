---
title: "Missing/Strange Bootsplash after attempts at Customization"
date: 2007-07-15
forum: Apple PPC Users
---

### Post by 0graham0 on 2007-07-15
Hey All,

So I was messing around with my bootsplash, It was loading in 1024 x768, which meant it wasn't centered on the 1440 x 900 screen (i know...i know...slight OCD). It was also showing up in funky colors with noise all over the place. I changed usplash.conf to load in 1440 x 900 (which I now changed back to 1024 x 768). I also edited yaboot.conf to have Mac OS X as the default os and removed quiet from "quiet splash. 

On top of all that I tried to install some custom screens, during which I may have overwritten the default ubuntu splash '.so' file?

Anyhow, this process also involved many "sudo ybin" and "sudo dpkg-reconfigure" which leave me now with no boot splash on shutdown, giving me the message "No image available for 1024 x 768" On startup I get a really funky bootsplash that has shapes and colors and strings of numbers, but also a loading bar, and a space for boot messages. I seem to remember reading a post somewhere that this is the bootsplash for beta/alpha releases/early builds?

Any suggestions for how to get out of this mess? any help is greatly appreciated...

---

