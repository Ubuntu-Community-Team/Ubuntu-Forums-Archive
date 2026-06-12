---
title: "Live CD can't boot with iBook G4? Please help..."
date: 2007-10-27
forum: Apple PPC Users
---

### Post by kiethrios on 2007-10-27
I search the forum but i can't get an answer...

is it too weird?

I burned a Live CD myself and boot with yaboot, then i press "return" key on my ibook.

the screen splash to with and return to black, the cd was read for a while then the machine seems die...

but i can't boot with the edgy, 6.10... i burned 7.10 as the same as i burnt the 7.10...

compatibility or sth else?:(

---

### Post by frog_pilot on 2007-10-27
Edgy desktop cd is working out of the box with my ibook G4 800 MHz, 640 MB, 32 MB Radeon. Feisty dektop comes up with a xserver error. When I add the line  ```
Option "NoInt10" "yes"
``` to the xorg.conf's driver-section, xserver is coming up and desktop cd works.

I assume, you know that you have to take the special version of the desktop cd for the ppc architecture... :)

---

### Post by shields on 2008-04-13
I finally got this working on the iBook I am using and posted the procedure on my blog.
[http://techtalk.shieldsgroup.com/2008/04/12/how-to-boot-an-ibook-g4-with-ubuntu/](http://techtalk.shieldsgroup.com/2008/04/12/how-to-boot-an-ibook-g4-with-ubuntu/)

Hope it helps.

---

### Post by stream303 on 2008-04-13
That is great stuff!

I always thought that just modprobe ide-core took care of all of that, and didn't realize that you can also try ide-disk and ide-cd

I got a feeling my early Hardy-alpha install which balked at the cd, could have used that.  That would be great stuff for the powerpcknownissues wiki..

Keeping an eye on your blog now!

---

### Post by poh on 2008-04-13
Maybe you can try 7.04 Feisty. I also use iBook G4, and it runs well by using live CD. Even installing on iBook, it runs well.

---

