---
title: "Graphical boot screen"
date: 2012-03-14
forum: Apple Hardware Users
---

### Post by rsavage on 2012-03-14
Anybody got the graphical boot screen fully working on PowerPC?  I'm not talking the text splash screen, but the fancy one.  
 
I've been playing around with KMS with my radeon card and one of the consequences is that I now get the graphical splash screen.  However, the colours are all screwed up with the splash screen, particularly on shutdown.  It is acceptable under lucid (blue background instead of purple), but under 12.04 it is awful.
 
So I was wondering what the nouveau people who use KMS have been getting?  
 
I think it maybe just the radeondrmfb framebuffer is set to 8 bit depth?  Trouble is, I can't figure out how to alter this.  I'm hoping it is not an endian issue. Can't find any powerpc bugs raised against plymouth.

---

