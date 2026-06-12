---
title: "QEMU for running MacOS as a &quot;guest&quot; on PPC hardware"
date: 2008-07-26
forum: Apple Hardware Users
---

### Post by mfox on 2008-07-26
I would like to be able to run Mac programs on my PowerBook without having to leave Ubuntu, and since the Mac-on-Linux program hasn't yet been patched to run on Hardy, I wondered whether QEMU could be used to do something similar.  The QEMU web page states that the program can run the Mac OS as a guest and that it can run from Linux as a host, but can it do these on PPC hardware?  Has anyone tried this - I wondered whether it would be fast since in theory this would be virtualization, not emulation.

---

### Post by cyberdork33 on 2008-07-27
[quote=http://bellard.org/qemu/about.html]The virtualizer mode requires that both the host and guest machine use x86 compatible processors[/quote]
.

---

### Post by 3rdalbum on 2008-07-27
I don't believe it is possible to run a functional Mac OS with Qemu. Take a look at PearPC and Sheepshaver - one of them runs Mac OS 9, the other runs Mac OS X, and I think they both work on PowerPC.

I never got them to work, but then I didn't spend long trying (and I think the ROM image from my computer was incompatible).

---

### Post by cyberdork33 on 2008-07-27
sheepshaver works OK...

---

### Post by mfox on 2008-07-28
I would be happy to run SheepShaver, but I can't seem to compile it.  I followed the instructions in the HowTos, but at the make stage, I got a bunch of errors.  Here is the output:

Configuration done. Now type "make". 
fox@fox-PowerBook:~/Desktop/SheepShaver-2.3/src/Unix$ make 
gcc -I../include -I. -I../slirp -DHAVE_CONFIG_H -D_REENTRANT -DDATADIR=\"/usr/local/share/SheepShaver\" -g -O2   -c Linux/sheepthreads.c -o obj/sheepthreads.o 
Linux/sheepthreads.c:53: error: field &#8216;__sem_lock&#8217; has incomplete type 
Linux/sheepthreads.c:55: error: expected specifier-qualifier-list before &#8216;_pthread_descr&#8217; 
Linux/sheepthreads.c: In function &#8216;fastlock_init&#8217;: 
Linux/sheepthreads.c:190: error: dereferencing pointer to incomplete type 
Linux/sheepthreads.c:191: error: dereferencing pointer to incomplete type 
Linux/sheepthreads.c: In function &#8216;fastlock_try_acquire&#8217;: 
Linux/sheepthreads.c:197: error: dereferencing pointer to incomplete type 
Linux/sheepthreads.c:198: error: dereferencing pointer to incomplete type 
Linux/sheepthreads.c:199: error: dereferencing pointer to incomplete type 
Linux/sheepthreads.c:203: error: dereferencing pointer to incomplete type 
Linux/sheepthreads.c: In function &#8216;fastlock_acquire&#8217;: 
Linux/sheepthreads.c:211: error: dereferencing pointer to incomplete type 
Linux/sheepthreads.c: In function &#8216;fastlock_release&#8217;: 
Linux/sheepthreads.c:218: error: dereferencing pointer to incomplete type 
Linux/sheepthreads.c:219: error: dereferencing pointer to incomplete type 
Linux/sheepthreads.c:219: error: dereferencing pointer to incomplete type 
Linux/sheepthreads.c:219: error: invalid lvalue in asm output 0 
Linux/sheepthreads.c:219: error: memory input 1 is not directly addressable 
Linux/sheepthreads.c: In function &#8216;pthread_mutex_init&#8217;: 
Linux/sheepthreads.c:229: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_lock&#8217; 
Linux/sheepthreads.c:230: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_kind&#8217; 
Linux/sheepthreads.c:230: error: &#8216;pthread_mutexattr_t&#8217; has no member named &#8216;__mutexkind&#8217; 
Linux/sheepthreads.c:231: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_count&#8217; 
Linux/sheepthreads.c:232: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_owner&#8217; 
Linux/sheepthreads.c: In function &#8216;pthread_mutex_destroy&#8217;: 
Linux/sheepthreads.c:243: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_kind&#8217; 
Linux/sheepthreads.c:245: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_lock&#8217; 
Linux/sheepthreads.c: In function &#8216;pthread_mutex_lock&#8217;: 
Linux/sheepthreads.c:258: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_kind&#8217; 
Linux/sheepthreads.c:260: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_lock&#8217; 
Linux/sheepthreads.c: In function &#8216;pthread_mutex_trylock&#8217;: 
Linux/sheepthreads.c:274: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_kind&#8217; 
Linux/sheepthreads.c:276: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_lock&#8217; 
Linux/sheepthreads.c: In function &#8216;pthread_mutex_unlock&#8217;: 
Linux/sheepthreads.c:289: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_kind&#8217; 
Linux/sheepthreads.c:291: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_lock&#8217; 
Linux/sheepthreads.c: In function &#8216;pthread_mutexattr_init&#8217;: 
Linux/sheepthreads.c:305: error: &#8216;pthread_mutexattr_t&#8217; has no member named &#8216;__mutexkind&#8217; 
Linux/sheepthreads.c: In function &#8216;sem_init&#8217;: 
Linux/sheepthreads.c:336: error: &#8216;sem_t&#8217; has no member named &#8216;__sem_waiting&#8217; 
Linux/sheepthreads.c: In function &#8216;sem_destroy&#8217;: 
Linux/sheepthreads.c:351: error: &#8216;sem_t&#8217; has no member named &#8216;__sem_waiting&#8217; 
Linux/sheepthreads.c:356: error: &#8216;sem_t&#8217; has no member named &#8216;__sem_waiting&#8217; 
Linux/sheepthreads.c: In function &#8216;sem_wait&#8217;: 
Linux/sheepthreads.c:377: error: &#8216;sem_t&#8217; has no member named &#8216;__sem_waiting&#8217; 
Linux/sheepthreads.c:377: error: &#8216;sem_t&#8217; has no member named &#8216;__sem_waiting&#8217; 
Linux/sheepthreads.c: In function &#8216;sem_post&#8217;: 
Linux/sheepthreads.c:400: error: &#8216;sem_t&#8217; has no member named &#8216;__sem_waiting&#8217; 
Linux/sheepthreads.c:401: error: &#8216;sem_t&#8217; has no member named &#8216;__sem_waiting&#8217; 
Linux/sheepthreads.c:401: error: &#8216;sem_t&#8217; has no member named &#8216;__sem_waiting&#8217; 
make: *** [obj/sheepthreads.o] Error 1 

Not to my surprise it wouldn't install.  Any idea of what I can do to fix this?  With regard to PearPC, I believe it will only run on x86 hardware.

---

