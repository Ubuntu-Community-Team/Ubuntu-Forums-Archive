---
title: "GAH!  Please HELP, Update Manager problems"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Scut_Farkus on 2008-02-27
Well, I'm still struggling with Update Manager and Gutsy.

Tried to update and the Update Manager broke the system so that now I can no longer install anything.

[HTML]SOFTWARE INDEX IS BROKEN
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.[/HTML]

I kept seeing lots of problems with various archive files, so I simply removed the offending entries by navigating to /var/cache/apt/archives and then using rm to get rid of the corrupted file.  Then I'd run sudo apt-get update, get another error message and kill THAT file.  This went on for a while until I kept getting the same error messages over and over again.  Here's the result of trying to run the sudo apt-get install -f command the system suggested:

[HTML]ed@ed-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libeel2-2 perl
Suggested packages:
  libterm-readline-gnu-perl libterm-readline-perl-perl
Recommended packages:
  perl-doc
The following packages will be upgraded:
  libeel2-2 perl
2 upgraded, 0 newly installed, 0 to remove and 180 not upgraded.
4 not fully installed or removed.
Need to get 0B/3679kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: Perl may be unconfigured (syntax error at /usr/lib/perl/5.8/IO/Handle.pm line 79, near "sub DESTROY "
Compilation failed in require at /usr/lib/perl/5.8/IO/Seekable.pm line 9.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/IO/Seekable.pm line 9.
Compilation failed in require at /usr/lib/perl/5.8/IO/File.pm line 11.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/IO/File.pm line 11.
Compilation failed in require at /usr/share/perl/5.8/FileHandle.pm line 9.
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
(Reading database ... 88883 files and directories currently installed.)
Preparing to replace perl 5.8.8-7ubuntu3 (using .../perl_5.8.8-7ubuntu3.1_i386.deb) ...
Unpacking replacement perl ...
dpkg: error processing /var/cache/apt/archives/perl_5.8.8-7ubuntu3.1_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/perl_5.8.8-7ubuntu3.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ed@ed-desktop:~$ [/HTML]

This is the same problem that has been plaguing me since I tried to upgrade to Gutsy over a month ago.  Dapper seems to run pretty well, but Gutsy keeps giving me problems.  I purchased this install disk from Canonical.  These are the same errors as the ISO I downloaded.  I have run memtest86 and the RAM tests fine.  I also got a code to test badblocks on the HDD.  That tested fine, too.  I'm running out of options due to the frustration factor.  

Thanks in advance!  :)

---

### Post by glennric on 2008-02-27
You seem to have a corrupt download of the package file.  Try 
```
sudo rm /var/cache/apt/archives/perl_5.8.8-7ubuntu3.1_i386.deb
```
and then try
```
sudo apt-get install -f
```

---

### Post by Scut_Farkus on 2008-02-27
HEY!  :)

Thanks for the quick response!

Here are the results of your instructions:

[HTML]ed@ed-desktop:~$ sudo rm /var/cache/apt/archives/perl_5.8.8-7ubuntu3.1_i386.deb
[sudo] password for ed:
ed@ed-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libeel2-2 perl
Suggested packages:
  libterm-readline-gnu-perl libterm-readline-perl-perl
Recommended packages:
  perl-doc
The following packages will be upgraded:
  libeel2-2 perl
2 upgraded, 0 newly installed, 0 to remove and 180 not upgraded.
4 not fully installed or removed.
Need to get 3387kB/3679kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com gutsy-updates/main perl 5.8.8-7ubuntu3.1 [3387kB]
Fetched 3387kB in 22s (151kB/s)                                                
debconf: Perl may be unconfigured (syntax error at /usr/lib/perl/5.8/IO/Handle.pm line 79, near "sub DESTROY "
Compilation failed in require at /usr/lib/perl/5.8/IO/Seekable.pm line 9.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/IO/Seekable.pm line 9.
Compilation failed in require at /usr/lib/perl/5.8/IO/File.pm line 11.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/IO/File.pm line 11.
Compilation failed in require at /usr/share/perl/5.8/FileHandle.pm line 9.
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
(Reading database ... 88883 files and directories currently installed.)
Preparing to replace perl 5.8.8-7ubuntu3 (using .../perl_5.8.8-7ubuntu3.1_i386.deb) ...
Unpacking replacement perl ...
Setting up perl-base (5.8.8-7ubuntu3.1) ...
(Reading database ... 88739 files and directories currently installed.)
Preparing to replace libeel2-2 2.20.0-0ubuntu1 (using .../libeel2-2_2.20.0-0ubuntu1_i386.deb) ...
Unpacking replacement libeel2-2 ...
Setting up libdb4.4 (4.4.20-8.1ubuntu3.1) ...
Setting up libperl5.8 (5.8.8-7ubuntu3.1) ...

Setting up libeel2-2 (2.20.0-0ubuntu1) ...

Setting up perl-modules (5.8.8-7ubuntu3.1) ...
Setting up perl (5.8.8-7ubuntu3.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
ed@ed-desktop:~$ 
[/HTML]

I'm not sure if it did what it was supposed to.  It seems like some things worked, but I see errors on the perl stuff.  What's next?  :)

OH!  Update manager appears to be up and running again, though.  Thanks a lot!  I'm afraid to run it, though.  Do you like Update Manager, or should I just use the terminal?

Thanks again!

---

### Post by glennric on 2008-02-27
I always prefer the terminal to a GUI as it is faster, but the GUI's are usually easier to learn.  It is your preference.  As to the other error you are having, I believe that it should go away now.  I think that was due to the bad download as well.  The reason it was still there is because that came before apt-get replaced perl.

---

### Post by Scut_Farkus on 2008-02-28
Well, I decided to run Update Manager again.  Here's what happened:

[HTML]E: /var/cache/apt/archives/language-pack-en-base_1%3a7.10+20080205_all.deb: short read in buffer_copy (backend dpkg-deb during `./usr/share/locale-langpack/en_AU/LC_MESSAGES/gcc-4.1.mo')
E: /var/cache/apt/archives/language-pack-gnome-en-base_1%3a7.10+20080205_all.deb: subprocess dpkg-deb --fsys-tarfile returned error exit status 2
E: /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb: subprocess pre-installation script returned error exit status 9[/HTML]

I tried to do this:

[HTML]rm /var/cache/apt/archives/language-pack-en-base_1%3a7.10+20080205_all.deb[/HTML]

and then this:

[HTML]rm /var/cache/apt/archives/language-pack-gnome-en-base_1%3a7.10+20080205_all.deb[/HTML]

but I got the same error message (as above).  Not really sure what to do if the remove doesn't kill off the offending file.  Any ideas?

---

