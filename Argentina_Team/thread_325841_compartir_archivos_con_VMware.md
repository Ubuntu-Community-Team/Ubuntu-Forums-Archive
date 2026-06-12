---
title: "compartir archivos con VMware"
date: 2006-12-26
forum: Argentina Team
---

### Post by cacharreo on 2006-12-26
Hola a tod@s

Instalé VmWare server y creé una máquina virtual WinXP, funciona de mararvilla, pero no se como compartir ficheros desde el host (Ubuntu 6.10) y el guest (VM WinXP).
Configuré la tarjeta de red virtual como NAT, lo cual hace que pueda salir a internet desde la VM, ya que comparte la IP del Host pero no se como ver las carpetas compartidas del host.](*,) 
Alguna idea?

---

### Post by marianom on 2006-12-26
Parece ser que es con samba:
[http://www.ubuntuforums.org/showthread.php?t=296668](http://www.ubuntuforums.org/showthread.php?t=296668)

Umm, parece que le erré. Vos decis que windows vea los archivos de ubuntu?

---

### Post by beuno on 2006-12-26
De una u otra forma vas a usar samba.
Tenes que compartir los archivos desde windows, o instalar samba server en Ubuntu.

---

### Post by tzulberti on 2006-12-26
Aca te paso un link que siempre lo tengo en favoritos, ya que yo uso el Vmware y comparto los archivos con mi ubuntu:
Samba simplified..
Backup your smb.conf file by using the following command.

mv /etc/samba/smb.conf /etc/samba/smb.conf.bk

now vi /etc/samba/smb.conf and copy paste this into your vi editor

############################
[global]
workgroup = YOURWORKGROUP
server string = Samba Server %v
log file = /var/log/samba/log.%m
encrypt passwords = yes
smb passwd file = /etc/samba/smbpasswd


[YOURSHARE]
comment = HEY ITS A SHARE
path = <Your Path to share>
public = yes
writable = yes
browseable = yes
#############################

Now save this.


Ok from the command line run this command.

smbpasswd -a <Your user Account>
Enter Password: **********
Re-Enter Password: ********** 

sacado de: [http://www.vmware.com/community/thread.jspa?messageID=399718&#399718](http://www.vmware.com/community/thread.jspa?messageID=399718&#399718)
Ademas, seguramente tengas que instalar el samba (sudo apt-get install samba). Casi todos los pasos que aparecen ahi tienen que ejecutarse como root.

---

### Post by jpmorelli on 2006-12-27
Yo seguí el mismo tutorial y me anduvo per-fec-to

---

