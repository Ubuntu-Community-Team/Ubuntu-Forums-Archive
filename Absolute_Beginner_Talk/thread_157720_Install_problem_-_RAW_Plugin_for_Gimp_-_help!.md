---
title: "Install problem - RAW Plugin for Gimp - help!"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by cliff0108 on 2006-04-09
I unpacked the tgz file to a subdirectory
The install instructions in the read-me say:
To install locally:
	gimptool --install rawphoto.c

  To install globally:
	gimptool --install-admin rawphoto.c

I go to the sub sub directory src that contains the files :
blackbody.h
makefile
rawphoto.c

and I let fly at the terminal with the following yucky result:
cliff@ubuntu:~/downloads/rawphoto-200410220910/src$ make install rawphoto.c
gcc -Wall -O0 -g  -c `gimptool --cflags`  rawphoto.c
/bin/sh: gimptool: command not found
rawphoto.c:118:21: error: gtk/gtk.h: No such file or directory
rawphoto.c:120:26: error: libgimp/gimp.h: No such file or directory
rawphoto.c:121:28: error: libgimp/gimpui.h: No such file or directory
rawphoto.c:146: warning: type defaults to ‘int’ in declaration of ‘gchar’
rawphoto.c:146: error: syntax error before ‘*’ token
rawphoto.c:152: error: syntax error before ‘load_dialog’
rawphoto.c:152: error: syntax error before ‘*’ token
rawphoto.c:152: warning: type defaults to ‘int’ in declaration of ‘load_dialog’rawphoto.c:152: warning: data definition has no type or storage class
rawphoto.c:153: error: syntax error before ‘load_image’
rawphoto.c:153: error: syntax error before ‘*’ token
rawphoto.c:153: warning: type defaults to ‘int’ in declaration of ‘load_image’rawphoto.c:153: warning: data definition has no type or storage class
rawphoto.c:160: error: syntax error before ‘PLUG_IN_INFO’
rawphoto.c:160: warning: type defaults to ‘int’ in declaration of ‘PLUG_IN_INFO’rawphoto.c:162: warning: initialization makes integer from pointer without a cast
rawphoto.c:163: warning: excess elements in scalar initializer
rawphoto.c:163: warning: (near initialization for ‘PLUG_IN_INFO’)
rawphoto.c:164: warning: excess elements in scalar initializer
rawphoto.c:164: warning: (near initialization for ‘PLUG_IN_INFO’)
rawphoto.c:165: warning: excess elements in scalar initializer
rawphoto.c:165: warning: (near initialization for ‘PLUG_IN_INFO’)
rawphoto.c:166: warning: data definition has no type or storage class
rawphoto.c:169: error: syntax error before ‘gboolean’
rawphoto.c:169: warning: no semicolon at end of struct or union
rawphoto.c:170: warning: type defaults to ‘int’ in declaration of ‘Temperature’rawphoto.c:170: warning: data definition has no type or storage class
rawphoto.c:171: error: syntax error before ‘Green’
rawphoto.c:171: warning: type defaults to ‘int’ in declaration of ‘Green’
rawphoto.c:171: warning: data definition has no type or storage class
rawphoto.c:172: error: syntax error before ‘Gamma’
rawphoto.c:172: warning: type defaults to ‘int’ in declaration of ‘Gamma’
rawphoto.c:172: warning: data definition has no type or storage class
rawphoto.c:173: error: syntax error before ‘Exposition’
rawphoto.c:173: warning: type defaults to ‘int’ in declaration of ‘Exposition’rawphoto.c:173: warning: data definition has no type or storage class
rawphoto.c:174: error: syntax error before ‘Black’
rawphoto.c:174: warning: type defaults to ‘int’ in declaration of ‘Black’
rawphoto.c:174: warning: data definition has no type or storage class
rawphoto.c:175: error: syntax error before ‘Dark’
rawphoto.c:175: warning: type defaults to ‘int’ in declaration of ‘Dark’
rawphoto.c:175: warning: data definition has no type or storage class
rawphoto.c:176: error: syntax error before ‘Saturation’
rawphoto.c:176: warning: type defaults to ‘int’ in declaration of ‘Saturation’rawphoto.c:176: warning: data definition has no type or storage class
rawphoto.c:177: error: syntax error before ‘OverExp’
rawphoto.c:177: warning: type defaults to ‘int’ in declaration of ‘OverExp’
rawphoto.c:177: warning: type defaults to ‘int’ in declaration of ‘ClipSat’
rawphoto.c:177: warning: type defaults to ‘int’ in declaration of ‘WBind’
rawphoto.c:177: warning: data definition has no type or storage class
rawphoto.c:178: error: syntax error before ‘Scale’
rawphoto.c:178: warning: type defaults to ‘int’ in declaration of ‘Scale’
rawphoto.c:178: warning: data definition has no type or storage class
rawphoto.c:179: warning: type defaults to ‘int’ in declaration of ‘cfg’
rawphoto.c:180: warning: braces around scalar initializer
rawphoto.c:180: warning: (near initialization for ‘cfg’)
rawphoto.c:180: error: ‘FALSE’ undeclared here (not in a function)
rawphoto.c:180: warning: excess elements in scalar initializer
rawphoto.c:180: warning: (near initialization for ‘cfg’)
rawphoto.c:180: warning: excess elements in scalar initializer
rawphoto.c:180: warning: (near initialization for ‘cfg’)
rawphoto.c:180: warning: excess elements in scalar initializer
rawphoto.c:180: warning: (near initialization for ‘cfg’)
rawphoto.c:180: warning: excess elements in scalar initializer
rawphoto.c:180: warning: (near initialization for ‘cfg’)
rawphoto.c:181: warning: excess elements in scalar initializer
rawphoto.c:181: warning: (near initialization for ‘cfg’)
rawphoto.c:181: warning: excess elements in scalar initializer
rawphoto.c:181: warning: (near initialization for ‘cfg’)
rawphoto.c:181: warning: excess elements in scalar initializer
rawphoto.c:181: warning: (near initialization for ‘cfg’)
rawphoto.c:181: warning: excess elements in scalar initializer
rawphoto.c:181: warning: (near initialization for ‘cfg’)
rawphoto.c:181: warning: excess elements in scalar initializer
rawphoto.c:181: warning: (near initialization for ‘cfg’)
rawphoto.c:181: warning: excess elements in scalar initializer
rawphoto.c:181: warning: (near initialization for ‘cfg’)
rawphoto.c:181: warning: excess elements in scalar initializer
rawphoto.c:181: warning: (near initialization for ‘cfg’)
rawphoto.c:181: error: ‘TRUE’ undeclared here (not in a function)
rawphoto.c:181: warning: excess elements in scalar initializer
rawphoto.c:181: warning: (near initialization for ‘cfg’)
rawphoto.c:181: warning: excess elements in scalar initializer
rawphoto.c:181: warning: (near initialization for ‘cfg’)
rawphoto.c:181: warning: excess elements in scalar initializer
rawphoto.c:181: warning: (near initialization for ‘cfg’)
rawphoto.c:182: warning: excess elements in scalar initializer
rawphoto.c:182: warning: (near initialization for ‘cfg’)
rawphoto.c:182: warning: data definition has no type or storage class
rawphoto.c:185: error: syntax error before ‘guint16’
rawphoto.c:185: warning: no semicolon at end of struct or union
rawphoto.c:186: warning: type defaults to ‘int’ in declaration of ‘rgb16’
rawphoto.c:186: warning: data definition has no type or storage class
rawphoto.c:188: error: syntax error before ‘*’ token
rawphoto.c:188: warning: type defaults to ‘int’ in declaration of ‘previewPixbuf’
rawphoto.c:188: warning: data definition has no type or storage class
rawphoto.c:189: error: syntax error before ‘*’ token
rawphoto.c:189: warning: type defaults to ‘int’ in declaration of ‘histoPixmap’rawphoto.c:189: warning: data definition has no type or storage class
rawphoto.c:190: error: syntax error before ‘*’ token
rawphoto.c:190: warning: type defaults to ‘int’ in declaration of ‘preview’
rawphoto.c:190: warning: type defaults to ‘int’ in declaration of ‘histo’
rawphoto.c:190: warning: data definition has no type or storage class
rawphoto.c:191: error: syntax error before ‘*’ token
rawphoto.c:191: warning: type defaults to ‘int’ in declaration of ‘ProgressBar’rawphoto.c:191: warning: data definition has no type or storage class
rawphoto.c:192: error: syntax error before ‘*’ token
rawphoto.c:192: warning: type defaults to ‘int’ in declaration of ‘rawBuf’
rawphoto.c:192: warning: data definition has no type or storage class
rawphoto.c:194: error: syntax error before ‘prevH’
rawphoto.c:194: warning: type defaults to ‘int’ in declaration of ‘prevH’
rawphoto.c:194: warning: type defaults to ‘int’ in declaration of ‘prevW’
rawphoto.c:194: warning: data definition has no type or storage class
rawphoto.c:195: error: syntax error before ‘LUT’
rawphoto.c:195: warning: type defaults to ‘int’ in declaration of ‘LUT’
rawphoto.c:195: warning: data definition has no type or storage class
rawphoto.c:196: error: syntax error before ‘curve’
rawphoto.c:196: warning: type defaults to ‘int’ in declaration of ‘curve’
rawphoto.c:196: warning: data definition has no type or storage class
rawphoto.c:197: error: syntax error before ‘maxR’
rawphoto.c:197: warning: type defaults to ‘int’ in declaration of ‘maxR’
rawphoto.c:197: warning: type defaults to ‘int’ in declaration of ‘maxG’
rawphoto.c:197: warning: type defaults to ‘int’ in declaration of ‘maxB’
rawphoto.c:197: warning: type defaults to ‘int’ in declaration of ‘minR’
rawphoto.c:197: warning: type defaults to ‘int’ in declaration of ‘minG’
rawphoto.c:197: warning: type defaults to ‘int’ in declaration of ‘minB’
rawphoto.c:197: warning: type defaults to ‘int’ in declaration of ‘minV’
rawphoto.c:197: warning: type defaults to ‘int’ in declaration of ‘maxV’
rawphoto.c:197: warning: data definition has no type or storage class
rawphoto.c:198: error: syntax error before ‘mr’
rawphoto.c:198: warning: type defaults to ‘int’ in declaration of ‘mr’
rawphoto.c:198: warning: type defaults to ‘int’ in declaration of ‘mg’
rawphoto.c:198: warning: type defaults to ‘int’ in declaration of ‘mb’
rawphoto.c:198: warning: data definition has no type or storage class
rawphoto.c:199: error: syntax error before ‘rgbMax’
rawphoto.c:199: warning: type defaults to ‘int’ in declaration of ‘rgbMax’
rawphoto.c:199: warning: data definition has no type or storage class
rawphoto.c:200: error: syntax error before ‘BP’
rawphoto.c:200: warning: type defaults to ‘int’ in declaration of ‘BP’
rawphoto.c:200: warning: type defaults to ‘int’ in declaration of ‘WP’
rawphoto.c:200: warning: data definition has no type or storage class
rawphoto.c:202: error: syntax error before ‘*’ token
rawphoto.c:202: warning: type defaults to ‘int’ in declaration of ‘adjTemperature’
rawphoto.c:203: warning: type defaults to ‘int’ in declaration of ‘adjExposition’
rawphoto.c:204: warning: type defaults to ‘int’ in declaration of ‘adjGamma’rawphoto.c:205: warning: type defaults to ‘int’ in declaration of ‘adjGreen’rawphoto.c:206: warning: type defaults to ‘int’ in declaration of ‘adjBlack’rawphoto.c:207: warning: type defaults to ‘int’ in declaration of ‘adjDark’
rawphoto.c:208: warning: type defaults to ‘int’ in declaration of ‘adjSaturation’
rawphoto.c:208: warning: data definition has no type or storage class
rawphoto.c:210: error: syntax error before ‘*’ token
rawphoto.c:210: warning: type defaults to ‘int’ in declaration of ‘fileName’rawphoto.c:210: warning: data definition has no type or storage class
rawphoto.c:215: error: syntax error before ‘histogramR’
rawphoto.c:215: warning: type defaults to ‘int’ in declaration of ‘histogramR’rawphoto.c:215: warning: data definition has no type or storage class
rawphoto.c:218: error: syntax error before ‘histogramRGB’
rawphoto.c:218: warning: type defaults to ‘int’ in declaration of ‘histogramRGB’rawphoto.c:218: warning: data definition has no type or storage class
rawphoto.c:227: warning: return type defaults to ‘int’
rawphoto.c: In function ‘MAIN’:
rawphoto.c:228: error: storage class specified for parameter ‘query’
rawphoto.c:228: error: syntax error before ‘{’ token
rawphoto.c:235: warning: type defaults to ‘int’ in declaration of ‘GimpParamDef’rawphoto.c:235: error: storage class specified for parameter ‘GimpParamDef’
rawphoto.c:235: error: syntax error before ‘load_return_vals’
rawphoto.c:240: warning: type defaults to ‘int’ in declaration of ‘gint’
rawphoto.c:240: error: storage class specified for parameter ‘gint’
rawphoto.c:240: error: syntax error before ‘num_load_args’
rawphoto.c:242: warning: type defaults to ‘int’ in declaration of ‘gint’
rawphoto.c:242: error: storage class specified for parameter ‘gint’
rawphoto.c:242: error: redefinition of parameter ‘gint’
rawphoto.c:240: error: previous definition of ‘gint’ was here
rawphoto.c:242: error: syntax error before ‘num_load_return_vals’
rawphoto.c:277: error: syntax error before ‘*’ token
rawphoto.c:401: error: syntax error before ‘gint32’
rawphoto.c:408: error: syntax error before ‘gdouble’
rawphoto.c:753: error: redefinition of parameter ‘command’
rawphoto.c:407: error: previous definition of ‘command’ was here
rawphoto.c:753: error: redefinition of parameter ‘nl’
rawphoto.c:407: error: previous definition of ‘nl’ was here
rawphoto.c:755: error: syntax error before ‘guint16’
rawphoto.c:942: error: syntax error before ‘{’ token
rawphoto.c:1043: error: storage class specified for parameter ‘label’
rawphoto.c:1043: error: parameter ‘label’ is initialized
rawphoto.c:1044: warning: initialization from incompatible pointer type
rawphoto.c:1044: warning: excess elements in scalar initializer
rawphoto.c:1044: warning: (near initialization for ‘label’)
rawphoto.c:1045: warning: excess elements in scalar initializer
rawphoto.c:1045: warning: (near initialization for ‘label’)
rawphoto.c:1045: warning: excess elements in scalar initializer
rawphoto.c:1045: warning: (near initialization for ‘label’)
rawphoto.c:1045: warning: excess elements in scalar initializer
rawphoto.c:1045: warning: (near initialization for ‘label’)
rawphoto.c:1046: warning: excess elements in scalar initializer
rawphoto.c:1046: warning: (near initialization for ‘label’)
rawphoto.c:1046: warning: excess elements in scalar initializer
rawphoto.c:1046: warning: (near initialization for ‘label’)
rawphoto.c:1046: warning: excess elements in scalar initializer
rawphoto.c:1046: warning: (near initialization for ‘label’)
rawphoto.c:1046: warning: excess elements in scalar initializer
rawphoto.c:1046: warning: (near initialization for ‘label’)
rawphoto.c:1048: error: syntax error before ‘fileName’
make: *** [rawphoto.o] Error 1
cliff@ubuntu:~/downloads/rawphoto-200410220910/src$ sudo -- make install rawphoto.c
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
cliff@ubuntu:~/downloads/rawphoto-200410220910/src$ sudo  make install rawphoto.c
Password:
gcc -Wall -O0 -g  -c `gimptool --cflags`  rawphoto.c
/bin/sh: gimptool: command not found
rawphoto.c:118:21: error: gtk/gtk.h: No such file or directory
rawphoto.c:120:26: error: libgimp/gimp.h: No such file or directory
rawphoto.c:121:28: error: libgimp/gimpui.h: No such file or directory
rawphoto.c:146: warning: type defaults to ‘int’ in declaration of ‘gchar’
rawphoto.c:146: error: syntax error before ‘*’ token
rawphoto.c:152: error: syntax error before ‘load_dialog’
rawphoto.c:152: error: syntax error before ‘*’ token
rawphoto.c:152: warning: type defaults to ‘int’ in declaration of ‘load_dialog’
rawphoto.c:152: warning: data definition has no type or storage class
rawphoto.c:153: error: syntax error before ‘load_image’
rawphoto.c:153: error: syntax error before ‘*’ token
rawphoto.c:153: warning: type defaults to ‘int’ in declaration of ‘load_image’
rawphoto.c:153: warning: data definition has no type or storage class
rawphoto.c:160: error: syntax error before ‘PLUG_IN_INFO’
rawphoto.c:160: warning: type defaults to ‘int’ in declaration of ‘PLUG_IN_INFO’
rawphoto.c:162: warning: initialization makes integer from pointer without a cast
rawphoto.c:163: warning: excess elements in scalar initializer
rawphoto.c:163: warning: (near initialization for ‘PLUG_IN_INFO’)
rawphoto.c:164: warning: excess elements in scalar initializer
rawphoto.c:164: warning: (near initialization for ‘PLUG_IN_INFO’)
rawphoto.c:165: warning: excess elements in scalar initializer
rawphoto.c:165: warning: (near initialization for ‘PLUG_IN_INFO’)
rawphoto.c:166: warning: data definition has no type or storage class
rawphoto.c:169: error: syntax error before ‘gboolean’
rawphoto.c:169: warning: no semicolon at end of struct or union
rawphoto.c:170: warning: type defaults to ‘int’ in declaration of ‘Temperature’
rawphoto.c:170: warning: data definition has no type or storage class
rawphoto.c:171: error: syntax error before ‘Green’
rawphoto.c:171: warning: type defaults to ‘int’ in declaration of ‘Green’
rawphoto.c:171: warning: data definition has no type or storage class
rawphoto.c:172: error: syntax error before ‘Gamma’
rawphoto.c:172: warning: type defaults to ‘int’ in declaration of ‘Gamma’
rawphoto.c:172: warning: data definition has no type or storage class
rawphoto.c:173: error: syntax error before ‘Exposition’
rawphoto.c:173: warning: type defaults to ‘int’ in declaration of ‘Exposition’
rawphoto.c:173: warning: data definition has no type or storage class
rawphoto.c:174: error: syntax error before ‘Black’
rawphoto.c:174: warning: type defaults to ‘int’ in declaration of ‘Black’
rawphoto.c:174: warning: data definition has no type or storage class
rawphoto.c:175: error: syntax error before ‘Dark’
rawphoto.c:175: warning: type defaults to ‘int’ in declaration of ‘Dark’
rawphoto.c:175: warning: data definition has no type or storage class
rawphoto.c:176: error: syntax error before ‘Saturation’
rawphoto.c:176: warning: type defaults to ‘int’ in declaration of ‘Saturation’
rawphoto.c:176: warning: data definition has no type or storage class
rawphoto.c:177: error: syntax error before ‘OverExp’
rawphoto.c:177: warning: type defaults to ‘int’ in declaration of ‘OverExp’
rawphoto.c:177: warning: type defaults to ‘int’ in declaration of ‘ClipSat’
rawphoto.c:177: warning: type defaults to ‘int’ in declaration of ‘WBind’
rawphoto.c:177: warning: data definition has no type or storage class
rawphoto.c:178: error: syntax error before ‘Scale’
rawphoto.c:178: warning: type defaults to ‘int’ in declaration of ‘Scale’
rawphoto.c:178: warning: data definition has no type or storage class
rawphoto.c:179: warning: type defaults to ‘int’ in declaration of ‘cfg’
rawphoto.c:180: warning: braces around scalar initializer
rawphoto.c:180: warning: (near initialization for ‘cfg’)
rawphoto.c:180: error: ‘FALSE’ undeclared here (not in a function)
rawphoto.c:180: warning: excess elements in scalar initializer
rawphoto.c:180: warning: (near initialization for ‘cfg’)
rawphoto.c:180: warning: excess elements in scalar initializer
rawphoto.c:180: warning: (near initialization for ‘cfg’)
rawphoto.c:180: warning: excess elements in scalar initializer
rawphoto.c:180: warning: (near initialization for ‘cfg’)
rawphoto.c:180: warning: excess elements in scalar initializer
rawphoto.c:180: warning: (near initialization for ‘cfg’)
rawphoto.c:181: warning: excess elements in scalar initializer
rawphoto.c:181: warning: (near initialization for ‘cfg’)
rawphoto.c:181: warning: excess elements in scalar initializer
rawphoto.c:181: warning: (near initialization for ‘cfg’)
rawphoto.c:181: warning: excess elements in scalar initializer
rawphoto.c:181: warning: (near initialization for ‘cfg’)
rawphoto.c:181: warning: excess elements in scalar initializer
rawphoto.c:181: warning: (near initialization for ‘cfg’)
rawphoto.c:181: warning: excess elements in scalar initializer
rawphoto.c:181: warning: (near initialization for ‘cfg’)
rawphoto.c:181: warning: excess elements in scalar initializer
rawphoto.c:181: warning: (near initialization for ‘cfg’)
rawphoto.c:181: warning: excess elements in scalar initializer
rawphoto.c:181: warning: (near initialization for ‘cfg’)
rawphoto.c:181: error: ‘TRUE’ undeclared here (not in a function)
rawphoto.c:181: warning: excess elements in scalar initializer
rawphoto.c:181: warning: (near initialization for ‘cfg’)
rawphoto.c:181: warning: excess elements in scalar initializer
rawphoto.c:181: warning: (near initialization for ‘cfg’)
rawphoto.c:181: warning: excess elements in scalar initializer
rawphoto.c:181: warning: (near initialization for ‘cfg’)
rawphoto.c:182: warning: excess elements in scalar initializer
rawphoto.c:182: warning: (near initialization for ‘cfg’)
rawphoto.c:182: warning: data definition has no type or storage class
rawphoto.c:185: error: syntax error before ‘guint16’
rawphoto.c:185: warning: no semicolon at end of struct or union
rawphoto.c:186: warning: type defaults to ‘int’ in declaration of ‘rgb16’
rawphoto.c:186: warning: data definition has no type or storage class
rawphoto.c:188: error: syntax error before ‘*’ token
rawphoto.c:188: warning: type defaults to ‘int’ in declaration of ‘previewPixbuf’
rawphoto.c:188: warning: data definition has no type or storage class
rawphoto.c:189: error: syntax error before ‘*’ token
rawphoto.c:189: warning: type defaults to ‘int’ in declaration of ‘histoPixmap’
rawphoto.c:189: warning: data definition has no type or storage class
rawphoto.c:190: error: syntax error before ‘*’ token
rawphoto.c:190: warning: type defaults to ‘int’ in declaration of ‘preview’
rawphoto.c:190: warning: type defaults to ‘int’ in declaration of ‘histo’
rawphoto.c:190: warning: data definition has no type or storage class
rawphoto.c:191: error: syntax error before ‘*’ token
rawphoto.c:191: warning: type defaults to ‘int’ in declaration of ‘ProgressBar’
rawphoto.c:191: warning: data definition has no type or storage class
rawphoto.c:192: error: syntax error before ‘*’ token
rawphoto.c:192: warning: type defaults to ‘int’ in declaration of ‘rawBuf’
rawphoto.c:192: warning: data definition has no type or storage class
rawphoto.c:194: error: syntax error before ‘prevH’
rawphoto.c:194: warning: type defaults to ‘int’ in declaration of ‘prevH’
rawphoto.c:194: warning: type defaults to ‘int’ in declaration of ‘prevW’
rawphoto.c:194: warning: data definition has no type or storage class
rawphoto.c:195: error: syntax error before ‘LUT’
rawphoto.c:195: warning: type defaults to ‘int’ in declaration of ‘LUT’
rawphoto.c:195: warning: data definition has no type or storage class
rawphoto.c:196: error: syntax error before ‘curve’
rawphoto.c:196: warning: type defaults to ‘int’ in declaration of ‘curve’
rawphoto.c:196: warning: data definition has no type or storage class
rawphoto.c:197: error: syntax error before ‘maxR’
rawphoto.c:197: warning: type defaults to ‘int’ in declaration of ‘maxR’
rawphoto.c:197: warning: type defaults to ‘int’ in declaration of ‘maxG’
rawphoto.c:197: warning: type defaults to ‘int’ in declaration of ‘maxB’
rawphoto.c:197: warning: type defaults to ‘int’ in declaration of ‘minR’
rawphoto.c:197: warning: type defaults to ‘int’ in declaration of ‘minG’
rawphoto.c:197: warning: type defaults to ‘int’ in declaration of ‘minB’
rawphoto.c:197: warning: type defaults to ‘int’ in declaration of ‘minV’
rawphoto.c:197: warning: type defaults to ‘int’ in declaration of ‘maxV’
rawphoto.c:197: warning: data definition has no type or storage class
rawphoto.c:198: error: syntax error before ‘mr’
rawphoto.c:198: warning: type defaults to ‘int’ in declaration of ‘mr’
rawphoto.c:198: warning: type defaults to ‘int’ in declaration of ‘mg’
rawphoto.c:198: warning: type defaults to ‘int’ in declaration of ‘mb’
rawphoto.c:198: warning: data definition has no type or storage class
rawphoto.c:199: error: syntax error before ‘rgbMax’
rawphoto.c:199: warning: type defaults to ‘int’ in declaration of ‘rgbMax’
rawphoto.c:199: warning: data definition has no type or storage class
rawphoto.c:200: error: syntax error before ‘BP’
rawphoto.c:200: warning: type defaults to ‘int’ in declaration of ‘BP’
rawphoto.c:200: warning: type defaults to ‘int’ in declaration of ‘WP’
rawphoto.c:200: warning: data definition has no type or storage class
rawphoto.c:202: error: syntax error before ‘*’ token
rawphoto.c:202: warning: type defaults to ‘int’ in declaration of ‘adjTemperature’
rawphoto.c:203: warning: type defaults to ‘int’ in declaration of ‘adjExposition’
rawphoto.c:204: warning: type defaults to ‘int’ in declaration of ‘adjGamma’rawphoto.c:205: warning: type defaults to ‘int’ in declaration of ‘adjGreen’rawphoto.c:206: warning: type defaults to ‘int’ in declaration of ‘adjBlack’rawphoto.c:207: warning: type defaults to ‘int’ in declaration of ‘adjDark’
rawphoto.c:208: warning: type defaults to ‘int’ in declaration of ‘adjSaturation’
rawphoto.c:208: warning: data definition has no type or storage class
rawphoto.c:210: error: syntax error before ‘*’ token
rawphoto.c:210: warning: type defaults to ‘int’ in declaration of ‘fileName’rawphoto.c:210: warning: data definition has no type or storage class
rawphoto.c:215: error: syntax error before ‘histogramR’
rawphoto.c:215: warning: type defaults to ‘int’ in declaration of ‘histogramR’
rawphoto.c:215: warning: data definition has no type or storage class
rawphoto.c:218: error: syntax error before ‘histogramRGB’
rawphoto.c:218: warning: type defaults to ‘int’ in declaration of ‘histogramRGB’
rawphoto.c:218: warning: data definition has no type or storage class
rawphoto.c:227: warning: return type defaults to ‘int’
rawphoto.c: In function ‘MAIN’:
rawphoto.c:228: error: storage class specified for parameter ‘query’
rawphoto.c:228: error: syntax error before ‘{’ token
rawphoto.c:235: warning: type defaults to ‘int’ in declaration of ‘GimpParamDef’
rawphoto.c:235: error: storage class specified for parameter ‘GimpParamDef’
rawphoto.c:235: error: syntax error before ‘load_return_vals’
rawphoto.c:240: warning: type defaults to ‘int’ in declaration of ‘gint’
rawphoto.c:240: error: storage class specified for parameter ‘gint’
rawphoto.c:240: error: syntax error before ‘num_load_args’
rawphoto.c:242: warning: type defaults to ‘int’ in declaration of ‘gint’
rawphoto.c:242: error: storage class specified for parameter ‘gint’
rawphoto.c:242: error: redefinition of parameter ‘gint’
rawphoto.c:240: error: previous definition of ‘gint’ was here
rawphoto.c:242: error: syntax error before ‘num_load_return_vals’
rawphoto.c:277: error: syntax error before ‘*’ token
rawphoto.c:401: error: syntax error before ‘gint32’
rawphoto.c:408: error: syntax error before ‘gdouble’
rawphoto.c:753: error: redefinition of parameter ‘command’
rawphoto.c:407: error: previous definition of ‘command’ was here
rawphoto.c:753: error: redefinition of parameter ‘nl’
rawphoto.c:407: error: previous definition of ‘nl’ was here
rawphoto.c:755: error: syntax error before ‘guint16’
rawphoto.c:942: error: syntax error before ‘{’ token
rawphoto.c:1043: error: storage class specified for parameter ‘label’
rawphoto.c:1043: error: parameter ‘label’ is initialized
rawphoto.c:1044: warning: initialization from incompatible pointer type
rawphoto.c:1044: warning: excess elements in scalar initializer
rawphoto.c:1044: warning: (near initialization for ‘label’)
rawphoto.c:1045: warning: excess elements in scalar initializer
rawphoto.c:1045: warning: (near initialization for ‘label’)
rawphoto.c:1045: warning: excess elements in scalar initializer
rawphoto.c:1045: warning: (near initialization for ‘label’)
rawphoto.c:1045: warning: excess elements in scalar initializer
rawphoto.c:1045: warning: (near initialization for ‘label’)
rawphoto.c:1046: warning: excess elements in scalar initializer
rawphoto.c:1046: warning: (near initialization for ‘label’)
rawphoto.c:1046: warning: excess elements in scalar initializer
rawphoto.c:1046: warning: (near initialization for ‘label’)
rawphoto.c:1046: warning: excess elements in scalar initializer
rawphoto.c:1046: warning: (near initialization for ‘label’)
rawphoto.c:1046: warning: excess elements in scalar initializer
rawphoto.c:1046: warning: (near initialization for ‘label’)
rawphoto.c:1048: error: syntax error before ‘fileName’
make: *** [rawphoto.o] Error 1

---

### Post by cliff0108 on 2006-04-09
Please ignore !
Solution is to install libgimp2.0.dev from Synaptic which loads a tool called gimptool-2.0 - which in turn, loads Gimp plugins.

---

