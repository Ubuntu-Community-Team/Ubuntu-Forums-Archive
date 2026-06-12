---
title: "HELP! Unable to get past Ubuntu splash screen"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by David Floyd on 2007-08-03
Using Feisty.

I was trying to install IES4Linux - I don't know what I did wrong but I decided to reboot.

Now, after the Ubuntu splash screen with the progress bar - when it comes to the end of that an error message comes up:-

> Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix the problem.
This is followed by a tick box "View details (~/.xsessions-errors file)"
And on ticking this I get the following in a text box:
> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:O.Xservers" -h "" -l ":O" "david"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: Permission denied

Can some-one please advise me what to do next so that I can get my system up and running again.

Thanks,
David

---

### Post by atomkarinca on 2007-08-03
you can reboot your computer, start with failsafe mode and try re-installing.

---

### Post by David Floyd on 2007-08-03
> **atomkarinca said:**
> you can reboot your computer, start with failsafe mode and try re-installing.

Before your reply I had tried with failsafe mode, but after all the boot messages etc had flown by I was left with the prompt and I didn't know what then to do :(

When you say re-install, can you say precisely what I do at the prompt, please?

Do you mean re-stall from the CD? - won't I loose all my settings and programs etc then.

Thanks,
David

---

### Post by FleetAdmiral74 on 2007-08-03
Do you have a separate home directory? If you do, you won't lose your settings, but you will have to reinstall the programs, I think thats  how it works

---

### Post by David Floyd on 2007-08-03
> **FleetAdmiral74 said:**
> Do you have a separate home directory? If you do, you won't lose your settings, but you will have to reinstall the programs, I think thats  how it works

Thanks.  It's 20 past midnight here in the UK, so I'll try this in the morning (in about 9 hours time)

David

---

