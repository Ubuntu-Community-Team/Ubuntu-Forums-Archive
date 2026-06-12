---
title: "Chopped windows"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by gheywood on 2007-09-22
Hello, 

I have noticed that several windows have the bottom chopped off them. I can kind of see that there is something else, but there is no way to get to it that I can work out. As an example, if you run VLC, go to File, then Open Capture device, then click "Settings". 

Even in 1024x768, I can't see most of the Miscallenous section..

Cheers

---

### Post by pmoseley on 2007-09-22
If you're using an LCD screen go into the monitor options and select 'auto-correct picture' or something similar. This may help...

If you've got a CRT monitor try altering the settings on that.

Alternatively, it may be something to do with the X-Windows configuration. I had to manually edit /etc/X11/xorg.conf on my laptop and main pc to correct the same problem. I found it particularly annoying when running in console.

---

### Post by gheywood on 2007-10-12
Thanks. When you talk about editing xorg.conf, what should I be looking for? A resolution setting?

Cheers

---

### Post by RomeReactor on 2007-10-12
Hi. I've seen that problem in VLC and sometimes aMule; I think it's an application-specific problem. Does this happen with other programs besides VLC?

---

