---
title: "VMWare 5.5 Server Dapper-&gt;Edgy following reconfig"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by fluffy-spikey on 2007-03-12
I installed VMWare Server on Dapper (6.06) LTS and created a couple of VMs, no problemo. Since then I have upgraded to Edgy 6.10. I have not reused VMWare till just now. When I tried to start the Server Console (from the command line) I received the message

```
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

```
I followed this and it rebuilt the installation. It said it was built successfully and restarted services - and *ps -ef* reports that things are all running. HOwever when I tried to start the Server Console again (using the command *vmware*) I got

```
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0:
 no version information available (required by /usr/lib/libcairo.so.2)
```

Any assistance gratefully received. Thank you

---

### Post by visik7 on 2007-03-12
this shouldn't be a problem the message is normal
after it the vmware console should start normaly

---

### Post by scxtt on 2007-03-12
i've gotten that too (from a straight install of edgy) - i'm sure it was there before, in the "warning" sense and since i used a button to launch it, i never saw that output in the terminal ...

at any rate i copied (the already existing) /usr/lib/libpng12.so.0 over to the one vmware uses and i don't get that "error / message" at all ...

on a side note, i was using DreamLinux (another debian-based distro) and using this method didn't allow vmware server to actually start up (and there were a few other install "issues")

---

### Post by fluffy-spikey on 2007-03-14
Thank you scxtt. I tried that, but in the process I noticed something weeeird: All the lib files are in subdirectories named after themselves (ie. libpng12.so.0 was in a subdir called /usr/lib/vmware/lib/libpng12.so.0) - with the exception of PAM/security stuff which contained multiple files.

I thought this looked bizarre. Anyway, I copied all the files out of the subdirs into the /usr/lib/vmware/lib/ dir (renaming the subdirs at the same time). Now it obviously loads some libraries, but then seems to baulk at others - at the moment it doesn't like libgnomecanvassmm-2.6.so.1, even though that is now in the lib directory.

Or perhaps I'm reading this wrong and I need just a simple environment variable or something?

Maybe I'll just reinstall the bugger from scratch... So don't worry too much, though I am grateful for the assistance.

---

### Post by scxtt on 2007-03-15
i wouldn't have messed w/ that ...

i just meant to copy

(the file): /usr/lib/libpng12.so.0

to

(the directory): /usr/lib/vmware/lib/libpng12.so.0/

so you'd have a file, /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0

so if i do a "slocate libpng12.so.0" i get:
```
[font=courier]:> slocate libpng12.so.0
/usr/lib/vmware/lib/libpng12.so.0
**/usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0**
/usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0_OLD
**/usr/lib/libpng12.so.0**
/usr/lib/libpng12.so.0.1.2.8[/font]
```

---

