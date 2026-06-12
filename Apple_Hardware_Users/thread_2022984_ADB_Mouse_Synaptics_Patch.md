---
title: "ADB Mouse Synaptics Patch"
date: 2012-07-11
forum: Apple Hardware Users
---

### Post by fried34 on 2012-07-11
Bonjour

i've got a powerbook g4 with an ADB-Toupad. Under 10.5 OSX i was able to use 2-finger-scroll with iScroll2. Under Xubuntu 12.04 it isn't working, because my Touchpad is recognized as an ADB-Mouse and not as a synaptic touchpad. After i spent hours in searching a solution i found this patch [http://ubuntuforums.org/showthread.php?t=380884](http://ubuntuforums.org/showthread.php?t=380884) ... sadly the link is offline (file caled adbsyn...diff). it says that the patch makes it possible to use the synaptic-driver instead of the adb-mouse-driver.

could anyone help me please to get this thing running?

thanks in advance

---

### Post by guidop on 2012-08-12
I don't know how helpful this will be.
The adbsyn code was provided as a kernel specific patch (.diff) file.

I got this to work with Ubuntu 7.04 kernel 2.6.20 back in 2007, and haven't tried it since.

I found an old image of Ubuntu 7.04 with the patch, and have the .diff files for the 2.6.20 and 2.6.22 kernels.  The patch files are about 160 lines long. If you or someone else has the time and skills to understand the patch file (ed editor?) syntax, perhaps a patch for the latest kernel can be made. 

It would also be helpful if someone more knowledgeable than I could determine whether the adbsyn mod could just be compiled and loaded as  a kernel module, rather than compiling a full custom kernel, which is what I did back 2007 to get my adb trackpad working in absolute mode. I never did get two finger operations to work, just hot corners and edges for mouse buttons and scrolling. The archived thread you linked to has the settings I used. 

Here is what I have for adbsyn_0.3-2.6.20.3.diff:

```
--- linux-2.6.20.3.ORIG/drivers/macintosh/adbhid.c	2007-03-13 19:27:08.000000000 +0100
+++ linux-2.6.20.3/drivers/macintosh/adbhid.c	2007-03-29 22:02:26.000000000 +0200
@@ -252,6 +252,15 @@ static struct adb_ids buttons_ids;
 #define ADBMOUSE_MS_A3		8	/* Mouse systems A3 trackball (handler 3) */
 #define ADBMOUSE_MACALLY2	9	/* MacAlly 2-button mouse */
 
+#ifdef CONFIG_ADB_TRACKPAD_ABSOLUTE
+#define	ABS_XMIN	310
+#define	ABS_XMAX	1700
+#define	ABS_YMIN	200
+#define	ABS_YMAX	1000
+#define	ABS_ZMIN	0
+#define	ABS_ZMAX	55
+#endif
+
 static void
 adbhid_keyboard_input(unsigned char *data, int nb, int apoll)
 {
@@ -350,6 +359,9 @@ static void
 adbhid_mouse_input(unsigned char *data, int nb, int autopoll)
 {
 	int id = (data[0] >> 4) & 0x0f;
+#ifdef CONFIG_ADB_TRACKPAD_ABSOLUTE
+	int btn = 0; int x_axis = 0; int y_axis = 0; int z_axis = 0;
+#endif
 
 	if (!adbhid[id]) {
 		printk(KERN_ERR "ADB HID on ID %d not yet registered\n", id);
@@ -381,6 +393,17 @@ adbhid_mouse_input(unsigned char *data, 
 	      high bits of y-axis motion.  XY is additional
 	      high bits of x-axis motion.
 
+    For ADB Absolute motion protocol the data array will contain the
+    following values:
+
+		BITS    COMMENTS
+    data[0] = dddd 1100 ADB command: Talk, register 0, for device dddd.
+    data[1] = byyy yyyy Left button and y-axis motion.
+    data[2] = bxxx xxxx Second button and x-axis motion.
+    data[3] = 1yyy 1xxx Half bits of y-axis and x-axis motion.
+    data[4] = 1yyy 1xxx Higher bits of y-axis and x-axis motion.
+    data[5] = 1zzz 1zzz Higher and lower bits of z-pressure.
+
     MacAlly 2-button mouse protocol.
 
     For MacAlly 2-button mouse protocol the data array will contain the
@@ -403,8 +426,17 @@ adbhid_mouse_input(unsigned char *data, 
 	switch (adbhid[id]->mouse_kind)
 	{
 	    case ADBMOUSE_TRACKPAD:
+#ifdef CONFIG_ADB_TRACKPAD_ABSOLUTE
+		x_axis = (data[2] & 0x7f) | ((data[3] & 0x07) << 7) |
+			((data[4] & 0x07) << 10);
+		y_axis = (data[1] & 0x7f) | ((data[3] & 0x70) << 3) |
+			((data[4] & 0x70) << 6);
+		z_axis = (data[5] & 0x07) | ((data[5] & 0x70) >> 1);
+		btn = (!(data[1] >> 7)) & 1;
+#else
 		data[1] = (data[1] & 0x7f) | ((data[1] & data[2]) & 0x80);
 		data[2] = data[2] | 0x80;
+#endif
 		break;
 	    case ADBMOUSE_MICROSPEED:
 		data[1] = (data[1] & 0x7f) | ((data[3] & 0x01) << 7);
@@ -430,17 +462,39 @@ adbhid_mouse_input(unsigned char *data, 
                 break;
 	}
 
-	input_report_key(adbhid[id]->input, BTN_LEFT,   !((data[1] >> 7) & 1));
-	input_report_key(adbhid[id]->input, BTN_MIDDLE, !((data[2] >> 7) & 1));
-
-	if (nb >= 4 && adbhid[id]->mouse_kind != ADBMOUSE_TRACKPAD)
-		input_report_key(adbhid[id]->input, BTN_RIGHT,  !((data[3] >> 7) & 1));
-
-	input_report_rel(adbhid[id]->input, REL_X,
-			 ((data[2]&0x7f) < 64 ? (data[2]&0x7f) : (data[2]&0x7f)-128 ));
-	input_report_rel(adbhid[id]->input, REL_Y,
-			 ((data[1]&0x7f) < 64 ? (data[1]&0x7f) : (data[1]&0x7f)-128 ));
+#ifdef CONFIG_ADB_TRACKPAD_ABSOLUTE
+	if ( adbhid[id]->mouse_kind == ADBMOUSE_TRACKPAD ) {
+		
+		if(z_axis > 30) input_report_key(adbhid[id]->input, BTN_TOUCH, 1);
+		if(z_axis < 25) input_report_key(adbhid[id]->input, BTN_TOUCH, 0);
+
+		if(z_axis > 0){
+			input_report_abs(adbhid[id]->input, ABS_X, x_axis);
+			input_report_abs(adbhid[id]->input, ABS_Y, y_axis);
+			input_report_key(adbhid[id]->input, BTN_TOOL_FINGER, 1);
+			input_report_key(adbhid[id]->input, ABS_TOOL_WIDTH, 5);
+		} else {
+			input_report_key(adbhid[id]->input, BTN_TOOL_FINGER, 0);
+			input_report_key(adbhid[id]->input, ABS_TOOL_WIDTH, 0);
+		}
 
+		input_report_abs(adbhid[id]->input, ABS_PRESSURE, z_axis);
+		input_report_key(adbhid[id]->input, BTN_LEFT, btn);
+	} else {
+#endif
+		input_report_key(adbhid[id]->input, BTN_LEFT,   !((data[1] >> 7) & 1));
+		input_report_key(adbhid[id]->input, BTN_MIDDLE, !((data[2] >> 7) & 1));
+		
+		if (nb >= 4 && adbhid[id]->mouse_kind != ADBMOUSE_TRACKPAD)
+			input_report_key(adbhid[id]->input, BTN_RIGHT,  !((data[3] >> 7) & 1));
+		
+		input_report_rel(adbhid[id]->input, REL_X,
+				((data[2]&0x7f) < 64 ? (data[2]&0x7f) : (data[2]&0x7f)-128 ));
+		input_report_rel(adbhid[id]->input, REL_Y,
+				((data[1]&0x7f) < 64 ? (data[1]&0x7f) : (data[1]&0x7f)-128 ));
+#ifdef CONFIG_ADB_TRACKPAD_ABSOLUTE
+	}
+#endif
 	input_sync(adbhid[id]->input);
 }
 
@@ -767,6 +821,15 @@ adbhid_input_register(int id, int defaul
 		input_dev->evbit[0] = BIT(EV_KEY) | BIT(EV_REL);
 		input_dev->keybit[LONG(BTN_MOUSE)] = BIT(BTN_LEFT) | BIT(BTN_MIDDLE) | BIT(BTN_RIGHT);
 		input_dev->relbit[0] = BIT(REL_X) | BIT(REL_Y);
+#ifdef CONFIG_ADB_TRACKPAD_ABSOLUTE
+		set_bit(EV_ABS, input_dev->evbit);
+		input_set_abs_params(input_dev, ABS_X, ABS_XMIN, ABS_XMAX, 0, 0);
+		input_set_abs_params(input_dev, ABS_Y, ABS_YMIN, ABS_YMAX, 0, 0);
+		input_set_abs_params(input_dev, ABS_PRESSURE, ABS_ZMIN, ABS_ZMAX, 0, 0);
+		set_bit(BTN_TOUCH, input_dev->keybit);
+		set_bit(BTN_TOOL_FINGER, input_dev->keybit);
+		set_bit(ABS_TOOL_WIDTH, input_dev->absbit);
+#endif
 		break;
 
 	case ADB_MISC:
@@ -1048,7 +1111,11 @@ init_trackpad(int id)
 	            r1_buffer[3],
 	            r1_buffer[4],
 	            r1_buffer[5],
+#ifdef CONFIG_ADB_TRACKPAD_ABSOLUTE
+		    0x00, /* Enable absolute mode */
+#else
 	            0x03, /*r1_buffer[6],*/
+#endif
 	            r1_buffer[7]);
 
 	    /* Without this flush, the trackpad may be locked up */
--- linux-2.6.20.3.ORIG/drivers/macintosh/Kconfig	2007-03-13 19:27:08.000000000 +0100
+++ linux-2.6.20.3/drivers/macintosh/Kconfig	2007-03-29 22:02:26.000000000 +0200
@@ -160,6 +160,13 @@ config INPUT_ADBHID
 
 	  If unsure, say Y.
 
+config ADB_TRACKPAD_ABSOLUTE
+	bool "Enable absolute mode for adb trackpads"
+	depends on INPUT_ADBHID
+	help
+	  Enable absolute mode in adb-base trackpads. This feature adds
+	  compatibility with synaptics Xorg / Xfree drivers.
+
 config MAC_EMUMOUSEBTN
 	bool "Support for mouse button 2+3 emulation"
 	help

```


And here is adbsyn_0.3-2.6.22.x.diff:

```
--- linux-2.6.22.ORIG/drivers/macintosh/adbhid.c	2007-08-30 17:09:44.000000000 +0200
+++ linux-2.6.22/drivers/macintosh/adbhid.c	2007-08-30 17:10:23.000000000 +0200
@@ -252,6 +252,15 @@ static struct adb_ids buttons_ids;
 #define ADBMOUSE_MS_A3		8	/* Mouse systems A3 trackball (handler 3) */
 #define ADBMOUSE_MACALLY2	9	/* MacAlly 2-button mouse */
 
+#ifdef CONFIG_ADB_TRACKPAD_ABSOLUTE
+#define	ABS_XMIN	310
+#define	ABS_XMAX	1700
+#define	ABS_YMIN	200
+#define	ABS_YMAX	1000
+#define	ABS_ZMIN	0
+#define	ABS_ZMAX	55
+#endif
+
 static void
 adbhid_keyboard_input(unsigned char *data, int nb, int apoll)
 {
@@ -350,6 +359,9 @@ static void
 adbhid_mouse_input(unsigned char *data, int nb, int autopoll)
 {
 	int id = (data[0] >> 4) & 0x0f;
+#ifdef CONFIG_ADB_TRACKPAD_ABSOLUTE
+	int btn = 0; int x_axis = 0; int y_axis = 0; int z_axis = 0;
+#endif
 
 	if (!adbhid[id]) {
 		printk(KERN_ERR "ADB HID on ID %d not yet registered\n", id);
@@ -381,6 +393,17 @@ adbhid_mouse_input(unsigned char *data, 
 	      high bits of y-axis motion.  XY is additional
 	      high bits of x-axis motion.
 
+    For ADB Absolute motion protocol the data array will contain the
+    following values:
+
+		BITS    COMMENTS
+    data[0] = dddd 1100 ADB command: Talk, register 0, for device dddd.
+    data[1] = byyy yyyy Left button and y-axis motion.
+    data[2] = bxxx xxxx Second button and x-axis motion.
+    data[3] = 1yyy 1xxx Half bits of y-axis and x-axis motion.
+    data[4] = 1yyy 1xxx Higher bits of y-axis and x-axis motion.
+    data[5] = 1zzz 1zzz Higher and lower bits of z-pressure.
+
     MacAlly 2-button mouse protocol.
 
     For MacAlly 2-button mouse protocol the data array will contain the
@@ -403,8 +426,17 @@ adbhid_mouse_input(unsigned char *data, 
 	switch (adbhid[id]->mouse_kind)
 	{
 	    case ADBMOUSE_TRACKPAD:
+#ifdef CONFIG_ADB_TRACKPAD_ABSOLUTE
+		x_axis = (data[2] & 0x7f) | ((data[3] & 0x07) << 7) |
+			((data[4] & 0x07) << 10);
+		y_axis = (data[1] & 0x7f) | ((data[3] & 0x70) << 3) |
+			((data[4] & 0x70) << 6);
+		z_axis = (data[5] & 0x07) | ((data[5] & 0x70) >> 1);
+		btn = (!(data[1] >> 7)) & 1;
+#else
 		data[1] = (data[1] & 0x7f) | ((data[1] & data[2]) & 0x80);
 		data[2] = data[2] | 0x80;
+#endif
 		break;
 	    case ADBMOUSE_MICROSPEED:
 		data[1] = (data[1] & 0x7f) | ((data[3] & 0x01) << 7);
@@ -430,17 +462,39 @@ adbhid_mouse_input(unsigned char *data, 
                 break;
 	}
 
-	input_report_key(adbhid[id]->input, BTN_LEFT,   !((data[1] >> 7) & 1));
-	input_report_key(adbhid[id]->input, BTN_MIDDLE, !((data[2] >> 7) & 1));
-
-	if (nb >= 4 && adbhid[id]->mouse_kind != ADBMOUSE_TRACKPAD)
-		input_report_key(adbhid[id]->input, BTN_RIGHT,  !((data[3] >> 7) & 1));
-
-	input_report_rel(adbhid[id]->input, REL_X,
-			 ((data[2]&0x7f) < 64 ? (data[2]&0x7f) : (data[2]&0x7f)-128 ));
-	input_report_rel(adbhid[id]->input, REL_Y,
-			 ((data[1]&0x7f) < 64 ? (data[1]&0x7f) : (data[1]&0x7f)-128 ));
+#ifdef CONFIG_ADB_TRACKPAD_ABSOLUTE
+	if ( adbhid[id]->mouse_kind == ADBMOUSE_TRACKPAD ) {
+		
+		if(z_axis > 30) input_report_key(adbhid[id]->input, BTN_TOUCH, 1);
+		if(z_axis < 25) input_report_key(adbhid[id]->input, BTN_TOUCH, 0);
+
+		if(z_axis > 0){
+			input_report_abs(adbhid[id]->input, ABS_X, x_axis);
+			input_report_abs(adbhid[id]->input, ABS_Y, y_axis);
+			input_report_key(adbhid[id]->input, BTN_TOOL_FINGER, 1);
+			input_report_key(adbhid[id]->input, ABS_TOOL_WIDTH, 5);
+		} else {
+			input_report_key(adbhid[id]->input, BTN_TOOL_FINGER, 0);
+			input_report_key(adbhid[id]->input, ABS_TOOL_WIDTH, 0);
+		}
 
+		input_report_abs(adbhid[id]->input, ABS_PRESSURE, z_axis);
+		input_report_key(adbhid[id]->input, BTN_LEFT, btn);
+	} else {
+#endif
+		input_report_key(adbhid[id]->input, BTN_LEFT,   !((data[1] >> 7) & 1));
+		input_report_key(adbhid[id]->input, BTN_MIDDLE, !((data[2] >> 7) & 1));
+		
+		if (nb >= 4 && adbhid[id]->mouse_kind != ADBMOUSE_TRACKPAD)
+			input_report_key(adbhid[id]->input, BTN_RIGHT,  !((data[3] >> 7) & 1));
+		
+		input_report_rel(adbhid[id]->input, REL_X,
+				((data[2]&0x7f) < 64 ? (data[2]&0x7f) : (data[2]&0x7f)-128 ));
+		input_report_rel(adbhid[id]->input, REL_Y,
+				((data[1]&0x7f) < 64 ? (data[1]&0x7f) : (data[1]&0x7f)-128 ));
+#ifdef CONFIG_ADB_TRACKPAD_ABSOLUTE
+	}
+#endif
 	input_sync(adbhid[id]->input);
 }
 
@@ -767,6 +821,15 @@ adbhid_input_register(int id, int defaul
 		input_dev->evbit[0] = BIT(EV_KEY) | BIT(EV_REL);
 		input_dev->keybit[LONG(BTN_MOUSE)] = BIT(BTN_LEFT) | BIT(BTN_MIDDLE) | BIT(BTN_RIGHT);
 		input_dev->relbit[0] = BIT(REL_X) | BIT(REL_Y);
+#ifdef CONFIG_ADB_TRACKPAD_ABSOLUTE
+		set_bit(EV_ABS, input_dev->evbit);
+		input_set_abs_params(input_dev, ABS_X, ABS_XMIN, ABS_XMAX, 0, 0);
+		input_set_abs_params(input_dev, ABS_Y, ABS_YMIN, ABS_YMAX, 0, 0);
+		input_set_abs_params(input_dev, ABS_PRESSURE, ABS_ZMIN, ABS_ZMAX, 0, 0);
+		set_bit(BTN_TOUCH, input_dev->keybit);
+		set_bit(BTN_TOOL_FINGER, input_dev->keybit);
+		set_bit(ABS_TOOL_WIDTH, input_dev->absbit);
+#endif
 		break;
 
 	case ADB_MISC:
@@ -1048,7 +1111,11 @@ init_trackpad(int id)
 	            r1_buffer[3],
 	            r1_buffer[4],
 	            r1_buffer[5],
+#ifdef CONFIG_ADB_TRACKPAD_ABSOLUTE
+		    0x00, /* Enable absolute mode */
+#else
 	            0x03, /*r1_buffer[6],*/
+#endif
 	            r1_buffer[7]);
 
 	    /* Without this flush, the trackpad may be locked up */
--- linux-2.6.22.ORIG/drivers/macintosh/Kconfig	2007-08-30 17:09:48.000000000 +0200
+++ linux-2.6.22/drivers/macintosh/Kconfig	2007-08-30 17:10:23.000000000 +0200
@@ -165,6 +165,13 @@ config INPUT_ADBHID
 
 	  If unsure, say Y.
 
+config ADB_TRACKPAD_ABSOLUTE
+	bool "Enable absolute mode for adb trackpads"
+	depends on INPUT_ADBHID
+	help
+	  Enable absolute mode in adb-base trackpads. This feature adds
+	  compatibility with synaptics Xorg / Xfree drivers.
+
 config MAC_EMUMOUSEBTN
 	bool "Support for mouse button 2+3 emulation"
 	help

```

---

