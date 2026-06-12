---
title: "libxml problems"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by Obor on 2006-03-28
Firstly, I'm very new to linux

Yesterday my gmail notifier stopped working...since then I found that it wasn't just me but everyone else as well [URL="http://www.ubuntuforums.org/showthread.php?t=151178"]Link to thread
[/URL]

Anyway, while I was playing around with different mail notify apps I managed to break something while installing following:

sudo perl -MCPAN -e 'install Bundle::LWP'
sudo perl -MCPAN -e 'install Crypt::Simple'
sudo perl -MCPAN -e 'install XML::Simple'
sudo perl -MCPAN -e 'install Crypt::SSLeay'

all of them seem to go through fine except for XML.
[B]
now when I try reinstall in synaptic:[/B]
libxml-sax-perl
libxml-libxml-perl
libxml-simple-perl
[B]
I get the following error:[/B]
E: libxml-sax-perl: subprocess post-installation script returned error exit status 255
E: libxml-libxml-perl: dependency problems - leaving unconfigured
E: libxml-sax-expat-perl: dependency problems - leaving unconfigured
E: libxml-simple-perl: dependency problems - leaving unconfigured
[B]
if I try install libxml-sax-perl from the terminal i get the following[/B] 
Reading package lists... Done
Building dependency tree... Done
libxml-sax-perl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up libxml-sax-perl (0.12-5) ...
Can't locate object method "save_parsers_debian" via package "XML::SAX" at /usr/bin/update-perl-sax-parsers line 90.
dpkg: error processing libxml-sax-perl (--configure):
 subprocess post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of libxml-libxml-perl:
 libxml-libxml-perl depends on libxml-sax-perl (>= 0.11); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-libxml-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-sax-expat-perl:
 libxml-sax-expat-perl depends on libxml-sax-perl (>= 0.03); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-sax-expat-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-simple-perl:
 libxml-simple-perl depends on libxml-sax-perl; however:
  Package libxml-sax-perl is not configured yet.
 libxml-simple-perl depends on libxml-libxml-perl | libxml-sax-expat-perl; however:
  Package libxml-libxml-perl is not configured yet.
  Package libxml-sax-expat-perl is not configured yet.
dpkg: error processing libxml-simple-perl (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxml-sax-perl
 libxml-libxml-perl
 libxml-sax-expat-perl
 libxml-simple-perl
E: Sub-process /usr/bin/dpkg returned an error code (1)

**I want to install some applications that depend on these libs so i'm bit stuck. How can i fix this?** ](*,)

---

### Post by Pragmatist on 2006-03-29
Instead of reinstalling the library package, have you tried using synaptic and choosing 'completely remove' and once that is done, then just install the library package?

One difference in this approach is that when you reinstall, it is not removing everything before reinstalling. So if you manually 'completely remove' the packages in question, and then install them, it might fix your problem.

---

### Post by danielk23 on 2006-07-26
I had the same problem and solved it like this:

[LIST]
[*] I first looked where I had XML::SAX installed by using "locate SAX.pm"
[*] I found that I had two versions installed:
[LIST]
[*] one under /usr/lib/perl5/...
[*] one under /usr/local/...
[/LIST]
[*] I looked into boh files for the string "save_parsers_debian":
[LIST]
[*] only the /usr/lib/perl5 file had it
[/LIST]
[*] I removed the SAX files from /usr/local/...
[*] I reran the installation: "apt-get install"
[*] Everything works now!
[/LIST]

daniel.

---

### Post by SepheeBear on 2007-04-28
This worked for me:

sudo rm /usr/local/share/perl/5.8.8/XML/SAX.pm

Dont know what else it breaks anybody know a more elegant way to uninstall CPAN mods?

---

### Post by khughitt on 2007-06-02
Worked for me as well, even though none of the files I found has the method. Anyone know what the cause of this is? I have installed stuff with cpan before, so maybe the version available from cpan conflicts with that used by applications available from the aptitude repositories?

---

### Post by ambient_sky on 2007-11-06
Thanks for post, method works on Debian Etch too.

---

### Post by mr_e_uss on 2007-11-16
This sounds like just what I need -- but (for some reason) I have quite a few SAX.pm (only one of which has the save_parsers_debian method -- see below).  Can I remove all of them except /usr/share/perl5/XML/SAX.pm?  

Thanks in advance!

$ for i in `locate SAX.pm`
> do
> echo $i
> grep "save_parsers_debian" $i
> echo "---"
> done
/root/.cpan/build/XML-SAX-0.16/SAX.pm
---
/root/.cpan/build/XML-SAX-0.16/blib/lib/XML/SAX.pm
---
/root/.cpan/build/XML-LibXML-1.65/lib/XML/LibXML/SAX.pm
---
/root/.cpan/build/XML-LibXML-1.65/blib/lib/XML/LibXML/SAX.pm
---
/home/eu/Downloads/XML-SAX-0.16/SAX.pm
---
/home/eu/Downloads/XML-SAX-0.16/blib/lib/XML/SAX.pm
---
/home/eu/.cpan/build/XML-SAX-0.16/SAX.pm
---
/home/eu/.cpan/build/XML-SAX-0.16/blib/lib/XML/SAX.pm
---
/home/eu/.cpan/build/XML-LibXML-1.65/lib/XML/LibXML/SAX.pm
---
/home/eu/.cpan/build/XML-LibXML-1.65/blib/lib/XML/LibXML/SAX.pm
---
/usr/lib/perl5/XML/LibXML/SAX.pm
---
/usr/local/lib/perl/5.8.8/XML/LibXML/SAX.pm
---
/usr/local/share/perl/5.8.8/XML/SAX.pm
---
/usr/share/perl5/XML/SAX.pm
sub save_parsers_debian {
---
$

---

### Post by coherence on 2007-12-11
> **danielk23 said:**
> I had the same problem and solved it like this:

[LIST]
[*] I first looked where I had XML::SAX installed by using "locate SAX.pm"
[*] I found that I had two versions installed:
[LIST]
[*] one under /usr/lib/perl5/...
[*] one under /usr/local/...
[/LIST]
[*] I looked into boh files for the string "save_parsers_debian":
[LIST]
[*] only the /usr/lib/perl5 file had it
[/LIST]
[*] I removed the SAX files from /usr/local/...
[*] I reran the installation: "apt-get install"
[*] Everything works now!
[/LIST]

daniel.


Great stuff, this worked for me under Etch 4.1.
Interestingly enough, this occurred on a completely fresh install on new server-class hardware. Not sure what I did wrong in the install process to get this to happen!
Thanks Daniel. :)

---

### Post by matthewboh on 2008-04-17
Thanks!

Regrettably, I had started deleting XML.pm files before I read your post, found the good one at [http://www.koders.com/perl/fid7C6E47D06A244E502EE4FBAE9442590000DD6049.aspx?s=parse#L18](http://www.koders.com/perl/fid7C6E47D06A244E502EE4FBAE9442590000DD6049.aspx?s=parse#L18) , downloaded the file, saved a copy with another name - just in case, reran cpan to load XML::LibXML and it all now works.

Thanks!

---

