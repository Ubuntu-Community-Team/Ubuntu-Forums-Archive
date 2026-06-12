---
title: "problems with compiling"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by Ouzelum on 2006-05-07
I recently set up a Lombard Powerbook with Ubuntu and have been enjoying it quite a bit.  I'm lost when it comes to Linux, but I'm not terribly intimidated of the command line.  I'm trying to install the most recent version of RhythmBox from the source code, and from what I've read (including the install readme) this is accomplished by typing "./configure" and then "sudo make install."  But when using the make command I get the message "No rule to make target 'install'. Stop."
I'm fairly certain I have correctly installed build-essential stuff correctly through Synaptic Package Manager, but would this have to do with that?
Any help would be great, as I'd love to access the shared music on my Quad from this Powerbook.
thanks,
Josh

---

### Post by moberry on 2006-05-07
Did configure finish without any errors? That is a common reason for makefiles not being generated correctly. Also make sure you are in the top level directory for the program. e.g. rythymbox-x.xx/

---

### Post by Ouzelum on 2006-05-07
this is the output:
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific protions of Makefiles... no
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

is the last one the culprit?  is that something I can easily remedy?

---

### Post by ComplexNumber on 2006-05-07
[quote=Ouzelum]this is the output:
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific protions of Makefiles... no
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

is the last one the culprit?  is that something I can easily remedy?[/quote] you need    perl-XML-Parser. look for it in the repositories. one of the things i do when i start a fresh installation is that i install all the perl and python package available. the reason why is that there are so many of them that depend on other perl packages and there are tons and tons of packages that have perl dependencies. you may find that you can't install perl-xml-parser until another perl package is installed. and that perl package depends upon another perl package,........

---

### Post by Omnios on 2006-05-07
Here hope this helps a bit
[http://ubuntuforums.org/showthread.php?t=171822]("http://ubuntuforums.org/showthread.php?t=171822")

 As for compiling errors. The errors are usually your answer to yoru problem. For example you got this error
```
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
```
 From this error you need a XML parser "parser perl modual so now can go to synaptic and find yourself a XML parser aka  parser perl modual. WHich will probably have xml in the description. Also sometimes you need the dev packages of something to compile so if you get an error that states you need something you already have it may require the deb package.

---

