---
title: "Insatlling problems"
date: 2005-11-17
forum: Absolute Beginner Talk
---

### Post by natman on 2005-11-17
Hi i have just downloaded a program called " polymake", i tried to look for it on the synapti package manager but got the following message

> W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-amd64_Packages) - stat (2 No such file or directory)


Anyway i found it on the web, and downloaded the file to the desktop, how do 
iinstall it, if possible is there an idots guide to doing this.
 The file is " polymake-2.10.tar.bz2" if that make any difference.

Thanks

---

### Post by matthewv on 2005-11-17
If you really must install it, heres how:
The file looks like it is source code, so we're going ot have to compile it.
Go to the command line, and navigate to your desktop. Then ```

bunzip2 polymake-2.10.tar.bz2
tar -xvf polymake-2.10.tar
cd polymake-2.10
./configure
make
sudo checkinstall

```
Hope it works

---

### Post by davmac on 2005-11-17
For the first part of your problem it looks, on first appearance, like a net access problem from synaptic. Obviously you've got a connection because you've downloaded the source package. Do you go via a proxy to access the internet?

If you start up a terminal and type "sudo apt-get update" what do you get?

For info about installing from source, have a look at [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html) but I would recommend working away the first problem and getting synaptic or apt-get working, because, if you want to remove the package later, it is so much easier if you've used the package management stuff to install it.

Hope this helps,

Dave Mac

---

### Post by natman on 2005-11-17
ok everthing you said seemed to work fine, but at one point of the install it said the following.
> *************************************************************
*********               WARNING:                    *********

Your C++ compiler g++ is apparently NOT an official release.
You may try to compile polymake with it, but if this fails,
please resort to one of versions recommended in the
Installation Guide before sending us a bug report.

*************************************************************
*************************************************************

Which C++ compiler should be used? [g++]

I use Anjuta to write C programs, so what should i do next in the install

---

### Post by matthewv on 2005-11-17
Problem.. it looks like it wants a different version of the compiler, but to download that different version you'll need synaptic working. Did the install or compile still continue after that message, or did it stop?? If it continued, you might be fine.

---

### Post by natman on 2005-11-17
yeah i keep going on with your command, everthing seemed ok, i just have no idea how to run the program,
I typed polymake in a terminal and it said command not found.

---

### Post by matthewv on 2005-11-17
When you ran sudo checkinstall, it would have created a .deb file in the folder. Try navigating to that folder, and running ```
sudo dpkg -i <filename.deb>
```

---

### Post by natman on 2005-11-17
Yeah i just assumed that last part wasnt to important
Ran it now and i get

> sudo: checkinstall: command not found


---

### Post by matthewv on 2005-11-17
[QUOTE=natman]Yeah i just assumed that last part wasnt to important
Ran it now and i get[/QUOTE]
Sorry, run ```
sudo apt-get install checkinstall
```and then run the sudo checkinstall

EDIT: If you're package manager isn't working, you might not be able to install checkinstall

---

### Post by natman on 2005-11-17
Ran it and got the following

> The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]:

Preparing package documentation...OK

Installing with "make install"...

========================= Installation results ===========================

Copying documentation directory...
perl support/install.pl -d -m 755 /usr/local/share/polymake
[ -z "" -o ! -f "" ] || perl support/install.pl -m 644  /usr/local/share/polymake
perl support/install.pl -m 755 -U -X CVS -e DefaultAppName=polytope -e InstallTop=/usr/local/share/polymake -X testsuite -X ext -P /usr/bin/perl perl /usr/local/share/polymake/perl
perl support/install.pl -m 755 -U -X CVS  modules/common/perllib /usr/local/share/polymake/modules/common/perllib
perl support/install.pl -m 755 -U -X CVS  modules/common/rules /usr/local/share/polymake/modules/common/rules
perl support/install.pl -m 755 -U -X CVS  modules/graph/perllib /usr/local/share/polymake/modules/graph/perllib
perl support/install.pl -m 755 -U -X CVS  modules/graph/rules /usr/local/share/polymake/modules/graph/rules
perl support/install.pl -m 755 -U -X CVS -e InstallTop=/usr/local/share/polymake -P /usr/bin/perl apps/polytope/scripts /usr/local/share/polymake/apps/polytope/scripts
perl support/install.pl -m 755 -U -X CVS  apps/polytope/perllib /usr/local/share/polymake/apps/polytope/perllib
perl support/install.pl -m 755 -U -X CVS  apps/polytope/rules /usr/local/share/polymake/apps/polytope/rules
perl support/install.pl -m 755 -U -X CVS  apps/topaz/rules /usr/local/share/polymake/apps/topaz/rules
perl support/install.pl -d -m 755 -U /usr/local/share/polymake/jars
perl support/install.pl -m 755 java_build/polytope.jar java_build/common.jar java_build/graph.jar /usr/local/share/polymake/jars
perl support/install.pl -m 755 -U -X CVS  povray /usr/local/share/polymake/povray
perl support/install.pl -m 755 -U -X CVS  scripts /usr/local/share/polymake/scripts
make[1]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp'
make  all-recursive
make[2]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp'
Making all in tests
make[3]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tests'
Making all in .
make[4]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tests'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tests'
Making all in devel
make[4]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tests/devel'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tests/devel'
Making all in mpn
make[4]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tests/mpn'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tests/mpn'
Making all in mpz
make[4]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tests/mpz'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tests/mpz'
Making all in mpq
make[4]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tests/mpq'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tests/mpq'
Making all in mpf
make[4]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tests/mpf'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tests/mpf'
Making all in rand
make[4]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tests/rand'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tests/rand'
Making all in misc
make[4]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tests/misc'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tests/misc'
Making all in cxx
make[4]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tests/cxx'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tests/cxx'
Making all in mpbsd
make[4]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tests/mpbsd'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tests/mpbsd'
make[3]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tests'
Making all in mpn
make[3]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/mpn'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/mpn'
Making all in mpz
make[3]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/mpz'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/mpz'
Making all in mpq
make[3]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/mpq'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/mpq'
Making all in mpf
make[3]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/mpf'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/mpf'
Making all in printf
make[3]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/printf'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/printf'
Making all in scanf
make[3]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/scanf'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/scanf'
Making all in cxx
make[3]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/cxx'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/cxx'
Making all in mpbsd
make[3]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/mpbsd'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/mpbsd'
Making all in demos
make[3]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/demos'
Making all in calc
make[4]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/demos/calc'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/demos/calc'
Making all in expr
make[4]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/demos/expr'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/demos/expr'
make[4]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/demos'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/demos'
make[3]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/demos'
Making all in tune
make[3]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tune'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp/tune'
make[3]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp'
make[3]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp'
make[2]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp'
make[1]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/external/gmp'
make[1]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/apps/polytope'
make[2]: Entering directory `/home/natman/polymake-2.1.0/build.x86_64/lib'
g++ -c -o Integer.o   -I../../lib/poly_client/include -I../../lib/PTL/include -I../../lib/PTL/include/std -I../../lib/gmp_wrapper/include -I../external/gmp -Wall -ftemplate-depth-200 -DALL_PLAUSIBLE_CHECKS=0 -O3 -MD -MT 'libpoly.a(Integer.o)' ../../lib/gmp_wrapper/src/Integer.cc
In file included from ../../lib/PTL/include/type_manip.h:22,
                 from ../../lib/PTL/include/operations_basic_defs.h:24,
                 from ../../lib/PTL/include/Integer.h:25,
                 from ../../lib/gmp_wrapper/src/Integer.cc:22:
../../lib/PTL/include/std/bits/type_traits.h:16:35: error: bits/type_traits.h: No such file or directory
../../lib/PTL/include/type_manip.h:103: error: wrong number of template arguments (1, should be 2)
../../lib/PTL/include/type_manip.h:86: error: provided for &#8216;template<class T1, class T2> struct pm::identical_raw&#8217;
../../lib/PTL/include/type_manip.h:103: error: &#8216;is_POD_type&#8217; is not a member of &#8216;<declaration error>&#8217;
../../lib/PTL/include/type_manip.h:103: error: a comma operator cannot appear in a constant-expression
../../lib/PTL/include/type_manip.h:103: error: &#8216;::answer&#8217; has not been declared
../../lib/PTL/include/type_manip.h:104: error: template argument 1 is invalid
../../lib/PTL/include/type_manip.h:103: error: expected nested-name-specifier
../../lib/PTL/include/type_manip.h:104: error: typedef name may not be a nested-name-specifier
../../lib/PTL/include/type_manip.h:104: error: expected &#8216;;&#8217; before &#8216;type&#8217;
../../lib/PTL/include/type_manip.h:105: error: &#8216;type&#8217; does not name a type
../../lib/PTL/include/type_manip.h:135: error: wrong number of template arguments (1, should be 2)
../../lib/PTL/include/type_manip.h:86: error: provided for &#8216;template<class T1, class T2> struct pm::identical_raw&#8217;
../../lib/PTL/include/type_manip.h:135: error: &#8216;has_trivial_default_constructor&#8217; is not a member of &#8216;<declaration error>&#8217;
../../lib/PTL/include/type_manip.h:135: error: expected &#8216;;&#8217; before &#8216;>&#8217; token
../../lib/PTL/include/type_manip.h:1217: warning: minimum/maximum operators are deprecated
../../lib/PTL/include/type_manip.h:1217: warning: minimum/maximum operators are deprecated
../../lib/PTL/include/type_manip.h: In function &#8216;void pm::relocate(T*, T*)&#8217;:
../../lib/PTL/include/type_manip.h:1536: error: expected nested-name-specifier before &#8216;__type_traits&#8217;
../../lib/PTL/include/type_manip.h:1536: error: expected primary-expression before &#8216;>&#8217; token
../../lib/PTL/include/type_manip.h:1536: error: &#8216;::is_POD_type&#8217; has not been declared
../../lib/PTL/include/operations_basic_defs.h: At global scope:
../../lib/PTL/include/operations_basic_defs.h: In instantiation of &#8216;pm::operations::div_scalar<int, Integer, int>&#8217;:
../../lib/PTL/include/Integer.h:59:   instantiated from here
../../lib/PTL/include/operations_basic_defs.h:182: error: no type named &#8216;type&#8217; in &#8216;struct pm::function_argument<Integer>&#8217;
../../lib/PTL/include/operations_basic_defs.h:185: error: no type named &#8216;type&#8217; in &#8216;struct pm::function_argument<Integer>&#8217;
../../lib/PTL/include/operations_basic_defs.h: In instantiation of &#8216;pm::operations::div_scalar<long int, Integer, long int>&#8217;:
../../lib/PTL/include/Integer.h:62:   instantiated from here
../../lib/PTL/include/operations_basic_defs.h:182: error: no type named &#8216;type&#8217; in &#8216;struct pm::function_argument<Integer>&#8217;
../../lib/PTL/include/operations_basic_defs.h:185: error: no type named &#8216;type&#8217; in &#8216;struct pm::function_argument<Integer>&#8217;
../../lib/PTL/include/operations_basic_defs.h: In instantiation of &#8216;pm::operations::mod_scalar<Integer, long int, long int>&#8217;:
../../lib/PTL/include/Integer.h:65:   instantiated from here
../../lib/PTL/include/operations_basic_defs.h:199: error: no type named &#8216;type&#8217; in &#8216;struct pm::function_argument<long int>&#8217;
../../lib/PTL/include/operations_basic_defs.h:202: error: no type named &#8216;type&#8217; in &#8216;struct pm::function_argument<long int>&#8217;
../../lib/PTL/include/operations_basic_defs.h: In instantiation of &#8216;pm::operations::mod_scalar<Integer, int, int>&#8217;:
../../lib/PTL/include/Integer.h:68:   instantiated from here
../../lib/PTL/include/operations_basic_defs.h:199: error: no type named &#8216;type&#8217; in &#8216;struct pm::function_argument<int>&#8217;
../../lib/PTL/include/operations_basic_defs.h:202: error: no type named &#8216;type&#8217; in &#8216;struct pm::function_argument<int>&#8217;
make[2]: *** [Integer.o] Error 1
make[2]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/lib'
make[1]: *** [_build_core_lib] Error 2
make[1]: Leaving directory `/home/natman/polymake-2.1.0/build.x86_64/apps/polytope'
make: *** [all] Error 2

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK


---

### Post by matthewv on 2005-11-17
It looks like some dependancy issue in compiling, which leaves me pretty much stuck. You'll probably need some help from someone who knows more about this than me. Only thing I can suggest is running all the steps from ./configure again.

---

### Post by natman on 2005-11-17
In relation to this bit

>  ************************************************** ***********
********* WARNING: *********

Your C++ compiler g++ is apparently NOT an official release.
You may try to compile polymake with it, but if this fails,
please resort to one of versions recommended in the
Installation Guide before sending us a bug report.

************************************************** ***********
************************************************** ***********

Which C++ compiler should be used? [g++]

How do i make it an official release?and generally get rid of this problem

---

### Post by matthewv on 2005-11-17
try installing build-essential, or g++, or cpp, or something like that.. thats all i can think of

---

