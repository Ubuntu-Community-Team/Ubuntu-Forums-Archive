---
title: "mbp UEFI boot  pommed and latest apple_gmux backlight"
date: 2012-04-04
forum: Apple Hardware Users
---

### Post by currir55 on 2012-04-04
Hi all,

Scratching a small itch I had,

if you're booting an macbook pro 6,2 (and other models, but I don't know whitch) using UEFI to get access to the intel card and amazing battery life,

For those that do remember to grab the dual channel lvds patch for i915 on mbp 6,2 or your machine will not turn the internal display back on but will still boot OK (don't know about externals)

Grab the latest AppleGmuxBacklight driver [https://wiki.ubuntu.com/Kernel/AppleGmuxBacklight](https://wiki.ubuntu.com/Kernel/AppleGmuxBacklight)

I'm running openSuSE so built the sources from here with no problems: [http://ppa.launchpad.net/sforshee/apple-bl-gmux/ubuntu/pool/main/a/apple-bl-gmux-dkms/](http://ppa.launchpad.net/sforshee/apple-bl-gmux/ubuntu/pool/main/a/apple-bl-gmux-dkms/)



To get the driver to work with pommed, grab the latest sources from
git://anonscm.debian.org/pommed/pommed.git

and apply the diff I wrote below at the bottom.


IMPORTANT, IMPORTANT

your pommed.conf should contain a sysfs section like the one below (possibly with a bigger step size of 1000 for those that want it)

DO NOT use the default lcd_sysfs config or you will get virtually no backlight and will likely not be able to see your screen
(this is a pain to fix if you just overwrote your /usr/bin/pommed file and have the service running at boot)


I hope this of some use to someone, at least for me I get a nice working backlight along with everything else from boot working with open drivers
(but not firmware yet)


Happy hacking,


Rob :D :D :D



pommed.conf:
```

lcd_sysfs {
        init = 12000
        step = 500
        on_batt = 6000
}

```pommed source code:

```

diff --git a/pommed/sysfs_backlight.c b/pommed/sysfs_backlight.c
index d2cf9f7..b3d6330 100644
--- a/pommed/sysfs_backlight.c
+++ b/pommed/sysfs_backlight.c
@@ -47,6 +47,7 @@ enum {
   SYSFS_DRIVER_NVIDIA,
   SYSFS_DRIVER_NOUVEAU,
   SYSFS_DRIVER_ACPI,
+  SYSFS_DRIVER_GMUX,
 #endif
   SYSFS_DRIVER_MAX
 };
@@ -70,6 +71,7 @@ static char *actual_brightness[] =
     "/sys/class/backlight/nvidia_backlight/actual_brightness",
     "/sys/class/backlight/nv_backlight/actual_brightness",
     "/sys/class/backlight/acpi_video0/actual_brightness",
+    "/sys/class/backlight/gmux_backlight/actual_brightness",
 #endif
   };
 
@@ -88,6 +90,7 @@ static char *brightness[] =
     "/sys/class/backlight/nvidia_backlight/brightness",
     "/sys/class/backlight/nv_backlight/brightness",
     "/sys/class/backlight/acpi_video0/brightness",
+    "/sys/class/backlight/gmux_backlight/brightness",
 #endif
   };
 
@@ -106,6 +109,7 @@ static char *max_brightness[] =
     "/sys/class/backlight/nvidia_backlight/max_brightness",
     "/sys/class/backlight/nv_backlight/max_brightness",
     "/sys/class/backlight/acpi_video0/max_brightness",
+    "/sys/class/backlight/gmux_backlight/max_brightness",
 #endif
   };
 
@@ -422,6 +426,12 @@ mbp_sysfs_backlight_probe(void)
        return 0;
     }
 
+  /* This driver works with a lot of the machines exclused below */
+  if( ret == SYSFS_DRIVER_GMUX )
+  {
+    logmsg(LOG_INFO, "Using the latest apple_gmux driver");
+    return ret;
+
   /* Probe failed, wire up native driver instead */
   switch (mops->type)
     {
@@ -452,3 +462,4 @@ mbp_sysfs_backlight_probe(void)
   return -1;
 }
 #endif
+

```

---

