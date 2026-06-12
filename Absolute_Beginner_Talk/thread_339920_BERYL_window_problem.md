---
title: "BERYL window problem"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by carlkhabbaz on 2007-01-16
Hi

first off, i'm a total Linux n00b. recently converted my faith to Linux, and I intend on keeping on.

Anyway, I managed to get everything working fine, I've been very happy for the past 2 months. Except for that BERYL thingie. I found a million how-tos, none of which yielded any results. However, I just finished following my nth how-to, I believe I'm very close to making it work, but when I start beryl-manager, something very strange happens:

1) No splash screen
2) all the windows lose the title-bar. it's impossible to move them or switch between them.

i fell back to gnome's window manager now and everything is back on track, but I really like the opacity thingie offered by Beryl :p

if it is of any help, I got the following output in the terminal where i ran beryl-manager:

[COLOR="Blue"]g@carl:~$ beryl-manager
g@carl:~$ Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
compiz: GLX_SGIX_fbconfig is missing
compiz: Failed to manage screen: 0
compiz: No manageable screens found on display :0.0
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
[/COLOR]
 

if it's any further help: I'm running a Fujitsu-Siemens M1425, with ATI Mobility Radeon 9700. I'm almost sure i installed the right drivers (since I have 1280x800 working fine. fglrx. should I use open-source?)

help! how can I get BERYL to work please please?

---

### Post by kilou on 2007-01-16
You probably already tried this but does your windows borders come back if you type **emerald --replace** in the terminal?

---

### Post by shof2k on 2007-01-16
> **carlkhabbaz said:**
> Hi

beryl: glXBindTexImageEXT is missing
compiz: GLX_SGIX_fbconfig is missing


I had a similar problem and I think the above lines are your cause.  You appear to be missing 2 features of beryl and compiz.  If you manage to get rid of these 2 lines, then beryl will work for you.  Unfortunately, I can't give much advice on how to do this.  Perhaps someone with a similar graphics set up will help you.

Some things to try:
1) Remove completely and reinstall beryl and compiz using synaptic.  Just in case the previous HOW TO's screwed something up.  (This is what happened to me)

2) Remove completely and reinstall the ATI driver for your card.

You can check which extensions you have by typing "glxinfo" into a terminal window.

I'm sorry I couldn't be much help, but I hope I've narrowed things down for you.

---

### Post by carlkhabbaz on 2007-01-16
ok so after posting my thread, I didn't expect such a quick reply (wow! Ubuntu community is just.. 5 stars.. Thanks a million for being there!), so I panicked a little and uninstalled BERYL and COMPIZ, hoping to regain a normal window-management. Didn't fix it. By sheer curiosity and intuition, I reinstalled them (through synaptics, of course), and oh Glory to the Mother of God, I now have all the wobbly effects AND the title-bar is back. Now I have no idea what happened deep down linux's dark bowels, but I'm somewhat happy I made it through.

Being an oldschool DOS user, seeing a problem magically disappearing isn't satisfying, so I'll keep on fiddling with Linux until I lose the partition :p

Again, thank you so much for the quick replies. You just gave me the nerve to go ahead and explore further :)

(eek.. i can almost see my million forthcoming threads banned :p)

---

