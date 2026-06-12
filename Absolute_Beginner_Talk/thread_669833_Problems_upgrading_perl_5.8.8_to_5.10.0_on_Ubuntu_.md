---
title: "Problems upgrading perl 5.8.8 to 5.10.0 on Ubuntu Desktop 7.10"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by j1n3l0 on 2008-01-16
Venerable monks,

Do forgive me for what seems a trivial issue but I am having problems
upgrading my installation of perl from 5.8.8 to 5.10.0 on my Ubuntu
7.10 system. I have followed the standard installation procedure as
follows:

```
% sh Configure -de
% make
% make test
% sudo make install
```

Now this seemed to work fine (admittedly after several attempts) so I
went on to test the new installation. I tried the following:

```
% which perl
/usr/local/bin/perl

% perl -v

This is perl, v5.10.0 built for i686-linux

Copyright 1987-2007, Larry Wall

Perl may be copied only under the terms of either the Artistic License
or the GNU General Public License, which may be found in the Perl 5 source
kit.

Complete documentation for Perl, including FAQ lists, should be found
on this system using "man perl" or "perldoc perl".  If you have access to
the Internet, point your browser at [http://www.perl.org/](http://www.perl.org/), the Perl Home
Page.

% perl -e 'use feature qw(:5.10); say q(Hello World!);'
Hello World!
```

As you can see, that lot works as expected. However when I tried the
following:

```
% sudo perl -MCPAN -e 'shell'
Perl lib version (v5.8.8) doesn't match executable version (v5.10.0) at /usr/lib/perl/5.8/Config.pm line 46.
Compilation failed in require at /usr/local/share/perl/5.8.8/CPAN.pm line 14.
BEGIN failed--compilation aborted at /usr/local/share/perl/5.8.8/CPAN.pm line 14.
Compilation failed in require.
BEGIN failed--compilation aborted.

% perldoc perl
Perl lib version (v5.8.8) doesn't match executable version (v5.10.0) at /usr/lib/perl/5.8/Config.pm line 46.
Compilation failed in require at /usr/share/perl/5.8/Pod/Perldoc.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl/5.8/Pod/Perldoc.pm line 7.
Compilation failed in require at /usr/local/bin/perldoc line 9.
BEGIN failed--compilation aborted at /usr/local/bin/perldoc line 9.
```

For some reason it is still checking the 5.8 version of Config.pm
:(

Is there something obvious I am missing? Is this the wrong place to be
asking this question? Any help would be much appreciated.

---

### Post by beardiggin on 2008-03-01
Try this; uninstall the version you compiled.

sudo make uninstall


If that works see if you can uninstall the version of perl that was on your computer before.Open synaptic package manager from the system menu

System->Administration->Synaptic Package Manager

click "package"  to sort by package.  Then click search "perl"

if you find a package named perl with a green box by it, mark it for removal and click apply. 

Then if you wan to you can try to reinstall the newer version of perl.

---

### Post by cmitch419 on 2008-06-01
From what I understand, you don't uninstall the version of perl that came with ubuntu, because it needs 5.8.8 and you should just install 5.10 it in another directory such as: /usr/local/bin/perl5.10

You can reinstall your 5.8.8 in the Synaptic Package Manager.

---

