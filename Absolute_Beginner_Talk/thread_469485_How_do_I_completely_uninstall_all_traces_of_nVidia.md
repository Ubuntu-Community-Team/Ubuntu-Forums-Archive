---
title: "How do I completely uninstall all traces of nVidia drivers?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Doc.Caliban on 2007-06-09
I need to elliminate all traces of any nVidia drivers and settings on my system.  I am currently running on the "nv" driver.

-Doc

---

### Post by 5-HT on 2007-06-09
Depends on how you installed the drivers (i.e., manually from Nvidia's binaries, from the repos, a third party utility, etc...)

---

### Post by Doc.Caliban on 2007-06-10
Originally I installed them from nVidia's binaries.  I think I've installed a couple versions of them that way.  Is there a way I can find out exactly which ones I've installed?

Thank you.

-Doc

---

### Post by 5-HT on 2007-06-10
You can check your current driver version form nvidia-xconfig.
IIRC, installing newer versions from NVIDIA's binaries would result in the files from previous installations being overwritten. If not, you can do a quick scan of the installation directories to make sure (if you only installed the driver itself, it will be the nvidia.ko file in the modules directory for your kernel). 

To uninstall, you can use the --uninstall flag when running NVIDIA's .run file.
You can check out available options using the --help flag from the .run file.

Hope that helps

---

### Post by Doc.Caliban on 2007-06-11
I'll take a look, thanks.

The problem I'm having is that the original beta drivers that I installed worked perfectly with Beryl, but I got an error at one point when trying to load X saying that the nVidia driver was wrong.  I reinstalled but can't get into X with the nvidia drivers anymore.  I'm hoping I can get back to where I was if I clean things out and start again.

-Doc

---

