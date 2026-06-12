---
title: "Should I Install an Anti-Virus for WinXP on Virtual Box?"
date: 2012-07-07
forum: Any Other OS
---

### Post by duranl on 2012-07-07
I'm running Ubuntu 12.04, just started using Oracle Virtual Box and installed a Windows XP machine.  Should I install an anti-virus for the virtual Windows XP machine?

---

### Post by Habitual on 2012-07-07
Windows Defender is all I ever install in a Window VM.
Pretty sure that it's not even necessary, but I'd rather have it and not need it...

---

### Post by sudodus on 2012-07-07
> **Habitual said:**
> Windows Defender is all I ever install in a Window VM.
Pretty sure that it's not even necessary, but I'd rather have it and not need it...
I use the free version of Avast antivirus. I think the two programs address different threats. Windows in VirtualBox is as open to attacks as Windows installed directly into a physical machine.

---

### Post by SeijiSensei on 2012-07-07
> **sudodus said:**
> Windows in VirtualBox is as open to attacks and Windows installed directly into a physical machine.

That's only true with respect to malware that is installed as a result of client activities like browsing.  More traditional direct attacks against a Windows installation won't work because the VM is typically hidden behind the host OS over a NAT connection.  Those kind of direct attacks seem less common these days as more people have a router between their workstations and the Internet, and Windows now includes a firewall by default.  Nevertheless some people still connect their Windows machines directly to the Internet.

I would argue that the only reason to use Windows in a VM is to accomplish a task that cannot be done in Linux.  I rarely browse the Web from inside the VM. I use Firefox on the Linux host.  Typically I only use the VM to run applications that can only work in Windows, like tax-preparation software or something like Microsoft Access.  Reading your mail in the VM can be dicey if you can't keep yourself from clicking links in unsolicited emails. 

Really the best protection is to act intelligently.

---

