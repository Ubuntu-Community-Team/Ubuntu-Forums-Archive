---
title: "Help me cut out a few modules"
date: 2008-03-08
forum: Arch and derivatives
---

### Post by PurposeOfReason on 2008-03-08
I know there is no way I need all of these but the problem is, I only know what a handful of them are full. Is there a guide that lists modules?

MODULES=(iwl3945 acpi-cpufreq cpufreq_powersave sky2 snd-mixer-oss snd-pcm-oss snd-hwdep snd-page-alloc snd-pcm snd-timer snd snd-hda-intel soundcore sony_laptop)  

Also, what is the netfs do?

---

### Post by K.Mandla on 2008-03-09
The best module help I usually found was in the kernel configuration.

Did that come up from the installation procedure, or from *hwdetect --show-modules*?

---

### Post by PurposeOfReason on 2008-03-09
You lost me there. What I posted was just from my /etc/rc.conf. I just want to know what each does. Is there a benefit to compiling them into the kernel, not as a module because the kernel just got updated so I have to do that anyways.

---

### Post by fwojciec on 2008-03-09
From the ones you posted:

iwl3945: wifi, I assume
sky2: ethernet
acpi-cpufreq cpufreq_powersave: powersave stuff
snd-mixer-oss snd-pcm-oss snd-hwdep snd-page-alloc snd-pcm snd-timer snd snd-hda-intel soundcore: your soundcard
sony_laptop: your laptop special keys and such.

In other words -- all of them are necessary.

---

### Post by K.Mandla on 2008-03-09
> **PurposeOfReason said:**
> You lost me there. What I posted was just from my /etc/rc.conf. I just want to know what each does. Is there a benefit to compiling them into the kernel, not as a module because the kernel just got updated so I have to do that anyways.
Sorry. If you recompile a kernel there are help pages that describe the module and the equipment it applies to. It's strange, but I'm having a hard time finding that same information with Google. :???:

I usually compiled mine into the kernel to avoid loading them at the start, but that's just me.

---

### Post by aeto on 2008-03-10
You're not autoloading so all of them are required even if one or more are dependent modules.

---

### Post by MisfitI38 on 2008-03-11
> **PurposeOfReason said:**
> I know there is no way I need all of these but the problem is, I only know what a handful of them are full. Is there a guide that lists modules?

MODULES=(iwl3945 acpi-cpufreq cpufreq_powersave sky2 snd-mixer-oss snd-pcm-oss snd-hwdep snd-page-alloc snd-pcm snd-timer snd snd-hda-intel soundcore sony_laptop)  

Also, what is the netfs do?

Those modules are put there during installation, from the results of hwdetect probing your machine. If MOD_AUTLOAD="yes", then you could  actually get rid of all of them, and they will be automatically loaded at bootup anyway. 
If hwdetect failed to detect a piece of hardware during installation, you may manually add the appropriate module to the MODULES= line.
Netfs is for file manipulation over a network. I personally don't use it.

---

