---
title: "Pantalla en negre després d'actualitzar"
date: 2011-07-16
forum: Catalan Team
---

### Post by Pelacanyes on 2011-07-16
Bona tarda a tothom:
Tinc l'actualització del programari en automatic i, avui, sense mirar-m'ho massa he fet que s'actualitces. Al acabar s'havia de reinicialitzar el sistema i l'he dit que si.
Al arrencar apareix aquest missatge amb la pantalla en negre
> [  0.1024080] Kernel panic - not syncing: VFS :Unable to mount root fs on unknown-block(0,0)
Es queda penjat aquí. He intentat solucionar-ho amb el Rescatux però no me'n surto.
Agrairé qualsevol sugeriment i/o indicació de que he de fer
Salut

Pelacanyes

---

### Post by wgarcia on 2011-07-17
A diferents fòrums diuen que és un problema de corrupció del fitxer "initramfs", que està relacionat amb l'arrencada del sistema. Per arreglar-ho suggereixen entrar en un nucli més antic si ho tens (per accedir has de mirar el menú inicial Grub i mirar i sota "versions anteriors" surten altres nuclis), entrar en "mode rescue" i córrer la següent comanda des d'una termninal:

```
update-initramfs -k all -c -v
```

---

### Post by Pelacanyes on 2011-07-18
Gracies company per la informació.
Quan dius "entrar en un nucli més antic", a que et refereixes? buscar en un altre ordinador, dintre del mateix ordinador?
Sóc força novell amb Ubuntu i encara em costa entendre les coses més tècniques?
Gracies de nou per donar-me un cop de ma
Salut
 
Pelacanyes

---

### Post by wgarcia on 2011-07-18
Si és una instal·lació nova potser no tinguis cap nucli més antic. 

El nucli és el sistema central de qualsevol sistema operatiu. A Linux hi ha una aplicació inicial que es diu Grub que et dóna un menú inicial on escollir si entrar a Linux o a un altre sistema operatiu, i dins de Linux si tens més d'un nucli instal·lat et dóna opció d'escollir a quin nucli entrar, tot i que per defecte entra al més nou que tinguis instal·lat. Quan s'actualitza el nucli és útil mantenir algun de més antic per si ha alguna cosa que falla a l'actualització. 

Doncs la primera pregunta seria si veus aquest menú del Grub quan inicies l'ordinador (o millor dit, just després d'iniciar-lo), i si dins d'aquest menú veus una línia que posa "Versions anteriors" o més d'una línia que posa "Ubuntu linux..." o alguna cosa així.

---

### Post by Pelacanyes on 2011-07-18
Hola de nou:
Doncs no em sortia res al iniciar-se l'ordinador. Només tinc l'ubuntu instal·lat i només hi ha una partició al disc dur.
Estic explorant el disc dur amb el Rescatux's per veure si trobo alguna carpeta amb el Grub, però molt em temo que no tinc cap altra versió instal·lada.
No se per on continuar :confused:
S'agraeixen totes les sugerencies
Salut

Pelacanyes

---

### Post by wgarcia on 2011-07-19
Per accedir al menú del grub en el cas que sols tinguis Ubuntu i una partició, quan comença l'ordinador prem la tecla "Majúscula" (Shift) de seguida que l'ordinador comença, a veure si ara surt aquest menú.

---

### Post by Pelacanyes on 2011-07-19
Hola de nou:
A veure, he fet el que m'has dit i em surt un llistat de l'ubuntu's. Crec que deuen ser les diferents versions i les mateixes en versió recuperació.
He entrat amb l'anterior en mode normal (l'ultima abans d'actualitzar) i l'ordinador ha arrencat be. Ara faré una proba d'apagar i tornar a encendre, a veure que passa.
Torno de seguides

Pelacanyes

---

### Post by Pelacanyes on 2011-07-19
Torno a ser aquí.
Doncs no a arrencat, torna a sortir el missatge "Kernel panic - not syncing:VFS: Unable to mount root fs on unknown-Block (0,0)"
He reiniciat l'ordinador pitjant la tecla de majuscules i apareix la següent pantalla.
> GNU GRUB version 1.98-1ubuntu12
Ubuntu, with Linux 2.6.32-33-generic
Ubuntu, with Linux 2.6.32-33-generic (recovery mode)
Ubuntu, with Linux 2.6.32-32-generic
Ubuntu, with Linux 2.6.32-32-generic (recovery mode)
Ubuntu, with Linux 2.6.32-31-generic
Ubuntu, with Linux 2.6.32-31-generic (recovery mode)
Ubuntu, with Linux 2.6.32-30-generic
Ubuntu, with Linux 2.6.32-30-generic (recovery mode)
Ubuntu, with Linux 2.6.32-29-generic
Ubuntu, with Linux 2.6.32-29-generic (recovery mode)
Ubuntu, with Linux 2.6.32-28-generic
Ubuntu, with Linux 2.6.32-28-generic (recovery mode)
Ubuntu, with Linux 2.6.32-27-generic
Ubuntu, with Linux 2.6.32-27-generic (recovery mode)
Ubuntu, with Linux 2.6.32-25-generic

Use the | and | keys to select which entry is highlighted.
Press enter to boot the selected OS, 'e' to edit the commands before booting or 'c' for a command line


Que es pot fer a partir d'aquí? Be, ara com a mínim puc entrar encara que sigui per la porta del darrera i això per mi ja es un gran qué.
Gracies de nou per la teva ajuda, no se que hi fariem sense gent com tu
Salut

Pelacanyes

---

### Post by wgarcia on 2011-07-19
Ara esculls un nucli més antic del que tenies en mode recovery (movent-te amb la fletxa cap a baix fins que quedi escollit), per exemple

Ubuntu, with Linux 2.6.32-32-generic (recovery mode)

Un cop que entris a l'escriptori obre una terminal i prova la instrucció suggerida més a dalt.

---

### Post by Pelacanyes on 2011-07-19
Be, he probat de fer el que m'has dit i, pel que sembla, no s'ha solucionat (al reiniciar torna a donar el missatge "kernel panic.....").
He copiat les instruccions que han sortit al terminal i crec que els errors que dona son el problema 
```
 
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/sata_vsc.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_ns87415.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_qdi.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_sc1200.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/sata_nv.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_pdc2027x.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_cmd640.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_opti.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_cs5520.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_hpt3x3.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_via.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_radisys.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_hpt366.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/sata_sx4.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/message/i2o/i2o_core.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/message/i2o/i2o_block.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ieee1394/ieee1394.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ieee1394/ohci1394.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ieee1394/sbp2.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/firewire/firewire-core.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/firewire/firewire-ohci.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/firewire/firewire-sbp2.ko
Adding binary /usr/share/initramfs-tools/init
Adding binary /etc/initramfs-tools/initramfs.conf
Adding binary /etc/initramfs-tools/conf.d/resume
Adding binary /usr/lib/initramfs-tools/bin//busybox
Adding library /lib/libc.so.6
Adding library /lib/ld-linux.so.2
Adding binary /usr/lib/initramfs-tools/bin/wait-for-root
Adding library /lib/libudev.so.0
Adding binary /sbin/modprobe
Adding binary /sbin/depmod
Adding binary /sbin/rmmod
Adding binary /sbin/blkid
Adding library /lib/libblkid.so.1
Adding library /lib/libuuid.so.1
Calling hook compcache
Calling hook fixrtc
Adding binary /bin/date
Adding library /lib/librt.so.1
Adding library /lib/libpthread.so.0
Adding binary /sbin/hwclock
Adding binary /sbin/dumpe2fs
Adding library /lib/libext2fs.so.2
Adding library /lib/libcom_err.so.2
Adding library /lib/libe2p.so.2
Calling hook fuse_utils
Adding binary /sbin/mount.fuse
Calling hook thermal
Calling hook udev
Adding binary /usr/bin/pkill
Adding library /lib/libproc-3.2.8.so
Adding binary /sbin/udevd
Adding library /lib/libselinux.so.1
Adding library /lib/libdl.so.2
Adding binary /sbin/udevadm
Adding binary /lib/udev/firmware
Adding binary /lib/udev/ata_id
Adding binary /lib/udev/usb_id
Adding binary /sbin/blkid
Adding binary /lib/udev/scsi_id
Adding binary /lib/udev/path_id
Adding binary /lib/udev/edd_id
Calling hook ntfs_3g
Adding binary /bin/ntfs-3g
Adding library //lib/libfuse.so.2
Adding library //lib/libntfs-3g.so.75
Calling hook console_setup
Calling hook kbd
Adding binary /bin/setfont
Adding binary /bin/kbd_mode
Adding binary /bin/loadkeys
Calling hook dmsetup
Adding binary /sbin/dmsetup
Adding library /lib/libdevmapper.so.1.02.1
Building cpio /boot/initrd.img-2.6.32-24-generic.new initramfs
/usr/sbin/mkinitramfs: 362: cannot create /boot/initrd.img-2.6.32-24-generic.new: Permission denied
update-initramfs: failed for /boot/initrd.img-2.6.32-24-generic
Execute: /usr/sbin/update-initramfs -c -k "2.6.32-21-generic" -b /boot -v -t
update-initramfs: Generating /boot/initrd.img-2.6.32-21-generic
touch: no s’han pogut canviar les dates de «/boot/initrd.img-2.6.32-21-generic.new»: Permission denied
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/hid/hid.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/hid/usbhid/usbhid.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/hid/hid-a4tech.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/hid/hid-apple.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/hid/hid-belkin.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/hid/hid-cherry.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/hid/hid-chicony.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/hid/hid-cypress.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/hid/hid-ezkey.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/hid/hid-gyration.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/input/ff-memless.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/hid/hid-logitech.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/hid/hid-microsoft.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/hid/hid-monterey.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/hid/hid-petalynx.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/hid/hid-pl.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/hid/hid-samsung.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/hid/hid-sony.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/hid/hid-sunplus.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/hid/hid-tmff.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/hid/hid-zpff.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/usb/storage/usb-storage.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/fs/isofs/isofs.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/fs/jfs/jfs.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/net/sunrpc/sunrpc.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/net/sunrpc/auth_gss/auth_rpcgss.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/fs/nfs_common/nfs_acl.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/fs/lockd/lockd.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/fs/nfs/nfs.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/fs/reiserfs/reiserfs.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/lib/crc-itu-t.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/fs/udf/udf.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/fs/exportfs/exportfs.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/fs/xfs/xfs.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/virtio/virtio.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/virtio/virtio_ring.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/virtio/virtio_pci.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/fs/fat/fat.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/fs/fat/vfat.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/fs/nls/nls_cp437.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/fs/nls/nls_iso8859-1.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/mii.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/3c59x.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/8139cp.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/8139too.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/8390.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/atlx/atl1.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/atl1e/atl1e.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ssb/ssb.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/b44.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/mdio.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/cxgb3/cxgb3.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/defxx.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/e100.ko
Adding binary /lib/firmware/2.6.32-21-generic/e100/d102e_ucode.bin
Adding firmware e100/d102e_ucode.bin
Adding binary /lib/firmware/2.6.32-21-generic/e100/d101s_ucode.bin
Adding firmware e100/d101s_ucode.bin
Adding binary /lib/firmware/2.6.32-21-generic/e100/d101m_ucode.bin
Adding firmware e100/d101m_ucode.bin
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/e1000/e1000.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/e1000e/e1000e.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/epic100.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/eql.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/fealnx.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/forcedeth.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/hp100.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/dca/dca.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/igb/igb.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/ipg.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/myri10ge/myri10ge.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/natsemi.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/ne2k-pci.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/fs/configfs/configfs.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/netconsole.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/niu.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/ns83820.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/pcnet32.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/qla3xxx.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/r8169.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/s2io.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/sis900.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/skge.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/sky2.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/starfire.ko
Adding binary /lib/firmware/2.6.32-21-generic/adaptec/starfire_tx.bin
Adding firmware adaptec/starfire_tx.bin
Adding binary /lib/firmware/2.6.32-21-generic/adaptec/starfire_rx.bin
Adding firmware adaptec/starfire_rx.bin
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/sundance.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/sungem_phy.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/sungem.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/sunhme.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/tg3.ko
Adding binary /lib/firmware/2.6.32-21-generic/tigon/tg3_tso5.bin
Adding firmware tigon/tg3_tso5.bin
Adding binary /lib/firmware/2.6.32-21-generic/tigon/tg3_tso.bin
Adding firmware tigon/tg3_tso.bin
Adding binary /lib/firmware/2.6.32-21-generic/tigon/tg3.bin
Adding firmware tigon/tg3.bin
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/tlan.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/tulip/de2104x.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/tulip/de4x5.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/tulip/dmfe.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/tulip/tulip.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/tulip/winbond-840.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/tulip/xircom_cb.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/via-rhine.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/lib/crc-ccitt.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/via-velocity.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/virtio_net.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/yellowfin.ko
Copying module directory kernel/drivers/scsi
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/atp870u.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/scsi_wait_scan.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/scsi_transport_spi.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/pas16.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/scsi_tgt.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/scsi_transport_fc.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/libfc/libfc.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/fcoe/libfcoe.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/fcoe/fcoe.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/fd_mcs.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/raid_class.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/fnic/fnic.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/BusLogic.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/qla2xxx/qla2xxx.ko
Adding binary /lib/firmware/ql2500_fw.bin
Adding firmware ql2500_fw.bin
Adding binary /lib/firmware/ql2400_fw.bin
Adding firmware ql2400_fw.bin
Adding binary /lib/firmware/ql2322_fw.bin
Adding firmware ql2322_fw.bin
Adding binary /lib/firmware/ql2300_fw.bin
Adding firmware ql2300_fw.bin
Adding binary /lib/firmware/ql2200_fw.bin
Adding firmware ql2200_fw.bin
Adding binary /lib/firmware/ql2100_fw.bin
Adding firmware ql2100_fw.bin
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/scsi_transport_iscsi.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/in2000.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/lpfc/lpfc.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/ultrastor.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/dc395x.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/libiscsi.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/libiscsi_tcp.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/iscsi_tcp.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/wd7000.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/hptiop.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/st.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/t128.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/3w-xxxx.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/dtc.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/libsrp.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/ips.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/53c700.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/NCR_D700.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/a100u2w.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/uio/uio.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/net/cnic.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/bnx2i/bnx2i.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/dpt_i2o.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/aic7xxx/aic7xxx.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/aic7xxx/aic79xx.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/aacraid/aacraid.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/osst.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/g_NCR5380.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/scsi_transport_sas.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/libsas/libsas.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/mvsas/mvsas.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/parport/parport.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/ppa.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/nsp32.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/fdomain.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/qlogicfas408.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/qlogicfas.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/osd/libosd.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/osd/osd.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/megaraid.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/imm.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/aha1740.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/sim710.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/mpt2sas/mpt2sas.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/scsi_transport_srp.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/vmw_pvscsi.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/pmcraid.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/tmscsim.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/ibmmca.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/device_handler/scsi_dh_alua.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/device_handler/scsi_dh_emc.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/device_handler/scsi_dh_hp_sw.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/device_handler/scsi_dh_rdac.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/NCR_Q720_mod.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/megaraid/megaraid_mm.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/megaraid/megaraid_mbox.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/megaraid/megaraid_sas.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/3w-9xxx.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/NCR53c406a.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/initio.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/qla4xxx/qla4xxx.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/stex.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/misc/enclosure.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/ses.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/dmx3191d.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/scsi_debug.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/aha1542.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/advansys.ko
Adding binary /lib/firmware/2.6.32-21-generic/advansys/38C1600.bin
Adding firmware advansys/38C1600.bin
Adding binary /lib/firmware/2.6.32-21-generic/advansys/38C0800.bin
Adding firmware advansys/38C0800.bin
Adding binary /lib/firmware/2.6.32-21-generic/advansys/3550.bin
Adding firmware advansys/3550.bin
Adding binary /lib/firmware/2.6.32-21-generic/advansys/mcode.bin
Adding firmware advansys/mcode.bin
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/be2iscsi/be2iscsi.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/g_NCR5380_mmio.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/ch.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/bfa/bfa.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/u14-34f.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/sym53c416.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/pcmcia/pcmcia_core.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/pcmcia/pcmcia.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/pcmcia/sym53c500_cs.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/pcmcia/aha152x_cs.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/pcmcia/qlogic_cs.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/pcmcia/nsp_cs.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/pcmcia/fdomain_cs.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/ipr.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/gdth.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/cxgb3i/cxgb3i.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/aha152x.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/arcmsr/arcmsr.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/qla1280.ko
Adding binary /lib/firmware/2.6.32-21-generic/qlogic/12160.bin
Adding firmware qlogic/12160.bin
Adding binary /lib/firmware/2.6.32-21-generic/qlogic/1280.bin
Adding firmware qlogic/1280.bin
Adding binary /lib/firmware/2.6.32-21-generic/qlogic/1040.bin
Adding firmware qlogic/1040.bin
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/sym53c8xx_2/sym53c8xx.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/aic94xx/aic94xx.ko
Adding binary /lib/firmware/aic94xx-seq.fw
Adding firmware aic94xx-seq.fw
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/scsi/eata.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/message/fusion/mptbase.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/message/fusion/mptscsih.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/message/fusion/mptfc.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/message/fusion/mptsas.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/message/fusion/mptspi.ko
Copying module directory kernel/drivers/block
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/cciss.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/paride/paride.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/paride/friq.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/paride/pg.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/paride/epat.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/paride/ktti.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/paride/pt.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/paride/fit2.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/paride/kbic.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/paride/on20.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/paride/bpck6.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/paride/bpck.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/paride/epia.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/paride/pf.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/paride/comm.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/paride/aten.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/paride/pcd.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/paride/dstr.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/paride/on26.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/paride/pd.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/paride/fit3.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/paride/frpw.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/virtio_blk.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/DAC960.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/cpqarray.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/osdblk.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/cryptoloop.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/nbd.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/floppy.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/sx8.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/umem.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/block/aoe/aoe.ko
Copying module directory kernel/drivers/usb/storage
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/usb/storage/ums-onetouch.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/usb/storage/ums-alauda.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/usb/storage/ums-cypress.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/usb/storage/ums-sddr09.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/usb/storage/ums-jumpshot.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/usb/storage/ums-sddr55.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/usb/storage/ums-usbat.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/usb/storage/ums-datafab.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/usb/storage/ums-isd200.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/usb/storage/ums-freecom.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/usb/storage/ums-karma.ko
Copying module directory kernel/drivers/ata
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/sata_mv.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_amd.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_pcmcia.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_it8213.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_isapnp.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/sata_sil.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_efar.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/sata_uli.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/sata_svw.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_atp867x.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_pdc202xx_old.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_artop.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_optidma.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_cs5530.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_ns87410.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_hpt37x.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_atiixp.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_marvell.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_oldpiix.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_winbond.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_sch.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_ali.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_rz1000.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_sil680.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_rdc.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_triflex.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_ninja32.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_mpiix.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_cmd64x.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_hpt3x2n.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_sl82c105.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_jmicron.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/ahci.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/sata_qstor.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_netcell.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_legacy.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_serverworks.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_cs5536.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_it821x.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/sata_promise.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/sata_sil24.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/sata_via.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_cs5535.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_cypress.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/sata_inic162x.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/sata_sis.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/sata_vsc.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_ns87415.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_qdi.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_sc1200.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/sata_nv.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_pdc2027x.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_cmd640.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_opti.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_cs5520.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_hpt3x3.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_via.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_radisys.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/pata_hpt366.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ata/sata_sx4.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/message/i2o/i2o_core.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/message/i2o/i2o_block.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ieee1394/ieee1394.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ieee1394/ohci1394.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/ieee1394/sbp2.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/firewire/firewire-core.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/firewire/firewire-ohci.ko
Adding module /lib/modules/2.6.32-21-generic/kernel/drivers/firewire/firewire-sbp2.ko
Adding binary /usr/share/initramfs-tools/init
Adding binary /etc/initramfs-tools/initramfs.conf
Adding binary /etc/initramfs-tools/conf.d/resume
Adding binary /usr/lib/initramfs-tools/bin//busybox
Adding library /lib/libc.so.6
Adding library /lib/ld-linux.so.2
Adding binary /usr/lib/initramfs-tools/bin/wait-for-root
Adding library /lib/libudev.so.0
Adding binary /sbin/modprobe
Adding binary /sbin/depmod
Adding binary /sbin/rmmod
Adding binary /sbin/blkid
Adding library /lib/libblkid.so.1
Adding library /lib/libuuid.so.1
Calling hook compcache
Calling hook fixrtc
Adding binary /bin/date
Adding library /lib/librt.so.1
Adding library /lib/libpthread.so.0
Adding binary /sbin/hwclock
Adding binary /sbin/dumpe2fs
Adding library /lib/libext2fs.so.2
Adding library /lib/libcom_err.so.2
Adding library /lib/libe2p.so.2
Calling hook fuse_utils
Adding binary /sbin/mount.fuse
Calling hook thermal
Calling hook udev
Adding binary /usr/bin/pkill
Adding library /lib/libproc-3.2.8.so
Adding binary /sbin/udevd
Adding library /lib/libselinux.so.1
Adding library /lib/libdl.so.2
Adding binary /sbin/udevadm
Adding binary /lib/udev/firmware
Adding binary /lib/udev/ata_id
Adding binary /lib/udev/usb_id
Adding binary /sbin/blkid
Adding binary /lib/udev/scsi_id
Adding binary /lib/udev/path_id
Adding binary /lib/udev/edd_id
Calling hook ntfs_3g
Adding binary /bin/ntfs-3g
Adding library //lib/libfuse.so.2
Adding library //lib/libntfs-3g.so.75
Calling hook console_setup
Calling hook kbd
Adding binary /bin/setfont
Adding binary /bin/kbd_mode
Adding binary /bin/loadkeys
Calling hook dmsetup
Adding binary /sbin/dmsetup
Adding library /lib/libdevmapper.so.1.02.1
Building cpio /boot/initrd.img-2.6.32-21-generic.new initramfs
/usr/sbin/mkinitramfs: 362: cannot create /boot/initrd.img-2.6.32-21-generic.new: Permission denied
update-initramfs: failed for /boot/initrd.img-2.6.32-21-generic
andreu@andreu-portatil:~$

``` 
 
Perdoneu si aquesta no es la manera d'insertar el codi, però es que encara no m'aclareixo massa. Això em demostra lo molt que em falta per aprendre d'aquest magnific sistema operatiu (alguna recomanació per aprendre Ubuntu?)
 
Salut 
 
Pelacanyes

---

### Post by wgarcia on 2011-07-20
El millor per enganxar missatges d'error o de la terminal és o bé crear un fitxer de text i posar-lo com un adjunt, o utilitzar l'etiqueta "Code", cosa que pots fer amb el petit editor del fòrum (l'etiqueta apareix a la barra d'eines quan edites un missatge i té la icona # ) . 

En quant al problema amb el teu ordinador, torna a fer exactament el que has fet però posa-li un "sudo" endavant de la instrucció, et demanarà la contrassenya. A veure si hi ha sort. Per tant la instrucció que has d'entrar al terminal seria:

```

sudo update-initramfs -k all -c -v

```

---

### Post by Pelacanyes on 2011-07-20
Hola de nou:
Ara sembla que si s'ha solucionat. Ho he fet tal com m'has dit, arrenca be desprès de re-inicialitzar. L'he aturat una bona estona i quan l'he tornat a encendre..... eureka, funciona be.
Moltes, moltissimes gracies pel teu ajut. Fins hi tot m'havia plantejat reinstal·lar de nou el SO, a costa de perdre tota l'informació.
Alguna recomanació per aprendre el funcionament d'Ubuntu?
Gracies de nou.
Salut i peles, que el demés son punyetes

Pelacanyes

---

### Post by wgarcia on 2011-07-20
M'alegro que s'hagi solucionat. Tinc la mania de no reinstal·lar mai, de fet tinc un ordinador que vinc actualitzant des de l'any 2006 cada sis mesos amb les versions d'Ubuntu que van anar sortint i mai no he hagut de reinstal·lar. 

En quant a aprendre penso que el millor és participar de la comunitat, sempre hi haurà gent que sàpiga més que tu però també que sàpiguen menys, o que simplement no s'hagin trobat amb algun problema que tu sí i que tens un suggeriment.

---

### Post by Pelacanyes on 2011-07-25
Dons així ho faré. Gracies a vosaltres (i al meus errors) vaig aprenent cada dia una mica més.
Una pregunta, Com s'ha de fer per actualitzar l'ubuntu de 10.04 a 11.04?

Salut

Pelacanyes

---

### Post by wgarcia on 2011-07-26
Obre un nou fil (un nou missatge) amb el títol apropiat i ho comentem.

---

