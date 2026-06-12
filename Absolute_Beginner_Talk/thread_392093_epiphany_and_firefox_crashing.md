---
title: "epiphany and firefox crashing"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-03-24
lately both epiphany and firefox have been crashing....

epiphany when i have several tabs up always crashes... sometimes even when only one tab is open...

firefox as soon as whatever url I type in comes up, crashes.

opera is open and running with no problems....

any idea about what is going on?


thanks

robi

---

### Post by jordanmthomas on 2007-03-24
Try running firefox or epiphany from a terminal and see what errors they output when they die (if any).

---

### Post by beanco on 2007-03-24
this is what I got running them through terminal

(epiphany:7553): libgnomevfs-WARNING **: Failed to create service browser: Bad s tate


firefox was fine.. it opened to the default page I have set but when I typed in this url

[www.t-online.hu](www.t-online.hu) it died...

that's the same as the epihpany one...

so I assume it is the site in question that is causing problems....

robi

---

### Post by jordanmthomas on 2007-03-24
Well, your error was just a warning.  So it's not what cause it to crash.  

The site worked fine for me.  It was ugly, but it loaded up fine.  Have you installed the flash plugin?  It might be part of your trouble.  (Just speculating though)

---

### Post by beanco on 2007-03-24
as far as I know I have installed it... but run me through the steps of doing so and I will

thanks

robi

---

### Post by tommcd on 2007-03-24
> **beanco said:**
> lately both epiphany and firefox have been crashing....

epiphany when i have several tabs up always crashes... sometimes even when only one tab is open...

firefox as soon as whatever url I type in comes up, crashes.

opera is open and running with no problems....

any idea about what is going on?


thanks

robi

You could try creating a new firefox profile. Your profile may be corrupt. Just rename .mozilla in your /home directory to .mozilla.bak <mv .movilla .mozilla.bak>, and launch firefox. It will create a new default profile. If the new profile runs ok you can copy your bookmarks over from .mozilla.bak to the new .mozilla directory.

---

### Post by x1a4 on 2007-03-24
Hi,

I'm willing to bet the farm it's a Flash problem.  See if your browsers crash when you visit pages without flash. If not, navigate to pages with flash and see if they crash.  If they do, install/reinstall the latest version of the Flash plug-in.

---

