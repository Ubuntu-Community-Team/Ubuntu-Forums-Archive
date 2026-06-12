---
title: "Can I mount smb://dns-323/Music??"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by Schammy on 2007-01-17
I've been looking at various posts about mounting a network share but I'm stuck at what I think is a fundamental level.

I can easily navigate to my SMB shares via Places > Network Servers.  I see my windows desktop and my Dlink DNS-323 NAS box (which by the way kicks arse as long as you update the firmware).  The problem comes when I want to use my ubuntu machine to serve my music to a web page using gnump3d.

In the gnump3d config file I tried to indicate the root location or my music as "smb://dns-323/Music".  This didn't work.  The terminal tells me that "that directory is missing".  So I guess it needs to be mounted?  Is it not mounted?  I can view the files.  Isn't that mounted?

I've tried to mount the network share by indicating the location as smb://dns-323/ but that does't work and I get similar error messages.

What am I missing here?  Is it as simple as incorrect syntax?  Is a SMB share not considered at network share?

Thanks in advance for any help y'all have.

---

### Post by Rippey on 2007-01-18
try mounting it using this
"sudo mount -t smbfs -o username=yourusername //serveriporhostname/sharename /mountpoint"

---

### Post by anaconda on 2007-01-18
have you instaled samba and smbfs??  or whatever their names were..

---

### Post by Schammy on 2007-01-21
I tried the command and get this response...
steve@ubuntu:~$ sudo mount -t smbfs -o username=steve //dns-323 /media/Storage
Usage: mount.smbfs service mountpoint [-n] [-o options,...]
Version 3.0.22

Options:
      username=<arg>                  SMB username
      password=<arg>                  SMB password
      credentials=<filename>          file with username/password
      krb                             use kerberos (active directory)
      netbiosname=<arg>               source NetBIOS name
      uid=<arg>                       mount uid or username
      gid=<arg>                       mount gid or groupname
      port=<arg>                      remote SMB port number
      fmask=<arg>                     file umask
      dmask=<arg>                     directory umask
      debug=<arg>                     debug level
      ip=<arg>                        destination host or IP address
      workgroup=<arg>                 workgroup on destination
      sockopt=<arg>                   TCP socket options
      scope=<arg>                     NetBIOS scope
      iocharset=<arg>                 Linux charset (iso8859-1, utf8)
      codepage=<arg>                  server codepage (cp850)
      unicode                         use unicode when communicating with server
      lfs                             large file system support
      ttl=<arg>                       dircache time to live
      guest                           don't prompt for a password
      ro                              mount read-only
      rw                              mount read-write

This command is designed to be run from within /bin/mount by giving
the option '-t smbfs'. For example:
  mount -t smbfs -o username=tridge,password=foobar //fjall/test /data/test
steve@ubuntu:~$

What's going on?  Please help.  Thanks.

---

### Post by Rippey on 2007-01-21
can you post the samba config file of dns-323?

---

### Post by routerstu on 2007-01-30
i ran into similar problems:

jason@Ubunt2:~$ sudo mount -t smbfs -o username=music //192.168.1.50/Volume_1 /media/Music
Password:
mount: wrong fs type, bad option, bad superblock on //192.168.1.50/Volume_1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

jason@Ubunt2:~$ 



I can browse the folder under network servers but i want to be able to play music from it, ie my player can see the music and stream it not copy it locally.

thoughts/ideas?

thanks

---

### Post by routerstu on 2007-01-30
i am now able to mount dns-323 via smbfs and:

[http://www.ubuntuforums.org/showthread.php?t=255872&highlight=smbfs](http://www.ubuntuforums.org/showthread.php?t=255872&highlight=smbfs)


in short i use:

sudo mount -t smbfs //192.168.1.50/Volume_1 /media/Music -o username=music,password=music

---

