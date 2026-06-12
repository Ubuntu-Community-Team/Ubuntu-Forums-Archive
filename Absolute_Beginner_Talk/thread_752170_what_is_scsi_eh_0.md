---
title: "what is scsi_eh_0"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by Kerry_W on 2008-04-11
i just ran TOP in the console and i've got 12 scsi_eh_ commands running.
what the heck is it and do i really need 12 instances of it?  
how can i cut down the number of these running?

Thanks.
Kerry

---

### Post by pedro_orange on 2008-04-11
What did you run in console?

scsi_eh is SCSI error handling threads I believe. 
I presume this is because you have SCSI drives in your machine. Don't know why you have 12.

---

### Post by 3rdalbum on 2008-04-11
I have eight running and I don't have a SCSI controller. I think optical burners emulate SCSI, but I've only got two burners, not eight :-)

My old computer also ran a few of those processes.

In any case, *ps* says they're using 0.0% CPU time or memory, so I don't worry about them.

---

