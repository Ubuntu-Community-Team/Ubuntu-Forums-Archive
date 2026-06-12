---
title: "Problema con drivers viejos"
date: 2007-12-04
forum: Argentina Team
---

### Post by kaede15 on 2007-12-04
Hola gente! Esta es mi primera PC linux, despues de preguntar y averiguar por google reuni suficiente fuerza de voluntad para instalar el xubuntu en mi vieja P3 800Mhz! No solo salio todo bien sino que le hice funcionar el Compiz :) siguiendo los tutoriales q estan el la web. Todo bien hasta aca. Pero despues quise instalar una placa de expansion de HighPoint RocketRaid133 modelo 372A que tenia tirado por ahi para agregarle un par de hdds mas y me tope con problemas de drivers.

Baje el driver de la pagina oficial para Linux pero segun lo que tengo entendido desde el readme tengo que teclear el commando "make" en el directorio donde extaje los archivos. y me tiro estos prompts que la verdad no le entiendo para nada.

```
gcc -DDRIVER_VERSION=\"2.1.060607\" -DLIST_H_INCLUDED -DMODVERSIONS -DMODULE -DLINUX -D_LINUX_ -D__KERNEL__=1 -DCONFIG_PCI -DNO_CROSS_CTRL=1 -DSUPPORT_ARRAY -DDBG=0 -Wall -O2 -Wstrict-prototypes -fomit-frame-pointer -I. -I/lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/drivers/scsi -c hpt.c -o hpt.o

hpt.c:1:26: error: linux/config.h: No such file or directory

In file included from /lib/modules/2.6.22-14-generic/build/include/asm/thread_info.h:16,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/thread_info.h:21,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/preempt.h:9,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/spinlock.h:49,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/capability.h:47,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/sched.h:46,

                 from hpt.c:8:

/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:83: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)

/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:83: error: requested alignment is not a constant

/lib/modules/2.6.22-14-generic/build/include/asm/processor.h: In function ‘cpuid_count’:

/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 1 of ‘native_cpuid’ differ in signedness

/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 2 of ‘native_cpuid’ differ in signedness

/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 3 of ‘native_cpuid’ differ in signedness

/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 4 of ‘native_cpuid’ differ in signedness

In file included from /lib/modules/2.6.22-14-generic/build/include/linux/sched.h:51,

                 from hpt.c:8:

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:33:3: error: #error You lose.

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

In file included from /lib/modules/2.6.22-14-generic/build/include/linux/aio.h:5,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/sched.h:273,

                 from hpt.c:8:

/lib/modules/2.6.22-14-generic/build/include/linux/workqueue.h: In function ‘cancel_delayed_work’:

/lib/modules/2.6.22-14-generic/build/include/linux/workqueue.h:165: warning: dereferencing type-punned pointer will break strict-aliasing rules

In file included from hpt.c:8:

/lib/modules/2.6.22-14-generic/build/include/linux/sched.h: In function ‘dequeue_signal_lock’:

/lib/modules/2.6.22-14-generic/build/include/linux/sched.h:1337: warning: implicit declaration of function ‘local_irq_save’

/lib/modules/2.6.22-14-generic/build/include/linux/sched.h:1339: warning: implicit declaration of function ‘local_irq_restore’

In file included from /lib/modules/2.6.22-14-generic/build/include/linux/module.h:21,

                 from hpt.c:9:

/lib/modules/2.6.22-14-generic/build/include/asm/module.h:64:2: error: #error unknown processor family

In file included from hpt.c:17:

/lib/modules/2.6.22-14-generic/build/include/linux/mm.h: In function ‘virt_to_head_page’:

/lib/modules/2.6.22-14-generic/build/include/linux/mm.h:291: warning: implicit declaration of function ‘__pfn_to_page’

/lib/modules/2.6.22-14-generic/build/include/linux/mm.h:291: error: ‘CONFIG_PAGE_OFFSET’ undeclared (first use in this function)

/lib/modules/2.6.22-14-generic/build/include/linux/mm.h:291: error: (Each undeclared identifier is reported only once

/lib/modules/2.6.22-14-generic/build/include/linux/mm.h:291: error: for each function it appears in.)

/lib/modules/2.6.22-14-generic/build/include/linux/mm.h:291: warning: initialization makes pointer from integer without a cast

In file included from hpt.c:17:

/lib/modules/2.6.22-14-generic/build/include/linux/mm.h: In function ‘lowmem_page_address’:

/lib/modules/2.6.22-14-generic/build/include/linux/mm.h:560: warning: implicit declaration of function ‘__page_to_pfn’

/lib/modules/2.6.22-14-generic/build/include/linux/mm.h:560: error: ‘CONFIG_PAGE_OFFSET’ undeclared (first use in this function)

In file included from /lib/modules/2.6.22-14-generic/build/include/linux/irq.h:23,

                 from /lib/modules/2.6.22-14-generic/build/include/asm/hardirq.h:5,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/hardirq.h:7,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:11,

                 from hpt.c:18:

/lib/modules/2.6.22-14-generic/build/include/asm/irq.h:15:25: error: irq_vectors.h: No such file or directory

In file included from /lib/modules/2.6.22-14-generic/build/include/asm/hardirq.h:5,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/hardirq.h:7,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:11,

                 from hpt.c:18:

/lib/modules/2.6.22-14-generic/build/include/linux/irq.h: At top level:

/lib/modules/2.6.22-14-generic/build/include/linux/irq.h:178: error: ‘NR_IRQS’ undeclared here (not in a function)

In file included from /lib/modules/2.6.22-14-generic/build/include/linux/hardirq.h:7,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:11,

                 from hpt.c:18:

/lib/modules/2.6.22-14-generic/build/include/asm/hardirq.h:12: error: requested alignment is not a constant

In file included from hpt.c:18:

/lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h: In function ‘cli’:

/lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:221: warning: implicit declaration of function ‘local_irq_disable’

/lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h: In function ‘sti’:

/lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:225: warning: implicit declaration of function ‘local_irq_enable’

/lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h: In function ‘save_flags’:

/lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:229: warning: implicit declaration of function ‘local_save_flags’

In file included from hpt.c:23:

/lib/modules/2.6.22-14-generic/build/include/linux/pci.h: In function ‘pci_register_driver’:

/lib/modules/2.6.22-14-generic/build/include/linux/pci.h:604: error: ‘KBUILD_MODNAME’ undeclared (first use in this function)

In file included from /lib/modules/2.6.22-14-generic/build/include/linux/dmapool.h:14,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/pci.h:621,

                 from hpt.c:23:

/lib/modules/2.6.22-14-generic/build/include/asm/io.h: In function ‘virt_to_phys’:

/lib/modules/2.6.22-14-generic/build/include/asm/io.h:77: error: ‘CONFIG_PAGE_OFFSET’ undeclared (first use in this function)

/lib/modules/2.6.22-14-generic/build/include/asm/io.h: In function ‘phys_to_virt’:

/lib/modules/2.6.22-14-generic/build/include/asm/io.h:95: error: ‘CONFIG_PAGE_OFFSET’ undeclared (first use in this function)

In file included from /lib/modules/2.6.22-14-generic/build/include/linux/pci.h:767,

                 from hpt.c:23:

/lib/modules/2.6.22-14-generic/build/include/asm/pci.h: In function ‘pci_dac_dma_to_page’:

/lib/modules/2.6.22-14-generic/build/include/asm/pci.h:72: warning: return makes pointer from integer without a cast

hpt.c: In function ‘get_bdev’:

hpt.c:136: warning: implicit declaration of function ‘bdget’

hpt.c:136: warning: initialization makes pointer from integer without a cast

hpt.c:137: warning: implicit declaration of function ‘blkdev_get’

hpt.c:138: error: dereferencing pointer to incomplete type

hpt.c:141: warning: implicit declaration of function ‘blkdev_put’

In file included from hpt.c:185:

entry.c: At top level:

entry.c:20: error: ‘UTS_RELEASE’ undeclared here (not in a function)

In file included from hpt.c:185:

entry.c: In function ‘Check_Idle_Call’:

entry.c:216: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c: In function ‘Queue_SC’:

entry.c:225: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:227: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:227: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:228: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c: In function ‘Release_SC’:

entry.c:238: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:242: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:243: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:245: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:245: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c: In function ‘scsicmd_buf_get’:

entry.c:271: error: ‘OS_KMAP_TYPE’ undeclared (first use in this function)

entry.c:271: error: incompatible type for argument 2 of ‘kmap_atomic’

entry.c: In function ‘do_mode_sense’:

entry.c:354: error: ‘Scsi_Cmnd’ has no member named ‘bufflen’

entry.c:354: warning: initialization makes integer from pointer without a cast

entry.c:372: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c: In function ‘OsSendCommand’:

entry.c:439: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:455: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:521: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c: In function ‘internal_done’:

entry.c:608: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c: In function ‘hpt3xx_Command’:

entry.c:621: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:624: error: ‘CONFIG_HZ’ undeclared (first use in this function)

entry.c:624: error: invalid operands to binary *

entry.c:624: warning: assignment makes integer from pointer without a cast

entry.c:625: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:627: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c: In function ‘hpt3xx_Detect’:

entry.c:715: warning: ‘pci_find_device’ is deprecated (declared at /lib/modules/2.6.22-14-generic/build/include/linux/pci.h:477)

entry.c:747: warning: ‘pci_find_device’ is deprecated (declared at /lib/modules/2.6.22-14-generic/build/include/linux/pci.h:477)

entry.c:778: warning: ‘pci_find_device’ is deprecated (declared at /lib/modules/2.6.22-14-generic/build/include/linux/pci.h:477)

entry.c:823: warning: ‘deprecated_irq_flag’ is deprecated (declared at /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:66)

entry.c:823: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type

entry.c:824: warning: ‘deprecated_irq_flag’ is deprecated (declared at /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:66)

entry.c:824: warning: ‘deprecated_irq_flag’ is deprecated (declared at /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:66)

entry.c:824: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type

entry.c: In function ‘hpt3xx_Reset’:

entry.c:915: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c: In function ‘fOsBuildSgl’:

entry.c:1112: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:1113: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:1116: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:1118: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:1123: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:1127: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:1128: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:1130: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:1132: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c: In function ‘fOsCommandDone’:

entry.c:1146: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:1157: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c: In function ‘__check_autorebuild’:

entry.c:1700: warning: pointer targets in return differ in signedness

In file included from hpt.c:186:

hptproc.c: In function ‘get_sd_name’:

hptproc.c:503: error: dereferencing pointer to incomplete type

hptproc.c:503: error: request for member ‘disk_name’ in something not a structure or union

In file included from ioctl.c:6,

                 from hpt.c:187:

gui_lib.c: In function ‘hpt_get_controller_info’:

gui_lib.c:427: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness

gui_lib.c:440: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness

gui_lib.c:446: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness

gui_lib.c:451: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness

gui_lib.c:464: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness

In file included from hpt.c:187:

ioctl.c: In function ‘timer_start_for_cmd’:

ioctl.c:197: error: ‘CONFIG_HZ’ undeclared (first use in this function)

ioctl.c:197: error: invalid operands to binary *

ioctl.c:197: warning: assignment makes integer from pointer without a cast

ioctl.c: In function ‘Kernel_DeviceIoControl’:

ioctl.c:476: error: ‘CONFIG_HZ’ undeclared (first use in this function)

ioctl.c:476: error: invalid operands to binary *

ioctl.c:476: warning: assignment makes integer from pointer without a cast

ioctl.c: In function ‘hpt_set_array_state’:

ioctl.c:521: error: ‘CONFIG_HZ’ undeclared (first use in this function)

ioctl.c:521: error: invalid operands to binary *

ioctl.c:521: warning: assignment makes integer from pointer without a cast

ioctl.c: In function ‘hpt_rescan_all’:

ioctl.c:658: error: ‘CONFIG_HZ’ undeclared (first use in this function)

ioctl.c:658: error: invalid operands to binary *

ioctl.c:658: warning: assignment makes integer from pointer without a cast

ioctl.c: In function ‘hpt_rebuild_data_block’:

ioctl.c:898: error: ‘CONFIG_HZ’ undeclared (first use in this function)

ioctl.c:898: error: invalid operands to binary *

ioctl.c:898: warning: passing argument 1 of ‘schedule_timeout’ makes integer from pointer without a cast

make: *** [hpt.o] Error 1
```

Que significa todo ese cacho de codigo?? se que algo salio mal por todos los errores que hubo. Alguien me puede dar una mano para instalar este driver?

un millon de gracias!

---

### Post by Hernán-Amaya on 2007-12-05
Para compilar tenés que tener estos paquetes instalados build-essential y linux-headers proba instalándolos y fijate que el linux-headers que instales sean los mismos del kernel que tengas instalados.

buscalos por synaptic, cualquier cosa pregunta nuevamente por acá.

si logras instalarlos, proba de compilar el driver nuevamente y contanos como te fue.

Suerte!

---

### Post by faktorqm on 2007-12-06
1) no me preguntes por que, pero me molesta mucho cuando preguntan lo mismo en dos foros distintos.....

2) hola, estuve mirando la pagina del driver, y me baje y lei el readme. Mas alla de lo que te dijo hernan, que esta muy bien, hace esto:

```
sudo aptitude install build-essential binutils linux-headers-2.6.20-16-generic linux-headers-2.6.20-16 linux-headers-generic gcc g++ automake autogen autoconf
```

luego, hacemos (es con sudo por que no como usuario no tenes permisos sobre /usr):

```
sudo mkdir /usr/src/htp37A2
```

en la carpeta que hayas bajado el driver:

```
tar -zvxf hpt37x2-opensource-v2.1-0717.tgz
```
```
cd hpt37x2-opensource-v2.1-0717_FILES/
```
```
sudo mv * /usr/src/hpt37A2
```

Ahora, con el driver copiado vamos a tratar de compilarlo:

```
cd /usr/src/hpt37A2
```
```
sudo make RR1520=0 --prefix=/usr/local
```

la ruta por defecto del kernel que usa esta cosa es /lib/modules/2.6.20-16-generic/build
no hace falta especificar kernel dir (leiste el readme??)
lo de prefix, no estoy 100% seguro si era --prefix=/usr o --prefix=/usr/local. cuando compile el driver de nvidia use con local, pero bueno, no se si aplica a todas las cosas.

Bueno paramos aca, si pudiste compilar bien y no sabes usar el driver, es otro tema que lo vemos despues. Postea a ver que paso. salu2!

---

