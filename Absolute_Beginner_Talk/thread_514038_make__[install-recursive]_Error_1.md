---
title: "make: *** [install-recursive] Error 1"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by rasesh_raz on 2007-07-31
root@root:/home/system/bluez-hcidump-1.12# make install
Making install in parser
make[1]: Entering directory `/home/system/bluez-hcidump-1.12/parser'
gcc -DHAVE_CONFIG_H -I. -I. -I..    -I/usr/include -Wall -O2 -c `test -f 'sdp.c' || echo './'`sdp.c
sdp.c:39: error: static declaration of ‘sdp_siz_idx_lookup_table’ follows non-static declaration
sdp.h:160: error: previous declaration of ‘sdp_siz_idx_lookup_table’ was here
sdp.c:50: error: static declaration of ‘sdp_uuid_nam_lookup_table’ follows non-static declaration
sdp.h:167: error: previous declaration of ‘sdp_uuid_nam_lookup_table’ was here
sdp.c:104: error: static declaration of ‘sdp_attr_id_nam_lookup_table’ follows non-static declaration
sdp.h:176: error: previous declaration of ‘sdp_attr_id_nam_lookup_table’ was here
make[1]: *** [sdp.o] Error 1
make[1]: Leaving directory `/home/system/bluez-hcidump-1.12/parser'
make: *** [install-recursive] Error 1

---

### Post by sad_iq on 2007-07-31
Can you paste the **./configure** output as well maybe there were errors
 Also why do you try to compile an old version of bluez-hcidump?? Version **1.33** is in the repositorys!!!

---

