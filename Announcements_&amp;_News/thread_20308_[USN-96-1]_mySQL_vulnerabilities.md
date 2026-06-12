---
title: "[USN-96-1] mySQL vulnerabilities"
date: 2005-03-16
forum: Announcements &amp; News
---

### Post by Martin Pitt on 2005-03-16
===========================================================
Ubuntu Security Notice USN-96-1		     March 16, 2005
mysql-dfsg vulnerabilities
CAN-2005-0709, CAN-2005-0710, CAN-2005-0711
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 4.10 (Warty Warthog)

The following packages are affected:

mysql-server

The problem can be corrected by upgrading the affected package to
version 4.0.20-2ubuntu1.4. In general, a standard system upgrade is
sufficient to effect the necessary changes.

Details follow:

Stefano Di Paola discovered three privilege escalation flaws in the MySQL
server:

- If an authenticated user had INSERT privileges on the 'mysql' administrative
  database, the CREATE FUNCTION command allowed that user to use libc functions
  to execute arbitrary code with the privileges of the database server (user
  'mysql'). (CAN-2005-0709)

- If an authenticated user had INSERT privileges on the 'mysql' administrative
  database, it was possible to load a library located in an arbitrary directory
  by using INSERT INTO mysql.func instead of CREATE FUNCTION.  This allowed the
  user to execute arbitrary code with the privileges of the database server (user
  'mysql'). (CAN-2005-0710)

- Temporary files belonging to tables created with CREATE TEMPORARY TABLE were
  handled in an insecure way. This allowed any local computer user to overwrite
  arbitrary files with the privileges of the database server. (CAN-2005-0711)

Matt Brubeck discovered that the directory /usr/share/mysql/ was owned and
writable by the database server user 'mysql'. This directory contains scripts
which are usually run by root. This allowed a local attacker who already has
mysql privileges to gain full root access by modifying a script and tricking
root into executing it.

  Source archives:
    [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-dfsg_4.0.20-2ubuntu1.4.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-dfsg_4.0.20-2ubuntu1.4.diff.gz)
      Size/MD5:   174589 a7bbe440e9d8cbcf41e7dcbf33254ba5
    [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-dfsg_4.0.20-2ubuntu1.4.dsc](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-dfsg_4.0.20-2ubuntu1.4.dsc)
      Size/MD5:      892 8410cb63b79655f10df1c2a797249350
    [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-dfsg_4.0.20.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-dfsg_4.0.20.orig.tar.gz)
      Size/MD5:  9760117 f092867f6df2f50b34b8065312b9fb2b

  Architecture independent packages:

    [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-common_4.0.20-2ubuntu1.4_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-common_4.0.20-2ubuntu1.4_all.deb)
      Size/MD5:    24600 8cce579993297755f7af60742b0c7738

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/libmysqlclient-dev_4.0.20-2ubuntu1.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/libmysqlclient-dev_4.0.20-2ubuntu1.4_amd64.deb)
      Size/MD5:  2810480 35a6f5626620f1446a82ba657731c524
    [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/libmysqlclient12_4.0.20-2ubuntu1.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/libmysqlclient12_4.0.20-2ubuntu1.4_amd64.deb)
      Size/MD5:   304662 a4b2c340bcbad53aebe3736b131ab608
    [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-client_4.0.20-2ubuntu1.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-client_4.0.20-2ubuntu1.4_amd64.deb)
      Size/MD5:   422698 5c4fc21698901aa4d895eb8e14b06b54
    [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-server_4.0.20-2ubuntu1.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-server_4.0.20-2ubuntu1.4_amd64.deb)
      Size/MD5:  3577580 ddddf044b09cc3860fbd18939ba4607f

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/libmysqlclient-dev_4.0.20-2ubuntu1.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/libmysqlclient-dev_4.0.20-2ubuntu1.4_i386.deb)
      Size/MD5:  2773926 c117672f9fed7ab0e3fe1232880f9262
    [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/libmysqlclient12_4.0.20-2ubuntu1.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/libmysqlclient12_4.0.20-2ubuntu1.4_i386.deb)
      Size/MD5:   287600 acd9b30e3e6ef2391cd36c208202b633
    [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-client_4.0.20-2ubuntu1.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-client_4.0.20-2ubuntu1.4_i386.deb)
      Size/MD5:   396652 0e753c494924f6d63a8a2ed772c86daa
    [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-server_4.0.20-2ubuntu1.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-server_4.0.20-2ubuntu1.4_i386.deb)
      Size/MD5:  3486636 aa84280881da8c2fe826df5c30b7905e

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/libmysqlclient-dev_4.0.20-2ubuntu1.4_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/libmysqlclient-dev_4.0.20-2ubuntu1.4_powerpc.deb)
      Size/MD5:  3109952 e36cf9560a5d8f345801cacb0c2c2c58
    [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/libmysqlclient12_4.0.20-2ubuntu1.4_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/libmysqlclient12_4.0.20-2ubuntu1.4_powerpc.deb)
      Size/MD5:   308292 a8ddf7818b3d7d4aa280eb862560f5ed
    [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-client_4.0.20-2ubuntu1.4_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-client_4.0.20-2ubuntu1.4_powerpc.deb)
      Size/MD5:   452118 7037cde3771768530ea54d7565bd4a5e
    [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-server_4.0.20-2ubuntu1.4_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg/mysql-server_4.0.20-2ubuntu1.4_powerpc.deb)
      Size/MD5:  3770076 211d6d9fb5899f80dd216cc76b854148

-- 
ubuntu-security-announce mailing list
[email]ubuntu-security-announce@lists.ubuntu.com[/email]
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.2.5 (GNU/Linux)

iD8DBQFCN+q6DecnbV4Fd/IRAvB7AKC/jYDDjp9EcG9idFnQlEkPTRiljgCgusPZ
I7cpx4JWBiEP0G60PPLArnA=
=MzeD
-----END PGP SIGNATURE-----

---

