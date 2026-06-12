---
title: "noob install problem with gutsy"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Davi0 on 2007-10-18
1st time user, system hangs on install at 82%. Window is at checking APT. Anyone run into this ?

---

### Post by LowSky on 2007-10-18
Did you check  the iso before burining it to make sure the data was fine?
what Speed did you burn the Live CD at? The Slower the Better.

---

### Post by Sef on 2007-10-18
> Did you check the iso before burining it to make sure the data was fine?

Check the iso = [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM")

> what Speed did you burn the Live CD at? The Slower the Better.

Burn at 4x or less.

---

### Post by Davi0 on 2007-10-18
Yes I checked the cd via the boot menu funtion and it passed.

---

### Post by samjh on 2007-10-18
I have the same problem.

Checked the md5 sum and the CD integrity as well.  All is fine, but installation stalls at 82% as it says "configuring apt" and underneath is the message "scanning mirrors".

I'm typing this from the live disk, trying to install for the second time.  I thought perhaps there was a network problem, but my internet connection is fine.

[EDIT]

OK, I've hit the 82% mark and the installer has stalled again.

There are no error messages.  I've even tried running ubiquity via terminal, but nothing there either.

---

### Post by Davi0 on 2007-10-18
Yep, exactly same  message as me.

---

### Post by Davi0 on 2007-10-18
bump

---

### Post by samjh on 2007-10-18
I've found a dirty work-around to the problem.

When it stalls, right-click on the Network Manager system tray icon on the right-hand side of the top panel, and untick "Enable Networking".  This will disable the network, and the installer will then skip to the next part of the installation after displaying an error message.

After the installation, you will need to go to System -> Administration -> Software Sources, and set up your repository settings.

I think with all the flurry just after this new release, the servers are getting overloaded.  When I did a quick diagnostic of the repo servers, some of them were not returning any responses.

---

### Post by Davi0 on 2007-10-18
Thanks, will try again tomorrow (or use the above "trick"

---

### Post by maliath on 2007-10-18
Same problem here ... I'm in livecd now ...

If I just let this sit for a really long time will it eventually resolve itself and configure apt properly? Or is it permanently hung with already misconfigured apt? Thx.

---

### Post by n00buntu on 2007-10-18
I had the same problem, and what I did was to pull out my network cable.  Then it installed quickly after that.

---

