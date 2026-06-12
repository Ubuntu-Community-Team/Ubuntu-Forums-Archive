---
title: "synaptic package manager broke"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by jbumgar on 2007-04-06
I was installing Virtual Box.  Realizing I'd forgotten to add a couple of libraries to let it install, I stopped it.  It then gave an error message.  When I went into synaptic to get the libraries I couldn't because it said virtual box needed to install.  When I did get into synamptic there is nothing there but All.  I check to see if the repos were still there and it look like they are.  I used gedit /etc/apt/sources.list and it shows the repos there.  So what do I do to fix it?

---

### Post by dbbolton on 2007-04-07
run ```
sudo aptitude update
``` to update your sources. then try to launch Synaptic. if it still doesn't work, reboot.

---

### Post by Lucifiel on 2007-04-07
Mmmm... maybe you can try reinstalling Virtual Box and let it fail by itself? And then install the libs then? Or you could try running > gksudo aptitude <application name>-remove

Or replace "remove" with "reinstall" .

---

### Post by jbumgar on 2007-04-07
Still no synaptic.   I get this E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.  The pack is in my downloads so it exists.


When I type this in  gksudo aptitude VirtualBox_1.3.6_Ubuntu_edgy_i386.deb -r 

I get this:

  Options:
 -h             This help text
 -s             Simulate actions, but do not actually perform them.
 -d             Only download packages, do not install or remove anything.
 -P             Always prompt for confirmation or actions
 -y             Assume that the answer to simple yes/no questions is 'yes'
 -F format      Specify a format for displaying search results; see the manual
 -O order       Specify how search results should be sorted; see the manual
 -w width       Specify the display width for formatting search results
 -f             Aggressively try to fix broken packages.
 -V             Show which versions of packages are to be installed.
 -D             Show the dependencies of automatically changed packages.
 -Z                 Show the change in installed size of each package.
 -v             Display extra information. (may be supplied multiple times)
 -t [release]   Set the release from which packages should be installed
 -q             In command-line mode, suppress the incremental progress indicators.
 -o key=val     Directly set the configuration option named 'key'
 --with(out)-recommends Specify whether or not to treat recommends as
                strong dependencies
 -S fname: Read the aptitude extended status info from fname.
 -u      : Download new package lists on startup.
 -i      : Perform an install run on startup.

                  This aptitude does not have Super Cow Powers.

So is there anything else to try.  I tried both suggestions.

---

### Post by confused57 on 2007-04-07
I don't think you can remove it with aptitude unless you installed it with aptitude...maybe something like:
```
sudo apt-get remove <package name>
```

or maybe install, reinstall...I'm not sure.

Synaptic uses apt-get, not aptitude to install packages.

---

### Post by jbumgar on 2007-04-07
I'll try that then.  Thanks.

---

