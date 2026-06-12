---
title: "PHP with dbase support."
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by cydec on 2006-11-30
Can anybody help me out here?

I was wondering if it was possible to get PHP5 up and running with dbase support? Without needing to compile him / recompile him with "--enable-dbase". I don't want to start all over again or have to do everything form scratch.

I'm trying "dbase_open()" but he gives me the usual "undefined function". I already have a apache2 with php up and running but I'm in need of the dbase functions.

I hope it IS possible...

---

### Post by achim.wessling on 2007-02-20
I had the same problem. I could solve it by downloading an RPM from here: [http://rpmseek.com/rpm-pl/php-dbase.html?hl=de&cbd=0:P:0::105](http://rpmseek.com/rpm-pl/php-dbase.html?hl=de&cbd=0:P:0::105)

I unpacked it and put the libary in the extension dir of my php5. I enabled it by putting this in my php.ini:
extension=dbase.so

After a restart of my apache everything worked fine.

achim

---

### Post by Junni on 2007-12-10
I've downloaded the x86 rpm file, and extracted the /usr/lib64/php/extension/dbase.so to /etc/php5/apache2.
Then I changed /etc/php5/apache2/php.ini, enabled extension_dir (extension_dir = "./"). In the dynamic extension section in this file I've added "extension=dbase.so".

Last thing was to restart apache (apachectl restart). Now he's complaining that the mysql extension is not loaded. Do I have to put every extension in the php.ini file now?

I'm using Ubuntu 7.10 x86, with Apache2 and PHP5 (installed through apt-get). I must admit that I'm no Linux expert.

---

### Post by stbe on 2007-12-11
I stored some self-built dbase.so (same php version) here:

/usr/lib/php5/20060613+lfs/dbase.so

I added "extension=dbase.so" to

/etc/php5/apache2/php.ini
/etc/php5/cli/php.ini

---

### Post by Junni on 2007-12-11
Nope, no luck over here. I did the same as you said, and changed the extension_dir to "/usr/lib/php5/20060613+lfs$".

---

### Post by stbe on 2007-12-11
I installed other extensions like php5-gd. Those extensions (.so files) appeared in /usr/lib/php5/20060613+lfs/ -- I'm not sure whether it is a good idea to install other extensions there, too.

But for me it worked to drop dbase.so there and I just added the extension=dbase.so lines. I did not change (uncomment) extension_dir and AFAIR I did nothing else.

I got dbase.so by using the official php package from php.net with "./configure  --prefix=/usr --enable-dbase=shared && make".

---

### Post by RobNY on 2007-12-24
For some reason (and it could have been my fault), the php.ini files were only readable by root.  This meant that changes such as adding dbase.so worked for apache, but not for the client version of php (unprivileged).  Chmod'ing to 644 fixed this. I can't say it is the correct thing to do, but the ini files in the conf.d directory already had these permissions.

---

### Post by stbe on 2007-12-27
php.ini files have 644 permissions here. I never changed permissions and it is a quite fresh install of Ubuntu 7.10 (server).

---

### Post by ernest0 on 2008-01-21
I try to run the sulution, for me don't work
then I saw the log this lines

[Mon Jan 21 21:24:23 2008] [notice] caught SIGWINCH, shutting down gracefully
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613/dbase.so' - /usr/lib/php5/20060613/dbase.so: wrong ELF class: ELFCLASS32 in Unknown on line 0
[Mon Jan 21 21:24:34 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 configured -- resuming normal operations


probably I need a specific dbase.so file, my .so was download from here : 
[http://resources.ync.pl/PLD-TEST/BUILD/php-5.2.3/modules/](http://resources.ync.pl/PLD-TEST/BUILD/php-5.2.3/modules/)

---

