---
title: "'apt-get netpbm' lacks some required programs"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by bsenftner on 2008-01-03
Hey Ubuntu Gurus,

I'm new to Ubuntu, but have been a Unix/Linux user since (shudder) the 70's...

I've got a new box, which I've installed Ubuntu and a boatload of programs via apt-get.
However, being a graphics guy, as I get to work I see that at least two of the netpbm utilities that I use constantly are not present in the netpbm package that apt-get installed. The programs pamscale and pamcomp are missing... 

What is the correct procedure here, community wise? Should I just download the source tarball of netpbm from SourceForge, build my own and go, or is there some procedure the community approves whereby these missing programs are added to the package?

-Bsenftner

---

### Post by taurus on 2008-01-03
Look in System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and make sure that all repos are enable with a check mark in front of all of them except the last line, Source code and CDROM at the bottom window.  Close it and click Refresh.  Now, see if you can install whatever you planned to install before.

---

### Post by carrett on 2008-01-03
Yeah, it looks like it's not in any other packages (I did a quick search of packages.ubuntu.com and packages.debian.org to see if Debian had it). Maybe these tools have been encompassed in some of the tools provided in netpbm? I'd check out the executables in that package:

```
dpkg -L netpbm|grep bin
```


and read up some manpages see if you get any luck there. Barring that, you might want to have a look at imagemagick. Sorry I can't be more helpful.

---

