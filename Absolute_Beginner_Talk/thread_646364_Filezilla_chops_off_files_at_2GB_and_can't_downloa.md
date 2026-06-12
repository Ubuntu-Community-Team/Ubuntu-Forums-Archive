---
title: "Filezilla chops off files at 2GB and can't download larger"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2007-12-21
I am downloading a file from a server larger than 2gb but when it gets to 2gb, filezilla won't let me download the other half.. It won't let me resume either.

---

### Post by akudewan on 2007-12-21
I faced this problem when I was downloading a DVD image. Then I realized that a FAT32 partition cannot handle a file larger than 2GB.

If you're downloading on a FAT partition, try downloading on ext3 instead.

---

### Post by systemintheglitch on 2007-12-21
Totally not a fat32..

---

### Post by insane_alien on 2007-12-21
just tested a 20GB file on filezilla(excessive for a test i know but it was going to have to be transferred anyway) ext3 to XFS filesystems. didn't experience any problems.

do you perhaps have your FTP server set to cut off at 2GB? check it's config file.

---

### Post by rextor on 2008-04-01
I too tried downloading a 4.2 GB ISO image. Every time the file stops downloading at 2 GB. I've tried it on KGet, curl and wget. And i am doing this on an Ext3 partition.

edit:
When i try to resume with
> curl [http://ftp.tw.debian.org/debian-cd/current/amd64/iso-dvd/debian-40r3-amd64-DVD-1.iso](http://ftp.tw.debian.org/debian-cd/current/amd64/iso-dvd/debian-40r3-amd64-DVD-1.iso) -C  - -o disc1.iso

curl says:
> curl: (52) Empty reply from server

edit2:
if this matters.... I am doing this on a 32bit intel system

---

### Post by rextor on 2008-04-02
Has this something to do with a proxy server? I am browsing behind a Squid proxy server.

---

### Post by bred on 2008-04-02
[COLOR="Blue"]well.. never used firezilla, but I use downthemall extension for Firefox and it works fine...[/COLOR]
;)

---

