---
title: "emulant l'openmoko"
date: 2009-06-29
forum: Catalan Team
---

### Post by christianpv on 2009-06-29
Abans d'escriure he fet la recerca de rigor però he trobat res, així que espere que algú li haja passat el mateix que jo o semblant i em puga ajudar, abans de res. Per tal d'emular l'openmoko al meu ubuntu, he seguit els pasos descrits en aquesta web:
 
[http://extralinux.net/?q=node/74#comment-289](http://extralinux.net/?q=node/74#comment-289) 

com podreu comprobar he deixat el meu problema al final de la web, vaja aquest és el problema:

~/qemu-neo1973$ openmoko/download.sh
Retrieving available builds list...
Trying alternative sources
Kernel is... not found

encara que me dirigit al la web de descàrregues: 

[http://downloads.openmoko.org/](http://downloads.openmoko.org/)

però no he trobat res que m'ajude. 

Així que se que és alguna cosa molt específica, però vaja, gràcies per tot, com sempre.

---

### Post by christianpv on 2009-07-10
per si hi ha algú que li interese:
canviant l'arxiu env: 


# The scripts will include this on startup to setup variables

src_dir="`pwd`"
script_dir_relative=openmoko
script_dir="$src_dir/$script_dir_relative"
ubo"
"
ot_symlink="$src_dir/u-boot.bin"
qemu_relative="arm-softmmu/qemu-system-arm -M gta01 -m 130"
qemu="$src_dir/$qemu_relative"
flash_base=openmoko-flash.base
flash_image=openmoko-flash.image
make=make
which gmake && make=gmake
echo=echo
which gecho && echo=gecho
export make echo
dump_dir="$script_dir/vvfat"

qemu_monitor="$HOME/.qemu_monitor"
qemu_cmd () { $script_dir/qemu-cmd.pl "$qemu_monitor" "$*"; }

kernel_addr=0x30100000
splash_addr=0x36000000
splash_size=0x5000

# We don't want the "-latest" symlinks to match
kernel_wildcard="Om2008.9-gta02-20081106.uImage.bin"
rootfs_wildcard="Om2008.9-gta02-20081117.rootfs.jffs2"
uboot_wildcard="gta01bv4-u-boot.bin"

download_dir="http://downloads.openmoko.org/distro/releases/Om2008.9/"
dev_download_dir="$download_dir"
backup_download_dir="http://downloads.openmoko.org/distro/"

ara me falla la flash.....:s

---

