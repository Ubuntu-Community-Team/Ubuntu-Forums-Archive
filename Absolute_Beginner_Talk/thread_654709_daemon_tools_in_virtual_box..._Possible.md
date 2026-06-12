---
title: "daemon tools in virtual box... Possible?"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Colemanvt on 2007-12-31
So I'm running a windows xp virtual box. trying to install adobe flash cs3 from a cd image. Of course you can mount an image in the drive for the virtual box but for some reason there is a type of copy protection that must be emulated for the image to install correctly.  This can be done in daemon tools. daemon tools installs fine in virtual box but gives a "this image format cannot be read", which is a false message, when i try to mount the image. (note it's an .iso) 

Anyone have any ideas?

EDIT: [Problem Solved]

Ok got it fixed apparently what I was doing daemon tools didn't like I was trying to string the iso from my share folder on my host. I just figured it would work that way but I suppose daemon tools thinks that I'm trying to run an image off of a network with it deems sub par in functionality.

So in short if you have this problem just make sure that the image is in your guest system partition

---

