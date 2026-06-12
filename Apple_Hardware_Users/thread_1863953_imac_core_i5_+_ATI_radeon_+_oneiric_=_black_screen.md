---
title: "imac core i5 + ATI radeon + oneiric = black screen"
date: 2011-10-18
forum: Apple Hardware Users
---

### Post by pindar on 2011-10-18
Hi all,

I'm trying to install oneiric on an external USB drive (with EFI boot). Installation works flawlessly, the system boots fine. But when it starts the graphical environment, the screen goes black. I assume it must be an issue with the ati drivers. The frustrating thing is: for whatever reasons, I could get a fully functional graphical desktop a couple of times, by booting with "nomodeset" and install xorg:fglrx with jockey-text. But then, after an update, I see some dkms messages, and the screen goes black again. I have tried the jockey method, and I have installed the fglrx package directly from the ARI website, So far, I haven't found a reliable way to boot into the graphical desktop, and I'm not really sure what's going wrong. Anyone have any suggestions? 

Thanks pindar

---

### Post by askvictor on 2011-10-18
Am having the same problem :( much the same setup, but booting off the internal drive. Back to windows I suppose...

---

### Post by pindar on 2011-10-21
Nobody have any idea? Anybody out there with a newish iMac running ubuntu?

---

### Post by willnight on 2011-10-26
this may be related?

i have tri-boot on macbook pro (2007) with connected cinema display, and had a working natty.

i upgraded to oneiric. after reboot and logged in, it showed the ubuntu background. i waited a bit for the interface to come up. nothing. waited more. still nothing. so i had just a blank background image as my desktop and no interface whatsoever. rebooted several time. same.

i thought it was a problem with oneiric, being a new upgrade, so i took the pains to reinstall the last stable and working version, which was natty for me. after installation and updates (not upgrade), i get the blank desktop again, as described above when upgraded to oneiric?

cinema display/nvidia issue? gdm issue? what am i missing? any idea?

thx

---

### Post by pindar on 2011-10-26
> **willnight said:**
> this may be related?

after reboot and logged in, it showed the ubuntu background. i waited a bit for the interface to come up. nothing. waited more. still nothing. so i had just a blank background image as my desktop and no interface whatsoever.
Hmm no, since you see the background, but not the interface, that doesn't appear to be the same problem. [This]("http://ubuntuforums.org/showthread.php?t=1869417") appears to be the same problem.

Though, come to think of it - I tried installing the latest fedora beta and had a similar problem: X seems to start, I see the background (though in a corrupted form, the video is split in two halves), but there is no menu, no nothing.

---

### Post by The MC on 2011-11-01
I have a 8,1 macbook with an i5 and radeon running oneiric without any problems now.

I was able to finally able to successfully install and boot into Ubuntu by installing from disk while disconnected from the internet.  When installing I disabled updates and proprietary software.  I was able to perform all updates after logging into oneiric.

---

### Post by pindar on 2011-11-02
> **The MC said:**
> I have a 8,1 macbook with an i5 and radeon running oneiric without any problems now.

I was able to finally able to successfully install and boot into Ubuntu by installing from disk while disconnected from the internet.  When installing I disabled updates and proprietary software.  I was able to perform all updates after logging into oneiric.
Nope, I just tried that, and I'm getting the same problem as before: black screen. From unverified rumors in obscure corners of the internet, I hear that the problem might be that linux directs the output to the external display port (thunderbolt); people are able to run ubuntu with an external monitor attached. So this sounds like it might be solvable with an appropriate xorg.conf file...

---

### Post by pindar on 2011-11-21
Bringing this thread back to life: I am posting this from my imac, running Ubuntu oneiric. If anyone's still interested in this, here's how to in a nutshell. (Two remarks: Jérémy Lal helped me with this, he was active on [the bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542660") that described this problem, so he deserves all credit; and this worked for me, I can't guarantee that it'll work for anyone else).

[LIST=1]
[*]Boot from live cd. dump the video bios with this command:
dd if=/dev/mem of=vbios.bin bs=65536 skip=12 count=1
copy this file to a place where you will later be able to retrieve it (like a usb stick).
[*]Install normally to your disk (I installed to an external USB disk, leaving my internal disk completely untouched).
[*]Boot into your newly installed system with kernel parameters "nomodeset radeon.modeset=0". This will give you access to a CLI system. Copy the file vbios.bin that you have saved to your new system, to /lib/firmware/radeon/vbios.bin
[*]You will have to compile a custom kernel and apply a patch to the kernel source. I followed [this guide]("http://www.howtoforge.com/kernel_compilation_ubuntu"). Save the patch which I append below as load_vbios_radeon.patch and apply it with this command:
patch -p0 < load_vbios_radeon.patch
[*]After you have compiled the kernel and installed the resulting deb files, reboot without the nomodeset parameter. Ubuntu should come up normally. 
[/LIST]
Let's see if this success is stable, but right now, I'm very happy! Thanks, Jérémy, and good luck everybody!

load_vbios_radeon.patch:
==============================================================
--- drivers/gpu/drm/radeon/radeon_bios.c.orig	2011-09-02 10:10:43.223802888 +0200
+++ drivers/gpu/drm/radeon/radeon_bios.c	2011-09-02 10:11:31.606652206 +0200
@@ -30,6 +30,7 @@
 #include "radeon.h"
 #include "atom.h"
 
+#include <linux/firmware.h>
 #include <linux/vga_switcheroo.h>
 #include <linux/slab.h>
 /*
@@ -98,6 +99,41 @@
 	return true;
 }
 
+static bool radeon_read_bios_from_firmware(struct radeon_device *rdev)
+{
+	const uint8_t __iomem *bios;
+	resource_size_t size;
+	const struct firmware *fw = NULL;
+
+	request_firmware(&fw, "radeon/vbios.bin", rdev->dev);
+	if (!fw) {
+		DRM_ERROR("No bios\n");
+		return false;
+	}
+	size = fw->size;
+	bios = fw->data;
+
+	if (!bios) {
+		DRM_ERROR("No bios\n");
+		return false;
+	}
+
+	if (size == 0 || bios[0] != 0x55 || bios[1] != 0xaa) {
+		DRM_ERROR("wrong sig\n");
+		release_firmware(fw);
+		return false;
+	}
+	rdev->bios = kmalloc(size, GFP_KERNEL);
+	if (rdev->bios == NULL) {
+		DRM_ERROR("alloc fail\n");
+		release_firmware(fw);
+		return false;
+	}
+	memcpy(rdev->bios, bios, size);
+	release_firmware(fw);
+	return true;
+}
+
 /* ATRM is used to get the BIOS on the discrete cards in
  * dual-gpu systems.
  */
@@ -482,7 +518,9 @@
 	bool r;
 	uint16_t tmp;
 
-	r = radeon_atrm_get_bios(rdev);
+	r = radeon_read_bios_from_firmware(rdev);
+	if (r == false)
+		r = radeon_atrm_get_bios(rdev);
 	if (r == false)
 		r = igp_read_bios_from_vram(rdev);
 	if (r == false)
@@ -490,6 +528,7 @@
 	if (r == false) {
 		r = radeon_read_disabled_bios(rdev);
 	}
+
 	if (r == false || rdev->bios == NULL) {
 		DRM_ERROR("Unable to locate a BIOS ROM\n");
 		rdev->bios = NULL;

---

### Post by kapouer on 2012-01-09
Update : linux 3.2 boots without the load_vbios patch on model iMac12,2.

---

