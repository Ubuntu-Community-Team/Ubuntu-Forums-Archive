---
title: "Hardware changes???"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by Razorback on 2006-01-16
Will changing hardware after ubuntu is installed cause problems?  I am wanting to try a different modem from the one I have in my pc now.  My present modem won't work and I have seen others having problems with the same modem.  Also, I am wanting to try another video card.  Any input would be appreciated. Thanks.

---

### Post by Sef on 2006-01-16
What you want to get is new hardware that is compatible with linux, not all new hardware is.

For modems: [http://www.linmodems.org]("http://www.linmodems.org")

NVidia has better support for Linux than ATI.  Not sure about other video cards.

---

### Post by Razorback on 2006-01-16
Thanks for the reply.  I really am wanting to know if you can add and remove hardware after an install without having to change settings first or will ubuntu alter the settings automatically for the new hardware.  I do realize some things will have to be tweaked.

---

### Post by Sef on 2006-01-16
If the hardware is Linux compatible, Ubuntu should recognize it and start up.  And yes, likely there may be tweaking involved.

---

### Post by irv on 2006-01-28
I would like to add one question to the forum. Can you force Ubuntu Linux to probe for new hardware if it doesn't see the change made? I changed monitors and it does not see the change. I had a Gateway monitor and changed to a Dell Trinitron with higher resolution, but the /etc/X11$/xorg.conf shows: 
"Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
This is why I am asking this question.
Thanks

---

