---
title: "HOW?: Installing Fonts Globally"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by E.T.Smith on 2006-12-22
After having first installed Ub' a few weeks ago, I'm finally getting around to reloading the TTF fonts which I had accumulated over the life of my Fedora setup. Since I prefer to have the fonts available to all applications in one shot, I have in the past always done this globally, installing directly to the Core X system via the terminal. This is the method I used under Fedora, copied verbatim from the guidebook:
Open a terminal, become root, enter the following
```
mkdir /usr/share/fonts/xsysfonts/
```
then
```
cp myxfonts/*.ttf/ usr/share/fonts/xsysfonts
```
"myfonts" being the folder in my home directory where the fonts have been downloaded to.
final steps:
```
cd /usr/share/fonts/xsysfonts
```
```
ttmkfdir > fonts.scale
```
```
mkfontdir
```
```
/usr/sbin/chkfontpath -a /usr/share/fonts/xsysfonts
```
After the fun and games of discovering that root is handled differently in Ub', and fixing the damage of the learning experience, I've found that the above method doesn't work anymore. So far, I can't get past the "cp myfonts/*.ttf..." step, since the terminal says the path doesn't exist. I have a variation or two to try to get past that, but I still suspect that further steps will fail as well. So ... anyone with advice on installing fonts globally? Preferabbly via some GUI method, as I'd rather avoid the command line entirely.

---

