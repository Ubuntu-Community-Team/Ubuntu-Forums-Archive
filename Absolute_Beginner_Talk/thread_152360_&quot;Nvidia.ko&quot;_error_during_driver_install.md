---
title: "&quot;Nvidia.ko&quot; error during driver install"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by gordong11 on 2006-03-29
I'm trying to install nvidia drivers, and keep getting "unable to load nvidia.ko" because of the kernel. Does anyone know a fix? I bypass all the error messages that shows up about  kernels that don't match. nothing I do seems to matter.

Thanks

---

### Post by simonn on 2006-03-29
I went through all this yesterday and the day before.

First off, try adding the following to the bottom of /etc/hotplug/blacklist.

```

#added by [insert your name here]
agpgart

```

Reboot.

If this does not work, let me know. If you have tried installing the drivers from nvidia, not the ubuntu packages you may need to clean all that up and reinstall the nvidia packages.

---

### Post by gordong11 on 2006-03-29
Thanks for the reply....I cant even find the blacklist file....is there a special command?

I'm at the point of just keeping Vesa, and buying a PCI sound card. IE Soundblaster audigy. I would like to get this thing installed, but it just doesnt seem to be meant to happen. I have literally been working 10+ hours on this install of the nvidia drivers.

I'm running 64bit breezy, on a Gigabyte GA-K8N51GMF mobo with onboard Nvidia 6100, and Nvidia 410 chipset...and sound. not only do i need video drivers from Nvidia, I need the Forceware as well...both get the same errors. I even tried that italian package install....but that errored also. ](*,)

---

