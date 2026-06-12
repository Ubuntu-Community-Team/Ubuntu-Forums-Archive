---
title: "Wine on Ubuntu 8.04 FreeNX server with Mac OS X 10.3 NX client"
date: 2009-04-01
forum: Apple Hardware Users
---

### Post by optimaco on 2009-04-01
Hello,
We have Ubuntu 8.04 running with FreeNX server on our 'remote desktop server' linux machine.
We can connect to the Ubuntu machine with the NoMachine NxClient from Windows, Linux and Mac OS 10.3, 10.4 and 10.5.
We also have Wine 1.0 installed on the Ubuntu machine, and we run a variety of Windows applications and utilities in the remote desktops from clients on all 3 systems (Windows, Linux, Mac)... except with Mac OS X 10.3.
In the case of the Mac OS X 10.3 NxClient, fonts are not rendered correctly (I would even say not at all) for the applications running under Wine. Menus, buttons, etc. are all empty, except for inactive buttons where some grayed out text is rendered. The Wine configuration panel itself is not rendering any text (titles, tabs, menu, buttons, etc. are all empty).
I believe this must have to do with some fonts used by Wine or the FreeNx server that must be rendered locally on the X11 of the client machine, or served by the Ubuntu machine, but I have no clue on how I can fix this.
I have included a small screenshot of the badly behaving Wine config panel to illustrate the point.
The whole environment is to be deployed for a business application to be accessible via remote desktop and we have at least 15 machines with Mac OS X 10.3, so this is quite critical.
Any comments, suggestions ... and of course solutions will be greatly appreciated.

---

### Post by cyberdork33 on 2009-04-01
hi
this forum is really focused on supporting Ubuntu running on Apple hardware. So this may not be the right forum to ask in. You do have a unique situation I think, and maybe someone here has ran into it, but I would just not rely on this one post to get your answer is all.

---

### Post by optimaco on 2009-05-19
Well, I found a solution to my problem via the Wine forum, which is also described here:
[http://wiki.winehq.org/FAQ#head-3b18ce54edb7ea108c8f08945bc52812c4e3ef71](http://wiki.winehq.org/FAQ#head-3b18ce54edb7ea108c8f08945bc52812c4e3ef71)
We now have successfully setup a system allowing us to run Wine inside a virtual Linux Desktop in a mixed environment of Mac OS 10.3, 10.4 and 10.5, and some Windows machines...

---

