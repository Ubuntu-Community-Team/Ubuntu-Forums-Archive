---
title: "problemes en samsung ML2240"
date: 2010-07-02
forum: Catalan Team
---

### Post by xavi67 on 2010-07-02
Tinc ubuntu 10.04 i no puc imprimir amb una samsung ML2240 he buscat informació per la web i pareix que siga un problema de filtres però no sé com fer el que em diu:    	
No sé per on començar a fer tot el que ahí diu. Algú em pot ajudar?

	 	 	 	 	  The samsung filter ppmtospl2 is incompatible with newer Linux
distributions. The problem has been reported with RedHat v9 and
Mandrake (now Mandriva) "Cooker" (around version 9.1).  
 This is likely a library error, but may lie in the binary itself.
There is no known solution. There are two possible solutions you
can try.  
 First, try using the free [[1]]("http://www.openprinting.org/smart")gdi ghostscript driver.
ppmtospl2 should start working. This requires using
ESP GhostScript.  
 Second, you can try to load the ppmtospl2 script by preloading old
libraries. First, obtain the old libraries that are needed. These
are libnss_files.so.2, libc.so.6 and ld-linux.so.2. Next,
edit the ld-linux.so.2 library and and change all
instances of the string /lib/ld-linux.so.2 to /lib/ld-smsng.so.2.
Very Important: The new name of the library (/lib/ld-smsng.so.2
must be exactly the same length as the old name /lib/ld-linux.so.2, or
the binary will not work anymore.
Then copy your old ld-linux.so.2 to lib/test/ld-smsng.so.2. Finally,
set the environment variable LD_PRELOAD to point to the new library directory.
Now try to run the filter.

---

### Post by papapep on 2010-07-02
Has vist [aquesta]("http://omoudo.wordpress.com/2009/04/18/instalar-samsung-ml-2240-linux/") pàgina?

De fet, hi ha unes quantes pàgines que sembla que se n'han sortit: [http://ves.cat/ag8m](http://ves.cat/ag8m)

Espero que t'ajudi.

---

