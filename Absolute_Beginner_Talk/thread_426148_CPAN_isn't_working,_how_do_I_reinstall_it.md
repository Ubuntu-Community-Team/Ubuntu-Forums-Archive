---
title: "CPAN isn't working, how do I reinstall it?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Mortuis on 2007-04-28
A few months ago I needed some Perl libraries.  Being new to Perl I didn't really know what CPAN was, so when I manually compiled/install the libraries from the CPAN site, I guess the CPAN command line got installed as well.  I remember the questions it would ask me were confusing, but I did my best and just went with it because I wanted to get started learning Perl.  Today I have a better understanding of what CPAN is, and would like to use the command line to install libraries rather than manually downloading the source and compiling it.  However, the command line doesn't seem to work.  Is there some way I can reconfigure it?

> cpan> install Bundle::CPAN
CPAN: Storable loaded ok
Going to read /home/john/.cpan/Metadata
Warning: Found only 0 objects in /home/john/.cpan/Metadata
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  [ftp://archive.progeny.com/CPAN/authors/01mailrc.txt.gz](ftp://archive.progeny.com/CPAN/authors/01mailrc.txt.gz)
LWP failed with code[500] message[LWP::Protocol::MyFTP: connect: Connection refused]
Fetching with Net::FTP:
  [ftp://archive.progeny.com/CPAN/authors/01mailrc.txt.gz](ftp://archive.progeny.com/CPAN/authors/01mailrc.txt.gz)

Trying with "/usr/bin/wget -O -" to get
    [ftp://archive.progeny.com/CPAN/authors/01mailrc.txt.gz](ftp://archive.progeny.com/CPAN/authors/01mailrc.txt.gz)
--09:12:20--  [ftp://archive.progeny.com/CPAN/authors/01mailrc.txt.gz](ftp://archive.progeny.com/CPAN/authors/01mailrc.txt.gz)
           => `-'
Resolving archive.progeny.com... 216.54.159.98
Connecting to archive.progeny.com|216.54.159.98|:21... failed: Connection refused.

System call "/usr/bin/wget -O - "ftp://archive.progeny.com/CPAN/authors/01mailrc.txt.gz"  > /home/john/.cpan/sources/authors/01mailrc.txt"
returned status 1 (wstat 256)
Warning: expected file [/home/john/.cpan/sources/authors/01mailrc.txt.gz] doesn't exist
Issuing "/usr/bin/ftp -n"
ftp: connect: Connection refused
Not connected.
Local directory now /home/john/.cpan/sources/authors
Not connected.
Not connected.
Not connected.
Not connected.
Not connected.
Bad luck... Still failed!
Can't access URL [ftp://archive.progeny.com/CPAN/authors/01mailrc.txt.gz](ftp://archive.progeny.com/CPAN/authors/01mailrc.txt.gz).

Please check, if the URLs I found in your configuration file
([ftp://archive.progeny.com/CPAN/](ftp://archive.progeny.com/CPAN/)) are valid. The urllist can be edited.
E.g. with 'o conf urllist push ftp://myurl/'

Could not fetch authors/01mailrc.txt.gz
Fetching with LWP:
  [ftp://archive.progeny.com/CPAN/modules/02packages.details.txt.gz](ftp://archive.progeny.com/CPAN/modules/02packages.details.txt.gz)
LWP failed with code[500] message[LWP::Protocol::MyFTP: connect: Connection refused]
Fetching with Net::FTP:
  [ftp://archive.progeny.com/CPAN/modules/02packages.details.txt.gz](ftp://archive.progeny.com/CPAN/modules/02packages.details.txt.gz)

Trying with "/usr/bin/wget -O -" to get
    [ftp://archive.progeny.com/CPAN/modules/02packages.details.txt.gz](ftp://archive.progeny.com/CPAN/modules/02packages.details.txt.gz)
--09:12:25--  [ftp://archive.progeny.com/CPAN/modules/02packages.details.txt.gz](ftp://archive.progeny.com/CPAN/modules/02packages.details.txt.gz)
           => `-'
Resolving archive.progeny.com... 216.54.159.98
Connecting to archive.progeny.com|216.54.159.98|:21... failed: Connection refused.

System call "/usr/bin/wget -O - "ftp://archive.progeny.com/CPAN/modules/02packages.details.txt.gz"  > /home/john/.cpan/sources/modules/02packages.details.txt"
returned status 1 (wstat 256)
Warning: expected file [/home/john/.cpan/sources/modules/02packages.details.txt.gz] doesn't exist
Issuing "/usr/bin/ftp -n"
ftp: connect: Connection refused
Not connected.
Local directory now /home/john/.cpan/sources/modules
Not connected.
Not connected.
Not connected.
Not connected.
Not connected.
Bad luck... Still failed!
Can't access URL [ftp://archive.progeny.com/CPAN/modules/02packages.details.txt.gz](ftp://archive.progeny.com/CPAN/modules/02packages.details.txt.gz).

Please check, if the URLs I found in your configuration file
([ftp://archive.progeny.com/CPAN/](ftp://archive.progeny.com/CPAN/)) are valid. The urllist can be edited.
E.g. with 'o conf urllist push ftp://myurl/'

Could not fetch modules/02packages.details.txt.gz
Fetching with LWP:
  [ftp://archive.progeny.com/CPAN/modules/03modlist.data.gz](ftp://archive.progeny.com/CPAN/modules/03modlist.data.gz)
LWP failed with code[500] message[LWP::Protocol::MyFTP: connect: Connection refused]
Fetching with Net::FTP:
  [ftp://archive.progeny.com/CPAN/modules/03modlist.data.gz](ftp://archive.progeny.com/CPAN/modules/03modlist.data.gz)

Trying with "/usr/bin/wget -O -" to get
    [ftp://archive.progeny.com/CPAN/modules/03modlist.data.gz](ftp://archive.progeny.com/CPAN/modules/03modlist.data.gz)
--09:12:29--  [ftp://archive.progeny.com/CPAN/modules/03modlist.data.gz](ftp://archive.progeny.com/CPAN/modules/03modlist.data.gz)
           => `-'
Resolving archive.progeny.com... 216.54.159.98
Connecting to archive.progeny.com|216.54.159.98|:21... failed: Connection refused.

System call "/usr/bin/wget -O - "ftp://archive.progeny.com/CPAN/modules/03modlist.data.gz"  > /home/john/.cpan/sources/modules/03modlist.data"
returned status 1 (wstat 256)
Warning: expected file [/home/john/.cpan/sources/modules/03modlist.data.gz] doesn't exist
Issuing "/usr/bin/ftp -n"
ftp: connect: Connection refused
Not connected.
Local directory now /home/john/.cpan/sources/modules
Not connected.
Not connected.
Not connected.
Not connected.
Not connected.
Bad luck... Still failed!
Can't access URL [ftp://archive.progeny.com/CPAN/modules/03modlist.data.gz](ftp://archive.progeny.com/CPAN/modules/03modlist.data.gz).

Please check, if the URLs I found in your configuration file
([ftp://archive.progeny.com/CPAN/](ftp://archive.progeny.com/CPAN/)) are valid. The urllist can be edited.
E.g. with 'o conf urllist push ftp://myurl/'

Could not fetch modules/03modlist.data.gz
Going to write /home/john/.cpan/Metadata
Warning: Cannot install Bundle::CPAN, don't know what it is.
Try the command

    i /Bundle::CPAN/

to find objects with matching identifiers.


---

### Post by Mortuis on 2007-04-28
Figured, as soon as I ask for help I find the solution.

Apparently you start cpan with:
perl -MCPAN -e shell

When you get to the prompt, you enter:
o conf init

and accept all the default values (and pick a few mirrors) rather than playing with stuff you don't understand.

---

