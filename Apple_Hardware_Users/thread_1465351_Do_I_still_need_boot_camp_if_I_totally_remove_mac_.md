---
title: "Do I still need boot camp if I totally remove mac os?"
date: 2010-04-29
forum: Apple Hardware Users
---

### Post by northfly on 2010-04-29
Thanks.

---

### Post by zeroti on 2010-04-29
I don't think so. but if you also want to boot windows, i'm not sure what configuration would be best. I don't really have any experience in dual-booting.

---

### Post by tricomp on 2010-04-29
I am no authority on this, but in my experience the answer is no. Boot camp consists of two parts - a partitioning utility and windows drivers collection, neither of which you need. I have installed Ubuntu on a Mac Pro (which had OS X still installed) by using GParted to change a mac partition to an ext3 partition and then installed Ubuntu all without using Bootcamp. See this for a better explanation of what Boot Camp does:
[http://en.wikipedia.org/wiki/Boot_Camp_%28software%29]("http://en.wikipedia.org/wiki/Boot_Camp_%28software%29")
If you have installed Linux and the Mac OS side by side you have probably used rEFit to do so. They have an excellent discussion which includes this topic:
[http://refit.sourceforge.net/myths/](http://refit.sourceforge.net/myths/)
The official Ubuntu MacTel documentation may also be helpful:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)
These sources seem to support my own experience, and are certainly a lot more authoritative than I am. I am only hesitant because I actually haven't done exactly what you propose myself. I do think the advice in the Mactel article about keeping at least a minimal Mac partition around for firmware updates is worth considering.

---

