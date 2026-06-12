---
title: "PCI error with ibook g3"
date: 2007-06-07
forum: Apple PPC Users
---

### Post by TCE on 2007-06-07
I am a new user of ubuntu and was wondering why I get this error with my ibook g3 with Feisty.  The error comes on just before the boot image appears and states Cannot Allocate resource region 0 of Device 0001.10.19.00.  It boots fine after that and i seem to have no problems, but was wondering what this means.  Is there anyway i can fix the problem?  If its a common problem of ppc users?  Can i somehow disable this warning if does not mean anything. any help would be grateful.

---

### Post by reh4c on 2007-06-08
Hello.  I've noticed the same message on my iBook G4, but don't know what it means or how to fix it.  Sorry that I can't help.  Hopefully, someone more knowledgable can fill us in.

---

### Post by DaDave on 2007-06-08
PCI is 'peripheral component interconnect'. It usually specifies a  bus for attaching peripheral devices to the motherboard. Do you have any expansion cards installed? Have you removed anything? All your hardware & external devices working?

---

### Post by TCE on 2007-06-08
yes all my externals are working.  The only thing i have ever done to it was add a 512mb stick of ram.  I do have a usb hub hook up to it. I am not sure but whatever distro besides mac osx i install i get this error.

---

### Post by reh4c on 2007-06-08
Nothing external hooked up to my iBook G4.  I'll track down the warning/error message (actually two of them) to make sure they match the one posted by TCE.  It may be a good idea to file a bug report in Malone...if it hasn't been done already.

---

### Post by TCE on 2007-10-24
I finally found what this error (0001.10.19.0) means.  It seems to be an bug caused by openfirmware that disables your usb-ohci.  I tried compiling a newer kernel to enable it in menuconfig, but still see this error even with the newer kernel booting up.  I really need some help to fix this.  If anybody knows about this problem and how to fix it I would really appreciate it.  Running out of ideas.

---

