---
title: "Getting SANE Networked Scanner to Show Up Inside OSX"
date: 2009-01-08
forum: Apple Hardware Users
---

### Post by rshnike on 2009-01-08
Hey everybody.

Everyone on this forum is always such a great help, figured I'd try my luck at another question.

I have an "old" box running Ubuntu Server 8.10. I've reformatted a bunch of times already to get everything just right, and I think I've finally gotten it set up pretty much as I'd like it.

I have some last bits of loose ends that I'm trying to take care of. I just finally was able to get my scanner working without needing sudo, so I can now scanimage -L without root privileges (an HP Scanjet 5590, and in case anyone is still looking for the fix for the root problem it took me a little bit to find it but it ended up being changing the subsystem mode for USB, PM me if you'd like a link or instructions and I'll post it in this topic).

I'd love to know however if there was some way that I could have the scanner show up so that the rest of my computers (all macs) could use it within the OS. I do already have the CGI script from here:

[http://scannerserver.online02.com/](http://scannerserver.online02.com/)

set up, and it's a very nice script if I don't say so myself, but native support inside Leopard would be great just like I have it from CUPS for my 2 printers and my hard drives using Avahi+Netatalk (which I configured using directions found online and is already working perfectly).

So yeah, if anyone has any suggestions as to how I could get the scanners to show up for example in Image Capture and Photoshop etc. or if you need more info I'd really appreciate it.

Also, on a side note that may deserve its own post, as I keep adding services, how does everyone keep track of all the host names and ports that they need to remember on their own network? There has to be a better way than what I did which was just to make a numbers document and remember that every time I added CUPS, SANE, or another service to type it into the document so I'd remember which port to access on. I mean just creating a bookmark in all the browsers I guess could work but is there some way to just have that information in one spot on the server for example that the other computers could just look up what port and what host is needed?

---

