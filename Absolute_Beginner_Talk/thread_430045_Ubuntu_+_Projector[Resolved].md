---
title: "Ubuntu + Projector[Resolved]"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by l951b951 on 2007-05-01
I'm giving a presentation this week.  I've used Open Office Impress to create a slideshow on my Ubuntu Laptop.  When I take this machine in to the meeting room on Thursday, I'm going to plug it into the projector using the external monitor port (not sure of the tech name).  

Is there something I should be aware of, or will this be as easy as taking my windows machine in to do the presentation?  In its previous life, this laptop used FN+F4 to cycle through the LCD/External Monitors.  Is there an odd keystroke to put it on the projector in Ubuntu?

---

### Post by raja on 2007-05-01
I was unsure about this with my laptop too, but when I tried it out, it worked with the same key combination. So, I guess there is nothing special that you need to do. Still, it might be better to test it if possible before the big day!

---

### Post by l951b951 on 2007-05-03
I did a test run yesterday afternoon.  Everything worked fine except for 1 caveat.  

The boot screen displayed on the projector.  However, when X server began everything got weird.  My laptop resolution changed to 640x480 and would not change back.  Additionally, at that resolution the projector on displayed 3/4 of the actual screen.  I shut down, unpluged the display cable and rebooted.  It came up in my normal resolution.  I then hotplugged the projector cable.  Everything worked perfectly.  

So to wrap up my experience (may not be typical)

Compaq Evo N610 notebook with projector
Must hotplug projector after loading X.
Function + F4 doesn't change which display is being used.

---

