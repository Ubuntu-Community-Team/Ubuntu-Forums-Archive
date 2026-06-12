---
title: "Hibernate or suspend creates a Network Connection failure"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by cybertron3000 on 2008-02-24
I've read numerous similar complaints, but no one seemed to offer any concrete solutions.  My wired network connection always gets disabled after coming from a hibernate or suspend mode.  Any solutions to prevent this irritation?  

I *can* fix it with turning the network connection on/off with a right click on the icon each time - but why should I have to do this?

---

### Post by hugmenot on 2008-02-24
Might try (not) unloading your network card driver in /etc/default/acpi-support during suspend.

```
# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""
```

Put into whitelist first.

---

### Post by cybertron3000 on 2008-02-25
I did manage to find a code line in the forums that seems to have solved this problem:

For those with similar issues, this works for me.  Go to Terminal and enter:

sudo /etc/init.d/networking restart

Hope this solves other similar problems out there.  I had the same issue with Windows before, but there were no Terminal code solutions there.:KS

---

### Post by hugmenot on 2008-02-25
But this is worse than right-clicking the applet, isn't it? More typing work.
Why don't you try to white-list your driver? For me this led to smooth reconnection after resuming.

---

### Post by fergalm on 2008-02-25
I'm running kubuntu 3.5.8 on a Dell Latitude Notebook and a Broadcom wireless card. I had the same problem on resume from Hibernate, but adding the following line to /etc/default/acpi-support seems to have fixed the problem
MODULES="network wireless"

---

### Post by hugmenot on 2008-02-26
Are your modules really called "network" and "wireless"?

---

