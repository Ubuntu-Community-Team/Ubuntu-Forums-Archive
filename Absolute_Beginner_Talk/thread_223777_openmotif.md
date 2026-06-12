---
title: "openmotif??"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by jmilane on 2006-07-26
I need openmotif to run my Citrix client. 

I cannot find it in Synaptic

This is what Citrix says to do... and none of it seems to work for me
[I]

Symptoms

When installing the Citrix ICA Client for Unix 9.x with the .rpm file, installation fails with the following error message:

“Failed Dependency: libXm.so.3 is needed by package ICA Client.”

After installing the ICA Client for Unix 9.x with the .tar.gz file and setupwfc shell script installation succeeds, launching the client doesn’t work and appears non-responsive. Also, launching the client from the command line renders the following error message:

“Error while loading shared libraries: libXm.so.3: cannot open shared object file: no such file or directory.”

Cause

There are several possible causes for this error message:

    * OpenMotif is not installed
    * OpenMotif 2.3.x is installed, which doesn’t have a libXm.so.3, it has a libXm.so.4, libXm.so.4.0.0, libXm.so.x or later
    * A symbolic link named libXm.so.3 to libXm.so.x is not present

Resolution

The commands below may vary depending on the Linux distribution you’re using, the user you’re logged in as, and the version-specific filename of libXm.so.x

The package installer Red Hat Package Manager (RPM) checks for the dependencies of the ICA Client when it’s used to install the ICA Client package. If the libXm.so.3 file is not present, and even if there’s a symbolic link named libXm.so.3, RPM aborts the installation unless it’s instructed to ignore dependencies.

Installing the ICA Client using the .rpm file:

1. Check to see if OpenMotif is installed: rpm –qa |grep openmotif

      a. If OpenMotif is not installed, install OpenMotif for your distribution:

          o For Fedora Core 5, use yum install openmotif.i386
          o For Debain Linux, use emerge openmotif
          o For Gentoo Linux, use emerge openmotif

      b. If OpenMotif is installed, find libXm.so.x

          o To find libXm.so.3, use find / -name libXm* -print and proceed to Step 2

2. Create a symbolic link for libXm.so.x by issuing the following command:
ln –s /usr/lib/libXm.so.4 /usr/lib/libXm.so.3

3. Install the RPM package with the --nodeps option:
rpm -ivh --nodeps ICAClient-x.x-x.i386.rpm

4. Run the ICA Client.

Fixing the installation after installing the ICA Client using the .tar.gz file:

Extracting the tarred and gzipped ICA Client works as expected (tar xzvf linuxx86.tar.gz). The ICA Client setup script setupwfc does not check for files or references that the ICA Client expects to exist.

1. Check to see if OpenMotif is installed: rpm –qa |grep openmotif

      a. If OpenMotif is not installed, install OpenMotif for your distribution:

          o For Fedora Core 5, use yum search openmotif.i386
          o For Debian Linux, use emerge –s openmotif
          o For Gentoo Linux, use emerge –s openmotif

      b. If OpenMotif is installed, find libXm.so.x

          o Use find / -name libXm* -print and proceed to Step 2.

2. Create a symbolic link for libXm.so.x by issuing the following command:
ln –s /usr/lib/libXm.so.x /usr/lib/libXm.so.3

3. Run the ICA Client.

Status

This is a known issue.[/I]

Please help.

---

### Post by Footissimo on 2006-07-26
Look for libmotif3 .. will probably work :)

---

### Post by jmilane on 2006-07-26
But how would I know to do that? Really? I appreciate the help very much. 

Oh my God it worked.

Thank you so much.

But really. How would I know to do that? Im trying to learn Linux and people tend to know the answers... like you... but I want to feel like I might actually learn it one day. How would I know that?

Thank you, very much, again.

---

### Post by Footissimo on 2006-07-26
I've had to find it before myself :)

If you search for 'open motif' in synaptic, it comes up - you still have to give the descriptions (in the last column) a quickie look, but its more sensible than it probably seems at first :)

---

