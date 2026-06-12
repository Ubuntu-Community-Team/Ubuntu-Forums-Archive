---
title: "Installing OSX in Fiesty through KVM..."
date: 2007-05-27
forum: Apple Intel Users
---

### Post by kcimpulse on 2007-05-27
Hey everyone i was just wondierng if anyone could help me out or point me in the right direction i am trying to install OSX86 in Fiesty through KVM, with qemu but with no luck. I have read throgh the guides for xp and made the modifications but it still wont work.  It gets like a memory dump error when i try it. Any help would be appreacheated... Thanks in advance...

---

### Post by Asgaard on 2007-05-28
Is your processor from Intel?
AFAIK, kvm on Intels is currently broken if whatever you're trying to boot uses real mode code (and apparently most OS graphical installers use it including Ubuntu).

---

### Post by kcimpulse on 2007-05-30
yes my proc is an intel core 2 duo, is there any information on maybe a kernel update or a fix. I know just about enough to get me in trouble so if you could point me in the right direction that would be a great help...

---

### Post by kcimpulse on 2007-05-30
Just found this on the KVM site, any gurus out there have any ideas how to fix this for osx installation... or if not the reason i am installing though kvm is because i coudlnt get it to install nativly with my computer and dual boot with ubuntu because when it would load it gave me the awsome apple debug erroe of bad computer icon with x in it...

[http://kvm.qumranet.com/kvmwiki/Intel_Real_Mode_Emulation_Problems](http://kvm.qumranet.com/kvmwiki/Intel_Real_Mode_Emulation_Problems)

---

