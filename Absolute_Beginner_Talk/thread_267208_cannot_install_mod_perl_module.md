---
title: "cannot install mod_perl module"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by itisgood on 2006-09-28
hi everyone

im a begginner to ubuntu
and i tried to install mod_perl on for my perl and apache server

jyao@jyao-laptop:~/mod_perl-2.0.2$ perl Makefile.PL MP_APXS=/usr/local/apache2/bin/apxs

Reading Makefile.PL args from @ARGV
   MP_APXS = /usr/local/apache2/bin/apxs
no conflicting prior mod_perl version found - good.
************* WARNING *************

  Your Perl is configured to link against libgdbm,
  but libgdbm.so was not found.
  You could just symlink it to /usr/lib/libgdbm.so.3.0.0


************* WARNING *************
<finishes without error>

>>make 
................<a lot of files>......
......................................
<then>
/usr/bin/ld: cannot find -lperl
collect2: ld returned 1 exit status
make[1]: *** [mod_perl.so] Error 1
make[1]: Leaving directory `/home/jyao/mod_perl-2.0.2/src/modules/perl'
make: *** [modperl_lib] Error 2
jyao@jyao-laptop:~/mod_perl-2.0.2$

i don know whats going on there, cuz i installed perl and apache quite following the instructions, and they work fine, but it seems im lack of a file there ??

plz help...

---

### Post by whizbaby on 2006-09-28
Did you do
> 
Your Perl is configured to link against libgdbm,
but libgdbm.so was not found.
You could just symlink it to /usr/lib/libgdbm.so.3.0.0

?

---

### Post by itisgood on 2006-09-28
thx u for your reply.

i know that might be the course, but i dont know how to symlink.

what should i type...

---

### Post by whizbaby on 2006-09-28
ln -s *target* *link_name*
ln -link
-s -symbolic
target -the really existing file (/usr/lib/libgdbm.so.3.0.0 in your case)
link_name -the name the link will have(libgdbm.so is mentioned, but without a path)
so let's try (copy-paste)

sudo ln -s /usr/lib/libgdbm.so.3.0.0 /usr/lib/libgdbm.so

type:
ls -la /usr/lib/libgdbm.so to see what you've done.

EDIT: I guessed the path and hope it works. Make sure the *target* exists

---

### Post by itisgood on 2006-09-28
great, it changed the link.

jyao@jyao-laptop:~/mod_perl-2.0.2$ ls -la /usr/lib/libgdbm.so lrwxrwxrwx 1 root root 25 2006-09-29 01:27 /usr/lib/libgdbm.so -> /usr/lib/libgdbm.so.3.0.0

and the warnning doesn't come out anymore,
but the problem still comes when i call >>perl Makefile.PL

/usr/bin/ld: cannot find -lperl
collect2: ld returned 1 exit status
make[1]: *** [mod_perl.so] Error 1
make[1]: Leaving directory `/home/jyao/mod_perl-2.0.2/src/modules/perl'
make: *** [modperl_lib] Error 2
jyao@jyao-laptop:~/mod_perl-2.0.2$

---

### Post by whizbaby on 2006-09-28
Only to know:
you are aware of the fact that
libapache-mod-perl
is available in the repositories? If you still want to compile be sure to have all development packages you need to compile.

---

### Post by itisgood on 2006-09-28
and actually, i have previously installed a low version mod_perl for the perl part, cuz it asks : please provide the path for your apache src:

as im using apache2, so i dont have that, so i skipped the  httpd part according to the INSTALATION:

>>  perl Makefile.PL NO_HTTPD=1

but when i add 
PerRequire conf/startup.pl

into the httpd.conf, it wont be parsed.

so i tried to install this mod_perl, which is version 2.(and got this trouble) 
i didnt delete the previous one, do u think that might be the course?

if it might matter, how can i delet tha module?

---

### Post by itisgood on 2006-09-28
i dont know ....

i have typed this:

jyao@jyao-laptop:~$ sudo apt-get install libapache-mod-perl
Password:
Reading package lists... Done
Building dependency tree... Done
Package libapache-mod-perl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libapache-mod-perl has no installation candidate

does that mean i dont have it ??

---

### Post by whizbaby on 2006-09-28
If it can't find something it usually doesn't mean you have too much installed but that something is missing. Search (e.g. synaptic) packages with *apache* and *dev* in their name , e.g. libapache2-mod-perl2-dev.

---

### Post by itisgood on 2006-09-28
just for correction:
"
but when i add
PerRequire conf/startup.pl

into the httpd.conf, it wont be parsed."

it is :

PerlRequire conf/startup.pl

i have wrote the startup.pl and it works fine

---

### Post by itisgood on 2006-09-28
ive searched,  and found nothing about apache2 has been installed...
and that includes libapache2-mod-perl2
this is weird ,cuz my apache2 is actually working. 

why is this? and does that mean i have to reinstall the apache2?

---

### Post by whizbaby on 2006-09-28
How do you usually install things, you seem to have a special (non-ubuntu-debian-standart) way.

---

### Post by itisgood on 2006-09-28
sometimes use the add/remove 

sometimes eg, the apache2, i download the tar.gz file and use 
>>perl Maekfile.PL
>>make
>>make install

for module installation, i first try >>cpan, if it fails then use >>sudo spt-get install. still fails, >>perl Makefile.PL

so what is the way we are supposed to use? 
so far i have just been keep trying , if it works, i feel lucky, if it doesnt ,i change another way...if all fail... i come to the forum..

:)

should i use add/remove option to reinstall the apache2?

or i should delete apache2 first?

---

### Post by whizbaby on 2006-09-28
The standard way to install is to search for desired programs in the repositories (e.g via *apt-cache search* or *synaptic*) and if such progs are available install them (with apt-get, aptitude, synaptic etc.).
If you want a newer version check if somebody built a .deb package (search on net) and install that with *dpkg -i [I]package_name.deb*[/I]. Only if all this doesn't help (or you just are a curious person) you should try to compile things on your own.

Check
dpkg --get-selections
for apache and remember the complete name, then
dpkg -r *package_name*.
Does it help?

If not, is it perhaps installed in your home?

---

### Post by itisgood on 2006-09-28
thx a lot, 

i downloaded a libperl-dev through add/remove 

and i succeeded in installing the mod_perl.

but the new problem comes. i add the line in the apache server httpd.conf
[B]
LoadModule perl_module /usr/lib/apache2/modules/mod_perl.so
[/B]

and when i start the apache server , it will say.
jyao@jyao-laptop:/usr/local/apache2/bin$ ./apachectl start
httpd: Syntax error on line 55 of /usr/local/apache2/conf/httpd.conf: API module structure `perl_module' in file _/usr/lib/apache2/modules/mod_perl.so is garbled - perhaps this is not an Apache module DSO?_

how can i solve that ??

---

