---
title: "SheepShaver compilation problems"
date: 2007-06-09
forum: Apple PPC Users
---

### Post by Ptero-4 on 2007-06-09
Hi. I`m trying to compile SheepShaver on my PPC Mac (it supposedly supports compiling and running on powerpc linux distros) but when I type make, it ends with this error:
```

gcc -I../include -I. -I../slirp -DHAVE_CONFIG_H -D_REENTRANT -DDATADIR=\"/Aplicaciones/SheepShaver/share/SheepShaver\" -g -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -c Linux/sheepthreads.c -o obj/sheepthreads.o
Linux/sheepthreads.c:53: error: el campo ‘__sem_lock’ tiene tipo de dato incompleto
Linux/sheepthreads.c:55: error: expected specifier-qualifier-list before ‘_pthread_descr’
Linux/sheepthreads.c: En la función ‘fastlock_init’:
Linux/sheepthreads.c:190: error: puntero deferenciado a tipo de dato incompleto
Linux/sheepthreads.c:191: error: puntero deferenciado a tipo de dato incompleto
Linux/sheepthreads.c: En la función ‘fastlock_try_acquire’:
Linux/sheepthreads.c:197: error: puntero deferenciado a tipo de dato incompleto
Linux/sheepthreads.c:198: error: puntero deferenciado a tipo de dato incompleto
Linux/sheepthreads.c:199: error: puntero deferenciado a tipo de dato incompleto
Linux/sheepthreads.c:203: error: puntero deferenciado a tipo de dato incompleto
Linux/sheepthreads.c: En la función ‘fastlock_acquire’:
Linux/sheepthreads.c:211: error: puntero deferenciado a tipo de dato incompleto
Linux/sheepthreads.c: En la función ‘fastlock_release’:
Linux/sheepthreads.c:218: error: puntero deferenciado a tipo de dato incompleto
Linux/sheepthreads.c:219: error: puntero deferenciado a tipo de dato incompleto
Linux/sheepthreads.c:219: error: puntero deferenciado a tipo de dato incompleto
Linux/sheepthreads.c:219: error: l-valor inválido en la salida asm 0
Linux/sheepthreads.c:219: error: la entrada de memoria 1 no es directamente direccionable
Linux/sheepthreads.c: En la función ‘pthread_mutex_init’:
Linux/sheepthreads.c:229: error: ‘pthread_mutex_t’ no tiene un miembro llamado ‘__m_lock’
Linux/sheepthreads.c:230: error: ‘pthread_mutex_t’ no tiene un miembro llamado ‘__m_kind’
Linux/sheepthreads.c:230: error: ‘pthread_mutexattr_t’ no tiene un miembro llamado ‘__mutexkind’
Linux/sheepthreads.c:231: error: ‘pthread_mutex_t’ no tiene un miembro llamado ‘__m_count’
Linux/sheepthreads.c:232: error: ‘pthread_mutex_t’ no tiene un miembro llamado ‘__m_owner’
Linux/sheepthreads.c: En la función ‘pthread_mutex_destroy’:
Linux/sheepthreads.c:243: error: ‘pthread_mutex_t’ no tiene un miembro llamado ‘__m_kind’
Linux/sheepthreads.c:245: error: ‘pthread_mutex_t’ no tiene un miembro llamado ‘__m_lock’
Linux/sheepthreads.c: En la función ‘pthread_mutex_lock’:
Linux/sheepthreads.c:258: error: ‘pthread_mutex_t’ no tiene un miembro llamado ‘__m_kind’
Linux/sheepthreads.c:260: error: ‘pthread_mutex_t’ no tiene un miembro llamado ‘__m_lock’
Linux/sheepthreads.c: En la función ‘pthread_mutex_trylock’:
Linux/sheepthreads.c:274: error: ‘pthread_mutex_t’ no tiene un miembro llamado ‘__m_kind’
Linux/sheepthreads.c:276: error: ‘pthread_mutex_t’ no tiene un miembro llamado ‘__m_lock’
Linux/sheepthreads.c: En la función ‘pthread_mutex_unlock’:
Linux/sheepthreads.c:289: error: ‘pthread_mutex_t’ no tiene un miembro llamado ‘__m_kind’
Linux/sheepthreads.c:291: error: ‘pthread_mutex_t’ no tiene un miembro llamado ‘__m_lock’
Linux/sheepthreads.c: En la función ‘pthread_mutexattr_init’:
Linux/sheepthreads.c:305: error: ‘pthread_mutexattr_t’ no tiene un miembro llamado ‘__mutexkind’
Linux/sheepthreads.c: En la función ‘sem_init’:
Linux/sheepthreads.c:336: error: ‘sem_t’ no tiene un miembro llamado ‘__sem_waiting’
Linux/sheepthreads.c: En la función ‘sem_destroy’:
Linux/sheepthreads.c:351: error: ‘sem_t’ no tiene un miembro llamado ‘__sem_waiting’
Linux/sheepthreads.c:356: error: ‘sem_t’ no tiene un miembro llamado ‘__sem_waiting’
Linux/sheepthreads.c: En la función ‘sem_wait’:
Linux/sheepthreads.c:377: error: ‘sem_t’ no tiene un miembro llamado ‘__sem_waiting’
Linux/sheepthreads.c:377: error: ‘sem_t’ no tiene un miembro llamado ‘__sem_waiting’
Linux/sheepthreads.c: En la función ‘sem_post’:
Linux/sheepthreads.c:400: error: ‘sem_t’ no tiene un miembro llamado ‘__sem_waiting’
Linux/sheepthreads.c:401: error: ‘sem_t’ no tiene un miembro llamado ‘__sem_waiting’
Linux/sheepthreads.c:401: error: ‘sem_t’ no tiene un miembro llamado ‘__sem_waiting’
make: *** [obj/sheepthreads.o] Error 1
Ptero-4@CrackBox:~/Adiciones/SheepShaver-2.3/src/Unix$ 

```
How do I get past this?

---

### Post by jargoman on 2007-06-09
Do you have build essentials installed. 
$ sudo apt-get build-essential

I can't really help you because it's SPANISH

---

### Post by Ptero-4 on 2007-06-09
yes. I do, in fact I have everything up to libgtk2-dev installed, including xorg-dev, the problem comes midway the make command.

---

### Post by stmiller on 2007-06-10
Please post the text above this message. Whatever it was executing is what failed, so these error messages don't tell us much. This might be more of a question for the SheepSaver mailing list...

---

### Post by Jimbob17 on 2007-06-22
I had the same problem with the version I checked out of CVS. I did manage to find a solution eventually and that was to remove the sheepthreads.c file from the Makefile. There's a line near the top of the Makefile that lists all of the source files to be compiled. I tried compiling it and it seems to work OK. I haven't tested it much though.

HTH

---

