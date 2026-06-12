---
title: "Dapper 6.06 LTS Upgrade"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by Daniel McLaws on 2006-05-27
I just upgraded from Breezy 5.10 to Dapper 6.06 using the automatic script after typing in gksudo "update e-manager -d".

During the boot up now I get a "PCMCIA Services [failed]" message.

Can anybody tell me what that means? :-| I didn't get that before when I booted up with Breezy 5.10.

---

### Post by mostwanted on 2006-05-27
I don't think it's important. Same thing happened to me after upgrading but I never experienced anything out of the ordinary.

---

### Post by Biltong (Dee) on 2006-05-27
I also get this. As everything seems fine I just ignore it.

---

### Post by dabear on 2006-05-27
Desktop or laptop PC? PCMCIA-slots are usually only vailable in laptops. PCI, PCI-express and AGP is used on desktop PCs. If your PC is a desktop machine, you've got nothing to worry about.

---

### Post by _simon_ on 2006-05-27
if you don't need it then:

```
 sudo sysv-rc-conf 
```

and simply disable it.

---

### Post by Daniel McLaws on 2006-05-27
[QUOTE=dabear]Desktop or laptop PC? PCMCIA-slots are usually only vailable in laptops. PCI, PCI-express and AGP is used on desktop PCs. If your PC is a desktop machine, you've got nothing to worry about.[/QUOTE]

It is a desktop, so I suppose it doesn't matter.

---

### Post by Sef on 2006-05-27
> It is a desktop, so I suppose it doesn't matter.

Not unless you're planning to convert your desktop into your laptop. :lol:

---

### Post by Daniel McLaws on 2006-05-27
[QUOTE=_simon_]if you don't need it then:

```
 sudo sysv-rc-conf 
```

and simply disable it.[/QUOTE]

Tried it and got:
"sudo: sysv-rc-conf: command not found"

Is there a space I'm missing here ?

---

### Post by confused57 on 2006-05-27
[QUOTE=Daniel McLaws]Tried it and got:
"sudo: sysv-rc-conf: command not found"

Is there a space I'm missing here ?[/QUOTE]

You'll need to install it first using Synaptic Package Manager..

---

### Post by Daniel McLaws on 2006-05-28
I installed sysvconfig from synaptic, rebooted, and it still says the sysv command is not found, even when I tried "sysv --help".

Not a big deal though.

---

