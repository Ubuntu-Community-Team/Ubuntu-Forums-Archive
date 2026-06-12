---
title: "Conflicting Software?"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Rossg on 2008-02-01
I've been trying to install 'Audacity' from the Add/Remove menu but every time I do I keep getting this message 

'[B]This application conflicts with other installed software. To install 'audacity' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.[/B]'

I went into the 'Synaptic Package Manager' like the error message said to but when I found 'Audacity' it wasn't installed and when I tried to install it I got this message 

[B]audacity:
 Depends: libid3tag0 (>=0.15.1b) but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable[/B]

 Also it's not only Audacity that's doing this, most of the software I've been trying to download is telling me that its conflicting with other software.

I've been using Linux for about a week now and I don't know what I would do to fix this.If anyone else has had this problem or knows how to fix it, I would really appreciate some help.

---

### Post by taurus on 2008-02-01
Why you are still in synaptic, go into Settings -> Repositories and make sure you have a check mark for all lines except the last one, Source code, and Cdrom in the window below.  Close it and press Refresh.  Now, see if you can install it again this time.

---

### Post by JoshuaRL on 2008-02-01
Go into Settings->Administration->Software Sources and make sure everything is checked.  Then run Update Manager.  After you get done with that, see if you can install audacity.

---

### Post by Rossg on 2008-02-02
HA!It worked!Thanks a lot guys, you just made my whole Ubuntu experience much better!:D

---

