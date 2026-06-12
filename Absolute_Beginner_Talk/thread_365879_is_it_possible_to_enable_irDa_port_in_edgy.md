---
title: "is it possible to enable irDa port in edgy?"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-02-20
Hi i have an IrDa port and i would like to enable it as it handy to transfer files to my cell phone that has this technology. my cell doesn't have gprs or bluetooth and i have done this from another old notebook that i had. but that had microshaft on it and i had to manually enable that too.

---

### Post by Jussi Kukkonen on 2007-02-20
Enabling the port is just the beginning (in fact it might just work straight out of the box) -- the problem is the communication with the phone as the software and protocols are usually proprietary and secret. So, first you should find out if file transfer between linux and your phone is possible at all , Google may help.

 ***apt-cache search irda*** will list all packages that have anything to do with irda. *obexftp* is your best bet, if your phone supports OBEX (be warned that many manufacturers advertize OBEX and only support a fraction of the standard features)

---

### Post by rapattack1 on 2007-02-20
here is what the terminal said when i typed what you said:
apt-cache search irda
irda-utils - IrDA management and handling utilities
toshset - Access much of the Toshiba laptop hardware interface
gsm-utils - GSM mobile phone access applications
ircp - Utility for "beaming" files via IRDA
libgsmme1c2a - GSM mobile phone access library
obexftp - file transfer utility for devices that use the OBEX protocol
opensync-plugin-irmc - IrMC plugin for opensync
ussp-push - Client for OBEX PUSH

looks like i have to get some things? i dunno i am still pretty new to reading this linux stuff.
can't seem to find anything in google but maybe i don't have the right search words.
will give it a try anyway and see what happens.

---

### Post by rapattack1 on 2007-02-20
i just remembered i also bought a sim card reader a few months ago that was very problematic when i installed it with microshaft. i wonder if i can use that with laptop too.

---

### Post by rapattack1 on 2007-03-29
i downloaded and installed all the things mentioned after doing that search but i guess there is more to do before the irda works? it took me thins long to get to this. i hope i did the right thing. can anyone tell me what to do next?

---

