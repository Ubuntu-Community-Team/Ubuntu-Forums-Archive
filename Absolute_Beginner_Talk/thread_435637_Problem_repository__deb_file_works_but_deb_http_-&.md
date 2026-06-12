---
title: "Problem repository  deb file:/ works but deb http:// -&gt; problems"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by byenary on 2007-05-07
Hello,

I have made a repository to install a program wich depends on some other programs, in the future we need to install this program a lot.
So im making a repo to avoid to fetch the extra files from the net. 
It works but there are a couple files he can't find.

I have build the repo using apt-ftparchive ([http://hausheer.osola.com/docs/14)](http://hausheer.osola.com/docs/14)).
The repo seems find and when using it it does install most of the debs. For some debs i get 404 not found while they were build in the same package and are all located in the same directory.
I assume this has something to do with apache cause when i copy the repo to a local machine and do a 
deb file :/...
instead of 
deb [http://.](http://.)..
It al works fine, so i think the problem has something to do with strang *.deb files ?
I made de repo chmod 777 to be sure its not a problem with rights.
So when using this repo and do an upgrade all files are being installed execpt for
the files starting with language, dnsutils and libbind9-0 they give a 404 Not Found
suggesitons ?? 

root@Backupsrv:/var/www/apt2/dists/dapper/djmaticdep/binary-i386# ls -all
total 10720
drwxr-xr-x  2 root root    8192 2007-05-07 10:55 .
drwxr-xr-x  3 root root    4096 2007-05-04 13:14 ..
-rwxrwxrwx  1 root root  175268 2007-05-04 15:22 dnsutils_1%3a9.3.2-2ubuntu1.2_i386.deb
-rwxrwxrwx  1 root root   52026 2007-05-04 15:22 dosfstools_2.11-2.1ubuntu1_i386.deb
-rwxrwxrwx  1 root root 1865504 2007-05-04 15:22 dpkg_1.13.11ubuntu6_i386.deb
-rwxrwxrwx  1 root root 1865828 2007-05-04 15:22 dpkg_1.13.11ubuntu7_i386.deb
-rwxrwxrwx  1 root root  117056 2007-05-04 15:22 dselect_1.13.11ubuntu7_i386.deb
-rwxrwxrwx  1 root root   78392 2007-05-04 15:22 e2fslibs_1.38-2ubuntu2_i386.deb
-rwxrwxrwx  1 root root  269848 2007-05-04 15:22 e2fsprogs_1.38-2ubuntu2_i386.deb
-rwxrwxrwx  1 root root  214256 2007-05-04 15:22 info_4.8-4ubuntu0.1_i386.deb
-rwxrwxrwx  1 root root   32248 2007-05-04 15:22 initramfs-tools_0.40ubuntu32_all.deb
-rwxrwxrwx  1 root root   45444 2007-05-04 15:22 initscripts_2.86.ds1-6ubuntu32_i386.deb
-rwxrwxrwx  1 root root  971950 2007-05-04 15:22 iproute_20041019-4ubuntu5_i386.deb
-rwxrwxrwx  1 root root   39932 2007-05-04 15:22 iputils-ping_3%3a20020927-3ubuntu1_i386.deb
-rwxrwxrwx  1 root root  262692 2007-05-04 15:22 jfsutils_1.1.8-1_i386.deb
-rwxrwxrwx  1 root root   97286 2007-05-04 15:22 klibc-utils_1.1.16-1ubuntu5_i386.deb
-rwxrwxrwx  1 root root   40428 2007-05-04 15:22 klogd_1.4.1-17ubuntu7_i386.deb
-rwxrwxrwx  1 root root    2160 2007-05-04 15:22 language-pack-en_1%3a6.06+20070129_all.deb
-rwxrwxrwx  1 root root 3015024 2007-05-04 15:22 language-pack-en-base_1%3a6.06+20070129_all.deb
-rwxrwxrwx  1 root root    2168 2007-05-04 15:22 language-pack-nl_1%3a6.06+20070129_all.deb
-rwxrwxrwx  1 root root 1060710 2007-05-04 15:22 language-pack-nl-base_1%3a6.06+20070129_all.deb
-rwxrwxrwx  1 root root  108808 2007-05-04 15:22 less_394-1_i386.deb
-rwxrwxrwx  1 root root   15098 2007-05-04 15:22 libacl1_2.2.34-1ubuntu1_i386.deb
-rwxrwxrwx  1 root root  311270 2007-05-04 15:22 libasound2_1.0.10-2ubuntu4_i386.deb
-rwxrwxrwx  1 root root   67932 2007-05-04 15:22 libatm1_2.4.1-17_i386.deb
-rwxrwxrwx  1 root root    7916 2007-05-04 15:22 libattr1_2.4.25-1_i386.deb
-rwxrwxrwx  1 root root   91098 2007-05-04 15:22 libbind9-0_1%3a9.3.2-2ubuntu1.2_i386.deb
-rw-r--r--  1 root root   20822 2007-05-07 10:55 Packages
-rw-r--r--  1 root root    6214 2007-05-07 10:55 Packages.bz2
-rw-r--r--  1 root root    6231 2007-05-07 10:55 Packages.gz
root@Backupsrv:/var/www/apt2/dists/dapper/djmaticdep/binary-i386#

---

### Post by rai4shu2 on 2007-05-07
It might be getting confused about the files with the <number>%3a in them. Try renaming those files (so they don't have the number%3a in them).

---

### Post by byenary on 2007-05-07
You are right,
It is a solution to rename the files without the % and rebuild the repo, but still the deb files are download like that from ubuntu's server so it must be possible to configure the apache to handle it, ill search a bit for that...

Thx

---

