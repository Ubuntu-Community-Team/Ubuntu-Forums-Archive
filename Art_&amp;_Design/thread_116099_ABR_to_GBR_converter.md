---
title: "ABR to GBR converter"
date: 2006-01-11
forum: Art &amp; Design
---

### Post by Kelpie on 2006-01-11
after doing a frustering search i come accross ABR2GBR, but since there was NO readme file or any file whatsoever to tell me how to compile it i had no idea what to do, being the (sarcasm) smart cookie i am (/sarcasm) i did gcc abr2gbr.c and got the following:

```
root@Dementia:/home/amber/Desktop/src# gcc abr2gbr.c
abr2gbr.c:26:18: error: glib.h: No such file or directory
abr2gbr.c:40: error: syntax error before ‘gshort’
abr2gbr.c:40: warning: no semicolon at end of struct or union
abr2gbr.c:41: warning: data definition has no type or storage class
abr2gbr.c:46: error: syntax error before ‘gshort’
abr2gbr.c:46: warning: no semicolon at end of struct or union
abr2gbr.c:47: warning: data definition has no type or storage class
abr2gbr.c:52: error: syntax error before ‘gint32’
abr2gbr.c:52: warning: no semicolon at end of struct or union
abr2gbr.c:53: warning: data definition has no type or storage class
abr2gbr.c:54: error: syntax error before ‘antialiasing’
abr2gbr.c:54: warning: data definition has no type or storage class
abr2gbr.c:55: error: syntax error before ‘bounds’
abr2gbr.c:55: warning: data definition has no type or storage class
abr2gbr.c:56: error: syntax error before ‘bounds_long’
abr2gbr.c:56: warning: data definition has no type or storage class
abr2gbr.c:57: error: syntax error before ‘depth’
abr2gbr.c:57: warning: data definition has no type or storage class
abr2gbr.c:58: error: syntax error before ‘wide’
abr2gbr.c:58: warning: data definition has no type or storage class
abr2gbr.c:63: error: syntax error before ‘guint’
abr2gbr.c:63: warning: no semicolon at end of struct or union
abr2gbr.c:64: warning: data definition has no type or storage class
abr2gbr.c:65: error: syntax error before ‘width’
abr2gbr.c:65: warning: data definition has no type or storage class
abr2gbr.c:66: error: syntax error before ‘height’
abr2gbr.c:66: warning: data definition has no type or storage class
abr2gbr.c:67: error: syntax error before ‘depth’
abr2gbr.c:67: warning: data definition has no type or storage class
abr2gbr.c:68: error: syntax error before ‘magic_number’
abr2gbr.c:68: warning: data definition has no type or storage class
abr2gbr.c:69: error: syntax error before ‘spacing’
abr2gbr.c:69: warning: data definition has no type or storage class
abr2gbr.c:74: error: field ‘header’ has incomplete type
abr2gbr.c:75: error: syntax error before ‘gchar’
abr2gbr.c:75: warning: no semicolon at end of struct or union
abr2gbr.c:76: warning: data definition has no type or storage class
abr2gbr.c:77: error: syntax error before ‘*’ token
abr2gbr.c:77: warning: data definition has no type or storage class
abr2gbr.c:78: error: syntax error before ‘size’
abr2gbr.c:78: warning: data definition has no type or storage class
abr2gbr.c:82: error: syntax error before ‘abr_read_char’
abr2gbr.c:82: warning: data definition has no type or storage class
abr2gbr.c:83: error: syntax error before ‘abr_read_short’
abr2gbr.c:83: warning: data definition has no type or storage class
abr2gbr.c:84: error: syntax error before ‘abr_read_long’
abr2gbr.c:84: warning: data definition has no type or storage class
abr2gbr.c:85: error: syntax error before ‘*’ token
abr2gbr.c:87: error: syntax error before ‘*’ token
abr2gbr.c:89: error: syntax error before ‘main’
abr2gbr.c:89: error: syntax error before ‘argc’
abr2gbr.c:89: warning: data definition has no type or storage class
abr2gbr.c:93: error: syntax error before ‘abr_read_char’
abr2gbr.c:101: error: syntax error before ‘abr_read_short’
abr2gbr.c: In function ‘abr_read_short’:
abr2gbr.c:103: error: ‘gshort’ undeclared (first use in this function)
abr2gbr.c:103: error: (Each undeclared identifier is reported only once
abr2gbr.c:103: error: for each function it appears in.)
abr2gbr.c:103: error: syntax error before ‘val’
abr2gbr.c:107: error: ‘val’ undeclared (first use in this function)
abr2gbr.c: At top level:
abr2gbr.c:113: error: syntax error before ‘abr_read_long’
abr2gbr.c: In function ‘abr_read_long’:
abr2gbr.c:115: error: ‘gint32’ undeclared (first use in this function)
abr2gbr.c:115: error: syntax error before ‘val’
abr2gbr.c:119: error: ‘val’ undeclared (first use in this function)
abr2gbr.c: In function ‘abr_brush_load’:
abr2gbr.c:127: error: storage size of ‘abr_brush_hdr’ isn’t known
abr2gbr.c:145: error: storage size of ‘abr_sampled_brush_hdr’ isn’t known
abr2gbr.c:146: error: ‘gint’ undeclared (first use in this function)
abr2gbr.c:146: error: syntax error before ‘width’
abr2gbr.c:154: error: ‘i’ undeclared (first use in this function)
abr2gbr.c:172: error: syntax error before ‘GbrBrush’
abr2gbr.c:173: error: dereferencing pointer to incomplete type
abr2gbr.c:174: error: dereferencing pointer to incomplete type
abr2gbr.c:175: error: dereferencing pointer to incomplete type
abr2gbr.c:176: error: dereferencing pointer to incomplete type
abr2gbr.c:177: error: dereferencing pointer to incomplete type
abr2gbr.c:178: error: dereferencing pointer to incomplete type
abr2gbr.c:179: error: dereferencing pointer to incomplete type
abr2gbr.c:179: error: ‘gchar’ undeclared (first use in this function)
abr2gbr.c:180: error: dereferencing pointer to incomplete type
abr2gbr.c:184: error: ‘gshort’ undeclared (first use in this function)
abr2gbr.c:184: error: syntax error before ‘comp’
abr2gbr.c:186: error: ‘comp’ undeclared (first use in this function)
abr2gbr.c:191: error: dereferencing pointer to incomplete type
abr2gbr.c:193: error: ‘gint32’ undeclared (first use in this function)
abr2gbr.c:193: error: syntax error before ‘n’
abr2gbr.c:196: error: ‘cscanline_len’ undeclared (first use in this function)
abr2gbr.c:197: error: dereferencing pointer to incomplete type
abr2gbr.c:206: error: ‘j’ undeclared (first use in this function)
abr2gbr.c:207: error: ‘n’ undeclared (first use in this function)
abr2gbr.c:215: error: ‘ch’ undeclared (first use in this function)
abr2gbr.c:217: error: ‘c’ undeclared (first use in this function)
abr2gbr.c:221: error: ‘guchar’ undeclared (first use in this function)
abr2gbr.c:221: error: syntax error before ‘abr_read_char’
abr2gbr.c: In function ‘gbr_brush_free’:
abr2gbr.c:241: error: dereferencing pointer to incomplete type
abr2gbr.c:242: error: dereferencing pointer to incomplete type
abr2gbr.c:243: error: dereferencing pointer to incomplete type
abr2gbr.c: At top level:
abr2gbr.c:248: error: syntax error before ‘*’ token
abr2gbr.c: In function ‘abr_load’:
abr2gbr.c:251: error: storage size of ‘abr_hdr’ isn’t known
abr2gbr.c:253: error: ‘gint’ undeclared (first use in this function)
abr2gbr.c:253: error: syntax error before ‘i’
abr2gbr.c:255: error: ‘file’ undeclared (first use in this function)
abr2gbr.c:269: error: ‘i’ undeclared (first use in this function)
abr2gbr.c: At top level:
abr2gbr.c:284: error: syntax error before ‘*’ token
abr2gbr.c: In function ‘gbr_brush_save’:
abr2gbr.c:287: error: ‘gchar’ undeclared (first use in this function)
abr2gbr.c:287: error: ‘p’ undeclared (first use in this function)
abr2gbr.c:289: error: ‘file’ undeclared (first use in this function)
abr2gbr.c:290: error: ‘brush’ undeclared (first use in this function)
abr2gbr.c:293: error: ‘id’ undeclared (first use in this function)
abr2gbr.c:299: error: invalid application of ‘sizeof’ to incomplete type ‘GbrBrushHeader’
abr2gbr.c:302: error: invalid application of ‘sizeof’ to incomplete type ‘GbrBrushHeader’
abr2gbr.c:306: error: invalid application of ‘sizeof’ to incomplete type ‘GbrBrushHeader’
abr2gbr.c: At top level:
abr2gbr.c:312: error: syntax error before ‘main’
abr2gbr.c:312: error: syntax error before ‘argc’
abr2gbr.c: In function ‘main’:
abr2gbr.c:314: error: ‘gint’ undeclared (first use in this function)
abr2gbr.c:314: error: syntax error before ‘i’
abr2gbr.c:316: error: ‘argc’ undeclared (first use in this function)
abr2gbr.c:317: error: ‘argv’ undeclared (first use in this function)
abr2gbr.c:321: error: ‘i’ undeclared (first use in this function)
root@Dementia:/home/amber/Desktop/src#

```

So i tried g++ and got: 
```

root@Dementia:/home/amber/Desktop/src# g++ abr2gbr.c
abr2gbr.c:26:18: error: glib.h: No such file or directory
abr2gbr.c:40: error: ‘gshort’ does not name a type
abr2gbr.c:41: error: ‘gshort’ does not name a type
abr2gbr.c:46: error: ‘gshort’ does not name a type
abr2gbr.c:47: error: ‘gint32’ does not name a type
abr2gbr.c:52: error: ‘gint32’ does not name a type
abr2gbr.c:53: error: ‘gshort’ does not name a type
abr2gbr.c:54: error: ‘gchar’ does not name a type
abr2gbr.c:55: error: ‘gshort’ does not name a type
abr2gbr.c:56: error: ‘gint32’ does not name a type
abr2gbr.c:57: error: ‘gshort’ does not name a type
abr2gbr.c:58: error: ‘gboolean’ does not name a type
abr2gbr.c:63: error: ‘guint’ does not name a type
abr2gbr.c:64: error: ‘guint’ does not name a type
abr2gbr.c:65: error: ‘guint’ does not name a type
abr2gbr.c:66: error: ‘guint’ does not name a type
abr2gbr.c:67: error: ‘guint’ does not name a type
abr2gbr.c:68: error: ‘guint’ does not name a type
abr2gbr.c:69: error: ‘guint’ does not name a type
abr2gbr.c:75: error: ISO C++ forbids declaration of ‘gchar’ with no type
abr2gbr.c:75: error: expected ‘;’ before ‘*’ token
abr2gbr.c:76: error: ISO C++ forbids declaration of ‘gchar’ with no type
abr2gbr.c:76: error: expected ‘;’ before ‘*’ token
abr2gbr.c:77: error: ISO C++ forbids declaration of ‘gchar’ with no type
abr2gbr.c:77: error: expected ‘;’ before ‘*’ token
abr2gbr.c:78: error: ‘gint’ does not name a type
abr2gbr.c:82: error: ‘gchar’ does not name a type
abr2gbr.c:83: error: ‘gshort’ does not name a type
abr2gbr.c:84: error: ‘gint32’ does not name a type
abr2gbr.c:85: error: expected ‘,’ or ‘...’ before ‘*’ token
abr2gbr.c:85: error: ISO C++ forbids declaration of ‘gchar’ with no type
abr2gbr.c:87: error: expected ‘,’ or ‘...’ before ‘*’ token
abr2gbr.c:87: error: ISO C++ forbids declaration of ‘gchar’ with no type
abr2gbr.c:89: error: ‘gint’ does not name a type
abr2gbr.c:92: error: ‘gchar’ does not name a type
abr2gbr.c:100: error: ‘gshort’ does not name a type
abr2gbr.c:112: error: ‘gint32’ does not name a type
abr2gbr.c: In function ‘GbrBrush* abr_brush_load(FILE*)’:
abr2gbr.c:130: error: ‘g_return_val_if_fail’ was not declared in this scope
abr2gbr.c:132: error: ‘struct AbrBrushHeader’ has no member named ‘type’
abr2gbr.c:132: error: ‘abr_read_short’ was not declared in this scope
abr2gbr.c:133: error: ‘struct AbrBrushHeader’ has no member named ‘size’
abr2gbr.c:133: error: ‘abr_read_long’ was not declared in this scope
abr2gbr.c:135: error: ‘struct AbrBrushHeader’ has no member named ‘type’
abr2gbr.c:135: error: ‘struct AbrBrushHeader’ has no member named ‘size’
abr2gbr.c:135: error: ‘g_print’ was not declared in this scope
abr2gbr.c:137: error: ‘struct AbrBrushHeader’ has no member named ‘type’
abr2gbr.c:141: error: ‘struct AbrBrushHeader’ has no member named ‘size’
abr2gbr.c:146: error: ‘gint’ was not declared in this scope
abr2gbr.c:146: error: expected `;' before ‘width’
abr2gbr.c:147: error: expected `;' before ‘size’
abr2gbr.c:148: error: expected `;' before ‘i’
abr2gbr.c:150: error: ‘struct AbrSampledBrushHeader’ has no member named ‘misc’
abr2gbr.c:151: error: ‘struct AbrSampledBrushHeader’ has no member named ‘spacing’
abr2gbr.c:152: error: ‘struct AbrSampledBrushHeader’ has no member named ‘antialiasing’
abr2gbr.c:152: error: ‘abr_read_char’ was not declared in this scope
abr2gbr.c:154: error: ‘i’ was not declared in this scope
abr2gbr.c:155: error: ‘struct AbrSampledBrushHeader’ has no member named ‘bounds’
abr2gbr.c:157: error: ‘struct AbrSampledBrushHeader’ has no member named ‘bounds_long’
abr2gbr.c:159: error: ‘struct AbrSampledBrushHeader’ has no member named ‘depth’abr2gbr.c:161: error: ‘height’ was not declared in this scope
abr2gbr.c:161: error: ‘struct AbrSampledBrushHeader’ has no member named ‘bounds_long’
abr2gbr.c:162: error: ‘struct AbrSampledBrushHeader’ has no member named ‘bounds_long’
abr2gbr.c:163: error: ‘width’ was not declared in this scope
abr2gbr.c:163: error: ‘struct AbrSampledBrushHeader’ has no member named ‘bounds_long’
abr2gbr.c:164: error: ‘struct AbrSampledBrushHeader’ has no member named ‘bounds_long’
abr2gbr.c:165: error: ‘size’ was not declared in this scope
abr2gbr.c:165: error: ‘struct AbrSampledBrushHeader’ has no member named ‘depth’abr2gbr.c:168: error: ‘struct AbrSampledBrushHeader’ has no member named ‘wide’
abr2gbr.c:169: error: ‘struct AbrSampledBrushHeader’ has no member named ‘wide’
abr2gbr.c:172: error: expected primary-expression before ‘,’ token
abr2gbr.c:172: error: ‘g_new0’ was not declared in this scope
abr2gbr.c:173: error: ‘struct GbrBrushHeader’ has no member named ‘version’
abr2gbr.c:173: error: ‘g_htonl’ was not declared in this scope
abr2gbr.c:174: error: ‘struct GbrBrushHeader’ has no member named ‘width’
abr2gbr.c:175: error: ‘struct GbrBrushHeader’ has no member named ‘height’
abr2gbr.c:176: error: ‘struct GbrBrushHeader’ has no member named ‘depth’
abr2gbr.c:176: error: ‘struct AbrSampledBrushHeader’ has no member named ‘depth’abr2gbr.c:177: error: ‘struct GbrBrushHeader’ has no member named ‘magic_number’abr2gbr.c:178: error: ‘struct GbrBrushHeader’ has no member named ‘spacing’
abr2gbr.c:178: error: ‘struct AbrSampledBrushHeader’ has no member named ‘spacing’
abr2gbr.c:179: error: ‘struct _GbrBrush’ has no member named ‘data’
abr2gbr.c:179: error: ‘gchar’ was not declared in this scope
abr2gbr.c:180: error: ‘struct _GbrBrush’ has no member named ‘size’
abr2gbr.c:184: error: ‘gshort’ was not declared in this scope
abr2gbr.c:184: error: expected `;' before ‘comp’
abr2gbr.c:186: error: ‘comp’ was not declared in this scope
abr2gbr.c:188: error: ‘struct AbrSampledBrushHeader’ has no member named ‘depth’abr2gbr.c:191: error: ‘struct _GbrBrush’ has no member named ‘data’
abr2gbr.c:193: error: ‘gint32’ was not declared in this scope
abr2gbr.c:193: error: expected `;' before ‘n’
abr2gbr.c:194: error: expected `;' before ‘ch’
abr2gbr.c:195: error: expected `;' before ‘i’
abr2gbr.c:196: error: ‘cscanline_len’ was not declared in this scope
abr2gbr.c:197: error: ‘data’ was not declared in this scope
abr2gbr.c:197: error: ‘struct _GbrBrush’ has no member named ‘data’
abr2gbr.c:206: error: ‘j’ was not declared in this scope
abr2gbr.c:207: error: ‘n’ was not declared in this scope
abr2gbr.c:215: error: ‘ch’ was not declared in this scope
abr2gbr.c:217: error: ‘c’ was not declared in this scope
abr2gbr.c:220: error: ‘c’ was not declared in this scope
abr2gbr.c:221: error: ‘guchar’ was not declared in this scope
abr2gbr.c:221: error: expected `;' before ‘abr_read_char’
abr2gbr.c:225: error: ‘g_free’ was not declared in this scope
abr2gbr.c:232: error: ‘struct AbrBrushHeader’ has no member named ‘size’
abr2gbr.c: In function ‘void gbr_brush_free(GbrBrush*)’:
abr2gbr.c:241: error: ‘struct _GbrBrush’ has no member named ‘name’
abr2gbr.c:241: error: ‘g_free’ was not declared in this scope
abr2gbr.c:242: error: ‘struct _GbrBrush’ has no member named ‘description’
abr2gbr.c:243: error: ‘struct _GbrBrush’ has no member named ‘data’
abr2gbr.c: At global scope:
abr2gbr.c:248: error: expected ‘,’ or ‘...’ before ‘*’ token
abr2gbr.c:248: error: ISO C++ forbids declaration of ‘gchar’ with no type
abr2gbr.c: In function ‘void abr_load(int)’:
abr2gbr.c:253: error: ‘gint’ was not declared in this scope
abr2gbr.c:253: error: expected `;' before ‘i’
abr2gbr.c:255: error: ‘file’ was not declared in this scope
abr2gbr.c:256: error: ‘g_print’ was not declared in this scope
abr2gbr.c:260: error: ‘struct AbrHeader’ has no member named ‘version’
abr2gbr.c:260: error: ‘abr_read_short’ was not declared in this scope
abr2gbr.c:261: error: ‘struct AbrHeader’ has no member named ‘count’
abr2gbr.c:264: error: ‘file’ was not declared in this scope
abr2gbr.c:264: error: ‘struct AbrHeader’ has no member named ‘version’
abr2gbr.c:264: error: ‘struct AbrHeader’ has no member named ‘count’
abr2gbr.c:264: error: ‘g_print’ was not declared in this scope
abr2gbr.c:266: error: ‘struct AbrHeader’ has no member named ‘version’
abr2gbr.c:267: error: ‘struct AbrHeader’ has no member named ‘version’
abr2gbr.c:269: error: ‘i’ was not declared in this scope
abr2gbr.c:269: error: ‘struct AbrHeader’ has no member named ‘count’
abr2gbr.c: At global scope:
abr2gbr.c:284: error: expected ‘,’ or ‘...’ before ‘*’ token
abr2gbr.c:284: error: ISO C++ forbids declaration of ‘gchar’ with no type
abr2gbr.c: In function ‘void gbr_brush_save(GbrBrush*, int)’:
abr2gbr.c:287: error: ‘p’ was not declared in this scope
abr2gbr.c:289: error: ‘file’ was not declared in this scope
abr2gbr.c:290: error: ‘struct _GbrBrush’ has no member named ‘name’
abr2gbr.c:290: error: ‘g_strndup’ was not declared in this scope
abr2gbr.c:292: error: ‘struct _GbrBrush’ has no member named ‘name’
abr2gbr.c:293: error: ‘struct _GbrBrush’ has no member named ‘name’
abr2gbr.c:293: error: ‘id’ was not declared in this scope
abr2gbr.c:293: error: ‘g_strdup_printf’ was not declared in this scope
abr2gbr.c:294: error: ‘struct _GbrBrush’ has no member named ‘description’
abr2gbr.c:295: error: ‘g_free’ was not declared in this scope
abr2gbr.c:299: error: ‘struct GbrBrushHeader’ has no member named ‘header_size’
abr2gbr.c:300: error: ‘struct _GbrBrush’ has no member named ‘description’
abr2gbr.c:300: error: ‘g_htonl’ was not declared in this scope
abr2gbr.c:301: error: ‘struct _GbrBrush’ has no member named ‘name’
abr2gbr.c:303: error: ‘struct _GbrBrush’ has no member named ‘description’
abr2gbr.c:303: error: ‘struct _GbrBrush’ has no member named ‘description’
abr2gbr.c:304: error: ‘struct _GbrBrush’ has no member named ‘data’
abr2gbr.c:304: error: ‘struct _GbrBrush’ has no member named ‘size’
abr2gbr.c:305: error: ‘struct _GbrBrush’ has no member named ‘name’
abr2gbr.c:306: error: ‘struct _GbrBrush’ has no member named ‘size’
abr2gbr.c:306: error: ‘struct _GbrBrush’ has no member named ‘description’
abr2gbr.c:306: error: ‘g_print’ was not declared in this scope
abr2gbr.c: At global scope:
abr2gbr.c:311: error: ‘gint’ does not name a type

```


me not knowing what im doing and this having NO readme file in it i couldnt help but explode.

i really like to use GIMP, and i like some of the brushes people make for PS, but i dont have a windows os...

So to save me the trouble, if any of you know of one for linux... that has a readme... i would be greatful... i have not the greatest memory for my age, so things like compiling stuff is still something "new" to me

Thanks much
~Amber

---

### Post by TheGrudge on 2006-01-12
You have to install the following package:
```
sudo wajig install libglib1.2-dev
```

I had only glib2.0 installed but this version seems not to work with the source code.

---

