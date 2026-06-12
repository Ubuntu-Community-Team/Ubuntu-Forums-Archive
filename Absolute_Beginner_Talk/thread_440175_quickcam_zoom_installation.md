---
title: "quickcam zoom installation"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by victor_sf on 2007-05-11
Hello everybody,
I'm trying to install my quickcam zoom on feisty. I first installed Easycam2 but I got an error  during the make. then I downloaded PWC but when i do "make" I got this :
```
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/sinapc/pwc-10.0.12-rc1 modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.20-15-generic »
  CC [M]  /home/sinapc/pwc-10.0.12-rc1/pwc-if.o
Dans le fichier inclus à partir de /home/sinapc/pwc-10.0.12-rc1/pwc-if.c:69:
/home/sinapc/pwc-10.0.12-rc1/pwc.h:28:26: erreur: linux/config.h : Aucun fichier ou répertoire de ce type
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:166: erreur: variable ‘pwc_template’ has initializer but incomplete type
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:167: erreur: unknown field ‘owner’ specified in initializer
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:167: attention : éléments en excès dans l'initialisation de la structure
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:167: attention : (near initialization for ‘pwc_template’)
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:168: erreur: unknown field ‘name’ specified in initializer
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:168: attention : éléments en excès dans l'initialisation de la structure
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:168: attention : (near initialization for ‘pwc_template’)
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:169: erreur: unknown field ‘type’ specified in initializer
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:169: attention : éléments en excès dans l'initialisation de la structure
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:169: attention : (near initialization for ‘pwc_template’)
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:170: erreur: unknown field ‘hardware’ specified in initializer
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:170: attention : éléments en excès dans l'initialisation de la structure
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:170: attention : (near initialization for ‘pwc_template’)
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:171: erreur: unknown field ‘release’ specified in initializer
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:171: erreur: ‘video_device_release’ undeclared here (not in a function)
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:171: attention : éléments en excès dans l'initialisation de la structure
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:171: attention : (near initialization for ‘pwc_template’)
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:172: erreur: unknown field ‘fops’ specified in initializer
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:172: attention : éléments en excès dans l'initialisation de la structure
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:172: attention : (near initialization for ‘pwc_template’)
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:173: erreur: unknown field ‘minor’ specified in initializer
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:173: attention : éléments en excès dans l'initialisation de la structure
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:173: attention : (near initialization for ‘pwc_template’)
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_isoc_init’:
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:921: attention : assignment from incompatible pointer type
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c: In function ‘cd_to_pwc’:
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1019: attention : implicit declaration of function ‘to_video_device’
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1019: attention : initialization makes pointer from integer without a cast
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1020: attention : implicit declaration of function ‘video_get_drvdata’
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1020: attention : return makes pointer from integer without a cast
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_create_sysfs_files’:
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1062: attention : initialization makes pointer from integer without a cast
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1064: attention : implicit declaration of function ‘video_device_create_file’
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_remove_sysfs_files’:
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1070: attention : initialization makes pointer from integer without a cast
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1072: attention : implicit declaration of function ‘video_device_remove_file’
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_open’:
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1112: attention : implicit declaration of function ‘video_devdata’
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1112: attention : initialization makes pointer from integer without a cast
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1117: erreur: déréférencement d'un pointeur de type incomplet
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_close’:
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1231: erreur: déréférencement d'un pointeur de type incomplet
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_read’:
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1292: erreur: déréférencement d'un pointeur de type incomplet
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_poll’:
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1359: erreur: déréférencement d'un pointeur de type incomplet
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_ioctl’:
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1375: attention : implicit declaration of function ‘video_usercopy’
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_mmap’:
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1388: erreur: déréférencement d'un pointeur de type incomplet
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c: In function ‘usb_pwc_probe’:
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1722: attention : implicit declaration of function ‘video_device_alloc’
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1722: attention : assignment makes pointer from integer without a cast
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1729: erreur: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1729: erreur: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1729: erreur: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1730: erreur: déréférencement d'un pointeur de type incomplet
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1731: erreur: déréférencement d'un pointeur de type incomplet
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1732: erreur: déréférencement d'un pointeur de type incomplet
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1733: attention : implicit declaration of function ‘video_set_drvdata’
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1756: erreur: déréférencement d'un pointeur de type incomplet
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1757: attention : implicit declaration of function ‘video_register_device’
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1757: erreur: ‘VFL_TYPE_GRABBER’ undeclared (first use in this function)
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1757: erreur: (Each undeclared identifier is reported only once
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1757: erreur: for each function it appears in.)
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1760: attention : implicit declaration of function ‘video_device_release’
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1765: erreur: déréférencement d'un pointeur de type incomplet
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c: In function ‘usb_pwc_disconnect’:
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:1819: attention : implicit declaration of function ‘video_unregister_device’
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c: Hors de toute fonction :
/home/sinapc/pwc-10.0.12-rc1/pwc-if.c:2042: erreur fatale: ouverture du fichier de dépendances /home/sinapc/pwc-10.0.12-rc1/.pwc-if.o.d: Permission non accordée
compilation terminée.
make[2]: *** [/home/sinapc/pwc-10.0.12-rc1/pwc-if.o] Erreur 1
make[1]: *** [_module_/home/sinapc/pwc-10.0.12-rc1] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.20-15-generic »
make: *** [all] Erreur 2
```

can I please explain me how to resolve these errors ?

Thanks a lot.

---

### Post by bapoumba on 2007-05-11
Thread moved to the "Absolute Beginner Talk" support forum.

---

### Post by victor_sf on 2007-05-11
nobody can help me ?

---

