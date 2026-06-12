---
title: "X Crashes and logs out on video play"
date: 2011-06-09
forum: Any Other OS
---

### Post by ommie ramirez-andujar on 2011-06-09
My Gnome session closes and logs me out on video o audio play? I attach my Gdm, Xorg and Syslog logs.
I am using Linux Mint 11

```

**[COLOR="Red"]GDM BEGIN[/COLOR]** ---------------------

(--) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event4)
(**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
(II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(**) Logitech USB-PS/2 Optical Mouse: always reports core events
(**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event4"
(--) Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
(--) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
(--) Logitech USB-PS/2 Optical Mouse: Found relative axes
(--) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
(II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
(II) Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
(**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
(II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
(**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
(**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
(**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
(**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
(II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(--) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) CHROME(0): VIALeaveVT
(II) CHROME(0): [drm] Cleaning up DMA ring-buffer.
(II) CHROME(0): VIARestore
(II) CHROME(0): ViaDisablePrimaryFIFO
(II) AIGLX: Resuming AIGLX clients after VT switch
(II) CHROME(0): VIAEnterVT
(II) CHROME(0): VIASave
(II) CHROME(0): Primary
(II) CHROME(0): Primary Adapter! saving VGA_SR_ALL !!
(II) CHROME(0): Crtc...
(II) CHROME(0): TVSave...
(II) CHROME(0): VIAWriteMode
(II) CHROME(0): ViaModePrimaryLegacy
(II) CHROME(0): Name: 1152x864
(II) CHROME(0): Clock: 108000
(II) CHROME(0): VRefresh: 75.000000
(II) CHROME(0): HSync: 67.500000
(II) CHROME(0): HDisplay: 1152
(II) CHROME(0): HSyncStart: 1216
(II) CHROME(0): HSyncEnd: 1344
(II) CHROME(0): HTotal: 1600
(II) CHROME(0): HSkew: 0
(II) CHROME(0): VDisplay: 864
(II) CHROME(0): VSyncStart: 865
(II) CHROME(0): VSyncEnd: 868
(II) CHROME(0): VTotal: 900
(II) CHROME(0): VScan: 0
(II) CHROME(0): Flags: 5
(II) CHROME(0): CrtcHDisplay: 0x480
(II) CHROME(0): CrtcHBlankStart: 0x480
(II) CHROME(0): CrtcHSyncStart: 0x4c0
(II) CHROME(0): CrtcHSyncEnd: 0x540
(II) CHROME(0): CrtcHBlankEnd: 0x640
(II) CHROME(0): CrtcHTotal: 0x640
(II) CHROME(0): CrtcHSkew: 0x0
(II) CHROME(0): CrtcVDisplay: 0x360
(II) CHROME(0): CrtcVBlankStart: 0x360
(II) CHROME(0): CrtcVSyncStart: 0x361
(II) CHROME(0): CrtcVSyncEnd: 0x364
(II) CHROME(0): CrtcVBlankEnd: 0x384
(II) CHROME(0): CrtcVTotal: 0x384
(II) CHROME(0): ViaFirstCRTCSetMode
(II) CHROME(0): Setting up 1152x864
(II) CHROME(0): ViaComputeDotClock 108000 : 0b53 : 8479
(II) CHROME(0): ViaTVPower: Off.
(II) CHROME(0): ViaSetPrimaryFIFO
(II) CHROME(0): ViaSetPrimaryExpireNumber
(II) CHROME(0): ViaSetDotclock to 0x008479
(II) CHROME(0): ViaSetUseExternalClock
(II) CHROME(0): VIAAdjustFrame 0x0
(II) CHROME(0): ViaFirstCRTCSetStartingAddress
(II) CHROME(0): [drm] Initialized AGP ring-buffer, size 0x200000 at AGP offset 0x1e00000.
(II) CHROME(0): VIALoadPalette: numColors: 256
(II) CHROME(0): VIASwitchMode
(II) CHROME(0): [drm] Cleaning up DMA ring-buffer.
(II) CHROME(0): VIAWriteMode
(II) CHROME(0): ViaModePrimaryLegacy
(II) CHROME(0): Name: 1024x768
(II) CHROME(0): Clock: 78750
(II) CHROME(0): VRefresh: 75.028580
(II) CHROME(0): HSync: 60.022865
(II) CHROME(0): HDisplay: 1024
(II) CHROME(0): HSyncStart: 1040
(II) CHROME(0): HSyncEnd: 1136
(II) CHROME(0): HTotal: 1312
(II) CHROME(0): HSkew: 0
(II) CHROME(0): VDisplay: 768
(II) CHROME(0): VSyncStart: 769
(II) CHROME(0): VSyncEnd: 772
(II) CHROME(0): VTotal: 800
(II) CHROME(0): VScan: 0
(II) CHROME(0): Flags: 5
(II) CHROME(0): CrtcHDisplay: 0x400
(II) CHROME(0): CrtcHBlankStart: 0x400
(II) CHROME(0): CrtcHSyncStart: 0x410
(II) CHROME(0): CrtcHSyncEnd: 0x470
(II) CHROME(0): CrtcHBlankEnd: 0x520
(II) CHROME(0): CrtcHTotal: 0x520
(II) CHROME(0): CrtcHSkew: 0x0
(II) CHROME(0): CrtcVDisplay: 0x300
(II) CHROME(0): CrtcVBlankStart: 0x300
(II) CHROME(0): CrtcVSyncStart: 0x301
(II) CHROME(0): CrtcVSyncEnd: 0x304
(II) CHROME(0): CrtcVBlankEnd: 0x320
(II) CHROME(0): CrtcVTotal: 0x320
(II) CHROME(0): ViaFirstCRTCSetMode
(II) CHROME(0): Setting up 1024x768
(II) CHROME(0): ViaComputeDotClock 78750 : 0000 : 020b
(II) CHROME(0): ViaTVPower: Off.
(II) CHROME(0): ViaSetPrimaryFIFO
(II) CHROME(0): ViaSetPrimaryExpireNumber
(II) CHROME(0): ViaSetDotclock to 0x00020b
(II) CHROME(0): ViaSetUseExternalClock
(II) CHROME(0): VIAAdjustFrame 0x0
(II) CHROME(0): ViaFirstCRTCSetStartingAddress
(II) CHROME(0): [drm] Initialized AGP ring-buffer, size 0x200000 at AGP offset 0x1e00000.
(II) CHROME(0): VIALoadPalette: numColors: 256
(II) CHROME(0): VIAAdjustFrame 0x0
(II) CHROME(0): ViaFirstCRTCSetStartingAddress
(II) CHROME(0): VIAAdjustFrame 1x1
(II) CHROME(0): ViaFirstCRTCSetStartingAddress
(II) CHROME(0): VIAAdjustFrame 0x0
(II) CHROME(0): ViaFirstCRTCSetStartingAddress
GDM END---------------------------------------------------------

**[COLOR="red"]SYSLOG BEGIN[/COLOR]**-- ----------------------------------
Jun 8 17:17:01 heroh CRON[2056]: (root) CMD ( cd / && run-parts --report /etc/cron.hourly)
Jun 8 17:17:50 heroh kernel: [ 220.908500] multiqueue0:src[2088] general protection ip:bbca84 sp:b5bfeb60 error:0 in libgstreamer-0.10.so.0.28.0[b70000+c3000]
Jun 8 17:19:09 heroh kernel: [ 299.988013] [Hardware Error]: Machine check events logged
Jun 8 17:21:12 heroh kernel: [ 422.805871] CPU0: Core temperature above threshold, cpu clock throttled (total events = 640)
Jun 8 17:21:12 heroh kernel: [ 422.805893] CPU1: Core temperature above threshold, cpu clock throttled (total events = 637)
Jun 8 17:21:12 heroh kernel: [ 422.807136] CPU0: Core temperature/speed normal
Jun 8 17:21:12 heroh kernel: [ 422.807146] CPU1: Core temperature/speed normal
Jun 8 17:21:37 heroh gdm-simple-slave[2292]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jun 8 17:21:37 heroh acpid: client connected from 2294[0:0]
Jun 8 17:21:37 heroh acpid: 1 client rule loaded
Jun 8 17:21:37 heroh kernel: [ 448.194404] agpgart-via 0000:00:00.0: AGP 3.5 bridge
Jun 8 17:21:37 heroh kernel: [ 448.194436] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
Jun 8 17:21:37 heroh kernel: [ 448.194543] pci 0000:01:00.0: putting AGP V3 device into 8x mode
Jun 8 17:21:39 heroh gdm-session-worker[2339]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jun 8 17:21:39 heroh kernel: [ 449.988049] [Hardware Error]: Machine check events logged
Jun 8 17:21:39 heroh rtkit-daemon[1431]: Successfully made thread 2346 of process 2346 (n/a) owned by '106' high priority at nice level -11.
Jun 8 17:21:39 heroh rtkit-daemon[1431]: Supervising 1 threads of 1 processes of 1 users.
Jun 8 17:21:40 heroh rtkit-daemon[1431]: Successfully made thread 2350 of process 2346 (n/a) owned by '106' RT at priority 5.
Jun 8 17:21:40 heroh rtkit-daemon[1431]: Supervising 2 threads of 1 processes of 1 users.
Jun 8 17:21:40 heroh rtkit-daemon[1431]: Successfully made thread 2351 of process 2346 (n/a) owned by '106' RT at priority 5.
Jun 8 17:21:40 heroh rtkit-daemon[1431]: Supervising 3 threads of 1 processes of 1 users.
Jun 8 17:21:40 heroh gdm-simple-greeter[2337]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a GtkWindow
Jun 8 17:21:41 heroh gdm-simple-greeter[2337]: WARNING: Unable to load CK history: no seat-id found
Jun 8 17:21:42 heroh gdm-session-worker[2339]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jun 8 17:21:43 heroh gdm-session-worker[2339]: pam_sm_authenticate: Called
Jun 8 17:21:43 heroh gdm-session-worker[2339]: pam_sm_authenticate: username = [tramirez]
Jun 8 17:21:45 heroh rtkit-daemon[1431]: Successfully made thread 2453 of process 2453 (n/a) owned by '1000' high priority at nice level -11.
Jun 8 17:21:45 heroh rtkit-daemon[1431]: Supervising 4 threads of 2 processes of 2 users.
Jun 8 17:21:45 heroh pulseaudio[2453]: pid.c: Stale PID file, overwriting.
Jun 8 17:21:45 heroh rtkit-daemon[1431]: Successfully made thread 2458 of process 2453 (n/a) owned by '1000' RT at priority 5.
Jun 8 17:21:45 heroh rtkit-daemon[1431]: Supervising 5 threads of 2 processes of 2 users.
Jun 8 17:21:45 heroh rtkit-daemon[1431]: Successfully made thread 2461 of process 2453 (n/a) owned by '1000' RT at priority 5.
Jun 8 17:21:45 heroh rtkit-daemon[1431]: Supervising 6 threads of 2 processes of 2 users.
Jun 8 17:21:48 heroh nautilus: [N-A] Nautilus-Actions Tracker 3.0.5 initializing...
Jun 8 17:21:48 heroh nautilus: [N-A] Nautilus-Actions Menu Extender 3.0.5 initializing...
Jun 8 17:22:43 heroh acpid: client 2294[0:0] has disconnected
Jun 8 17:22:43 heroh acpid: client connected from 2294[0:0]
Jun 8 17:22:43 heroh acpid: 1 client rule loaded
Jun 8 17:23:45 heroh gdm-simple-slave[3014]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jun 8 17:23:45 heroh acpid: client 2294[0:0] has disconnected
Jun 8 17:23:45 heroh acpid: client connected from 3016[0:0]
Jun 8 17:23:45 heroh acpid: 1 client rule loaded
Jun 8 17:23:45 heroh kernel: [ 576.401232] agpgart-via 0000:00:00.0: AGP 3.5 bridge
Jun 8 17:23:45 heroh kernel: [ 576.401263] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
Jun 8 17:23:45 heroh kernel: [ 576.401370] pci 0000:01:00.0: putting AGP V3 device into 8x mode
Jun 8 17:23:47 heroh gdm-session-worker[3061]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jun 8 17:23:47 heroh rtkit-daemon[1431]: Successfully made thread 3070 of process 3070 (n/a) owned by '106' high priority at nice level -11.
Jun 8 17:23:47 heroh rtkit-daemon[1431]: Supervising 1 threads of 1 processes of 1 users.
Jun 8 17:23:48 heroh rtkit-daemon[1431]: Successfully made thread 3072 of process 3070 (n/a) owned by '106' RT at priority 5.
Jun 8 17:23:48 heroh rtkit-daemon[1431]: Supervising 2 threads of 1 processes of 1 users.
Jun 8 17:23:48 heroh rtkit-daemon[1431]: Successfully made thread 3073 of process 3070 (n/a) owned by '106' RT at priority 5.
Jun 8 17:23:48 heroh rtkit-daemon[1431]: Supervising 3 threads of 1 processes of 1 users.
Jun 8 17:23:48 heroh gdm-simple-greeter[3059]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a GtkWindow
Jun 8 17:23:49 heroh gdm-simple-greeter[3059]: WARNING: Unable to load CK history: no seat-id found
Jun 8 17:25:27 heroh acpid: client 3016[0:0] has disconnected
Jun 8 17:25:27 heroh acpid: client connected from 3016[0:0]
Jun 8 17:25:27 heroh acpid: 1 client rule loaded
Jun 8 17:25:29 heroh gdm-session-worker[3061]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jun 8 17:25:31 heroh gdm-session-worker[3061]: pam_sm_authenticate: Called
Jun 8 17:25:31 heroh gdm-session-worker[3061]: pam_sm_authenticate: username = [tramirez]
Jun 8 17:25:33 heroh rtkit-daemon[1431]: Successfully made thread 3186 of process 3186 (n/a) owned by '1000' high priority at nice level -11.
Jun 8 17:25:33 heroh rtkit-daemon[1431]: Supervising 4 threads of 2 processes of 2 users.
Jun 8 17:25:33 heroh pulseaudio[3186]: pid.c: Stale PID file, overwriting.
Jun 8 17:25:33 heroh rtkit-daemon[1431]: Successfully made thread 3191 of process 3186 (n/a) owned by '1000' RT at priority 5.
Jun 8 17:25:33 heroh rtkit-daemon[1431]: Supervising 5 threads of 2 processes of 2 users.
Jun 8 17:25:33 heroh rtkit-daemon[1431]: Successfully made thread 3194 of process 3186 (n/a) owned by '1000' RT at priority 5.
Jun 8 17:25:33 heroh rtkit-daemon[1431]: Supervising 6 threads of 2 processes of 2 users.
Jun 8 17:25:34 heroh nautilus: [N-A] Nautilus-Actions Tracker 3.0.5 initializing...
Jun 8 17:25:35 heroh nautilus: [N-A] Nautilus-Actions Menu Extender 3.0.5 initializing...
Jun 8 17:25:54 heroh sudo: pam_sm_authenticate: Called
Jun 8 17:25:54 heroh sudo: pam_sm_authenticate: username = [tramirez]
Jun 8 17:25:54 heroh nautilus: [N-A] Nautilus-Actions Tracker 3.0.5 initializing...
Jun 8 17:25:54 heroh nautilus: [N-A] Nautilus-Actions Menu Extender 3.0.5 initializing...
Jun 8 17:25:55 heroh kernel: [ 706.028033] end_request: I/O error, dev fd0, sector 0
Jun 8 17:25:55 heroh kernel: [ 706.052056] end_request: I/O error, dev fd0, sector 0
SYSLOG END


**[COLOR="red"]XORG BEGIN[/COLOR]**
[ 576.762] (**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 576.762] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.0/usb2/2-2/2-2:1.0/input/input4/event4"
[ 576.762] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
[ 576.762] (II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[ 576.762] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[ 576.762] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[ 576.762] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[ 576.762] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[ 576.763] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[ 576.763] (II) No input driver/identifier specified (ignoring)
[ 576.771] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[ 576.771] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[ 576.771] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[ 576.771] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 576.771] (**) AT Translated Set 2 keyboard: always reports core events
[ 576.771] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[ 576.771] (--) AT Translated Set 2 keyboard: Found keys
[ 576.771] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[ 576.771] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[ 576.771] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[ 576.771] (**) Option "xkb_rules" "evdev"
[ 576.771] (**) Option "xkb_model" "pc105"
[ 576.771] (**) Option "xkb_layout" "us"
[ 579.696] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 579.696] (II) CHROME(0): VIALeaveVT
[ 579.696] (II) CHROME(0): [drm] Cleaning up DMA ring-buffer.
[ 579.772] (II) CHROME(0): VIARestore
[ 579.772] (II) CHROME(0): ViaDisablePrimaryFIFO
[ 678.005] (II) Open ACPI successful (/var/run/acpid.socket)
[ 678.005] (II) AIGLX: Resuming AIGLX clients after VT switch
[ 678.005] (II) CHROME(0): VIAEnterVT
[ 678.005] (II) CHROME(0): VIASave
[ 678.006] (II) CHROME(0): Primary
[ 678.006] (II) CHROME(0): Primary Adapter! saving VGA_SR_ALL !!
[ 678.006] (II) CHROME(0): Crtc...
[ 678.006] (II) CHROME(0): TVSave...
[ 678.006] (II) CHROME(0): VIAWriteMode
[ 678.006] (II) CHROME(0): ViaModePrimaryLegacy
[ 678.006] (II) CHROME(0): Name: 1152x864
[ 678.006] (II) CHROME(0): Clock: 108000
[ 678.006] (II) CHROME(0): VRefresh: 75.000000
[ 678.006] (II) CHROME(0): HSync: 67.500000
[ 678.006] (II) CHROME(0): HDisplay: 1152
[ 678.006] (II) CHROME(0): HSyncStart: 1216
[ 678.006] (II) CHROME(0): HSyncEnd: 1344
[ 678.006] (II) CHROME(0): HTotal: 1600
[ 678.006] (II) CHROME(0): HSkew: 0
[ 678.006] (II) CHROME(0): VDisplay: 864
[ 678.006] (II) CHROME(0): VSyncStart: 865
[ 678.006] (II) CHROME(0): VSyncEnd: 868
[ 678.006] (II) CHROME(0): VTotal: 900
[ 678.006] (II) CHROME(0): VScan: 0
[ 678.006] (II) CHROME(0): Flags: 5
[ 678.006] (II) CHROME(0): CrtcHDisplay: 0x480
[ 678.006] (II) CHROME(0): CrtcHBlankStart: 0x480
[ 678.006] (II) CHROME(0): CrtcHSyncStart: 0x4c0
[ 678.007] (II) CHROME(0): CrtcHSyncEnd: 0x540
[ 678.007] (II) CHROME(0): CrtcHBlankEnd: 0x640
[ 678.007] (II) CHROME(0): CrtcHTotal: 0x640
[ 678.007] (II) CHROME(0): CrtcHSkew: 0x0
[ 678.007] (II) CHROME(0): CrtcVDisplay: 0x360
[ 678.007] (II) CHROME(0): CrtcVBlankStart: 0x360
[ 678.007] (II) CHROME(0): CrtcVSyncStart: 0x361
[ 678.007] (II) CHROME(0): CrtcVSyncEnd: 0x364
[ 678.007] (II) CHROME(0): CrtcVBlankEnd: 0x384
[ 678.007] (II) CHROME(0): CrtcVTotal: 0x384
[ 678.007] (II) CHROME(0): ViaFirstCRTCSetMode
[ 678.007] (II) CHROME(0): Setting up 1152x864
[ 678.007] (II) CHROME(0): ViaComputeDotClock 108000 : 0b53 : 8479
[ 678.008] (II) CHROME(0): ViaTVPower: Off.
[ 678.008] (II) CHROME(0): ViaSetPrimaryFIFO
[ 678.008] (II) CHROME(0): ViaSetPrimaryExpireNumber
[ 678.008] (II) CHROME(0): ViaSetDotclock to 0x008479
[ 678.008] (II) CHROME(0): ViaSetUseExternalClock
[ 678.008] (II) CHROME(0): VIAAdjustFrame 0x0
[ 678.008] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
[ 678.009] (II) CHROME(0): [drm] Initialized AGP ring-buffer, size 0x200000 at AGP offset 0x1e00000.
[ 678.025] (II) CHROME(0): VIALoadPalette: numColors: 256
[ 683.332] (II) CHROME(0): VIASwitchMode
[ 683.332] (II) CHROME(0): [drm] Cleaning up DMA ring-buffer.
[ 683.332] (II) CHROME(0): VIAWriteMode
[ 683.332] (II) CHROME(0): ViaModePrimaryLegacy
[ 683.332] (II) CHROME(0): Name: 1024x768
[ 683.332] (II) CHROME(0): Clock: 78750
[ 683.332] (II) CHROME(0): VRefresh: 75.028580
[ 683.332] (II) CHROME(0): HSync: 60.022865
[ 683.332] (II) CHROME(0): HDisplay: 1024
[ 683.332] (II) CHROME(0): HSyncStart: 1040
[ 683.332] (II) CHROME(0): HSyncEnd: 1136
[ 683.333] (II) CHROME(0): HTotal: 1312
[ 683.333] (II) CHROME(0): HSkew: 0
[ 683.333] (II) CHROME(0): VDisplay: 768
[ 683.333] (II) CHROME(0): VSyncStart: 769
[ 683.333] (II) CHROME(0): VSyncEnd: 772
[ 683.333] (II) CHROME(0): VTotal: 800
[ 683.333] (II) CHROME(0): VScan: 0
[ 683.333] (II) CHROME(0): Flags: 5
[ 683.333] (II) CHROME(0): CrtcHDisplay: 0x400
[ 683.333] (II) CHROME(0): CrtcHBlankStart: 0x400
[ 683.333] (II) CHROME(0): CrtcHSyncStart: 0x410
[ 683.333] (II) CHROME(0): CrtcHSyncEnd: 0x470
[ 683.333] (II) CHROME(0): CrtcHBlankEnd: 0x520
[ 683.333] (II) CHROME(0): CrtcHTotal: 0x520
[ 683.333] (II) CHROME(0): CrtcHSkew: 0x0
[ 683.333] (II) CHROME(0): CrtcVDisplay: 0x300
[ 683.333] (II) CHROME(0): CrtcVBlankStart: 0x300
[ 683.333] (II) CHROME(0): CrtcVSyncStart: 0x301
[ 683.333] (II) CHROME(0): CrtcVSyncEnd: 0x304
[ 683.333] (II) CHROME(0): CrtcVBlankEnd: 0x320
[ 683.333] (II) CHROME(0): CrtcVTotal: 0x320
[ 683.333] (II) CHROME(0): ViaFirstCRTCSetMode
[ 683.333] (II) CHROME(0): Setting up 1024x768
[ 683.334] (II) CHROME(0): ViaComputeDotClock 78750 : 0000 : 020b
[ 683.334] (II) CHROME(0): ViaTVPower: Off.
[ 683.334] (II) CHROME(0): ViaSetPrimaryFIFO
[ 683.334] (II) CHROME(0): ViaSetPrimaryExpireNumber
[ 683.334] (II) CHROME(0): ViaSetDotclock to 0x00020b
[ 683.334] (II) CHROME(0): ViaSetUseExternalClock
[ 683.334] (II) CHROME(0): VIAAdjustFrame 0x0
[ 683.334] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
[ 683.334] (II) CHROME(0): [drm] Initialized AGP ring-buffer, size 0x200000 at AGP offset 0x1e00000.
[ 683.334] (II) CHROME(0): VIALoadPalette: numColors: 256
[ 683.335] (II) CHROME(0): VIAAdjustFrame 0x0
[ 683.335] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
[ 683.335] (II) CHROME(0): VIAAdjustFrame 1x1
[ 683.335] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
[ 683.335] (II) CHROME(0): VIAAdjustFrame 0x0
[ 683.335] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
XORG END
```

---

### Post by Perfect Storm on 2011-06-09
Moved to Other OS/Distro Talk.

---

