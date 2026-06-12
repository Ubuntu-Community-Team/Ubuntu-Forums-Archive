---
title: "how do i install xdmcp?"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by stevieb on 2006-11-10
when i run ltspcfg, xdmcp shows up as not installed.  how do i get this? it's not listed in the repositories.

thanks,
-steve

---

### Post by JayTee on 2006-11-10
It's installed by default. Go to System | Administration | Login Window and click on the Remote tab. There is a button on the lower right to configure XDMCP. You probably need to check the "Honor indirect requests" checkbox.

---

### Post by stevieb on 2006-11-10
i've done this already; it is not installed by default.  otherwise it would show up as "installed," right?

-steve

---

### Post by stevieb on 2006-11-11
is it in the repositories under a different name?

---

### Post by stevieb on 2006-11-11
no solution yet, but [here's]("https://launchpad.net/distros/ubuntu/+source/gdm/+bug/27885") some more info:

```
hi, the ltsp 4.1 package ended up through a packaging error in main, it should
never ever be in the supported set, the ubuntu ltsp doesnt use xdmcp or other
insecure transport mechanisms ... i will have to talk to jim about what to do...
we never planned to support 4.1 in any of our ubuntu releases, i'd suggest to
use the ubuntu implementation (the ltsp-server-standalone package) and follow
the ThinClientHowto on the wiki if its urgent to get it to work.
```

so much for "xdmcp is installed by default"](*,)

---

### Post by JayTee on 2006-11-11
That's odd. I never had to install it. It was just there. I only found it when I started messing with VNC and wanted to change the port it listened on. I ended up moving to X11vnc instead as it supported the x-server session 0 with Beryl/XGL. Maybe an earlier install of vncserver put it on my system but I'm sure I didn't type anything like sudo apt-get xdmcp.

---

