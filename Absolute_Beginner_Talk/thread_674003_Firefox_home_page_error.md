---
title: "Firefox home page error"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by linuxforrealpeople on 2008-01-21
A minor quibble.
When I fire up Ubuntu I have Firefox startup automatically. Each time it errors with:

Server not found
                         
Firefox can't find the server at [www.%u.com](www.%u.com).

All I have to do to resolve this is hit the Home icon and my homepage tabs are displayed.

Any ideas folks?
Thanks for reading this,

---

### Post by markyb86 on 2008-01-21
what command are you using to auto-start firefox?

---

### Post by linuxforrealpeople on 2008-01-27
firefox %u

Thanks

---

### Post by sports fan Matt on 2008-01-27
how do you start it automatically? and what is that link you posted?  It couldnt find it for me either

---

### Post by linuxforrealpeople on 2008-01-27
Um, this is the default setup for Firefox as per the original install.........

---

### Post by markyb86 on 2008-01-27
get rid of the %u

---

### Post by seventhc on 2008-01-27
If you are doing this from the terminal just use firefox, if this is in the properties box from the panel then that is what it should be.
It doesn't work in a terminal. If it's the launcher on the panel try removing it and then add it back. Or just make it be firefox with nothing else added.

---

### Post by linuxforrealpeople on 2008-01-28
That did it. Thanks.

---

### Post by cheike on 2008-01-30
This same problem will occur if you try to add the firefox icon to the stacks applet in awn.  Simply right click and slect properties.  From there remove the %u from the command line and you should be all set

---

