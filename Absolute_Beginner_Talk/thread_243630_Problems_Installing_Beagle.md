---
title: "Problems Installing Beagle"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by chimerical_brio on 2006-08-25
I'm very new to Ubuntu (and Linux in general), and I'm having trouble installing Beagle. I type ```
sudo apt-get install beagle
``` and receive the following error:

Reading package lists... Done
Building dependency tree... Done
Package beagle is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libbeagle0
E: Package beagle has no installation candidate

I have no clue what to do. I enabled Universe in my sources.list file, and tried what Beagle's website says to do for installation, but no luck.

---

### Post by Crosbie on 2006-08-25
If you're new, try the graphic way: 

System > Administration > Synaptic Package Manager.

You'll be able to search for 'beagle' and see what packages are available. :)

---

### Post by chimerical_brio on 2006-08-25
Well, Beagle wasn't there when I checked Synaptic. But, I figured out that I needed to refresh Synaptic's list, and then that package plus a few more I had been looking for were there.

However, it still won't install.

When I try to install it using Synaptic, I am told that other things need to be installed, specifically:

libevolution-cil
libgecko2.0-cil
libgmime2.1
libgmime.2.1-cil

So I click "Mark," and then get the following error message:

"The following packages have unresolvable dependencies," and proceeds to tell me to make sure I have the required dependencies. This is the text of the error:

beagle:
  Depends: libgconf2.0-cil (<2.5.0) but 2.8.2-0ubuntu5 is to be installed
  Depends: libglade2.0-cil (<2.5.0) but 2.8.2-0ubuntu5 is to be installed
  Depends: libglib2.0-cil (<2.5.0) but 2.8.2-0ubuntu5 is to be installed
  Depends: libgnome2.0-cil (<2.5.0) but 2.8.2-0ubuntu5 is to be installed
  Depends: libgtk2.0-cil (<2.5.0) but 2.8.2-0ubuntu5 is to be installed

Similarly, when I try to install with "sudo apt-get install beagle," I get the error:

"Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
beagle: Depends: libgconf2.0-cil (< 2.5.0) but 2.8.2-0ubuntu5 is to be installed
Depends: libglade2.0-cil (< 2.5.0) but 2.8.2-0ubuntu5 is to be installed
Depends: libglib2.0-cil (< 2.5.0) but 2.8.2-0ubuntu5 is to be installed
Depends: libgnome2.0-cil (< 2.5.0) but 2.8.2-0ubuntu5 is to be installed
Depends: libgtk2.0-cil (< 2.5.0) but 2.8.2-0ubuntu5 is to be installed
E: Broken packages"

This happens with other programs' installations as well; any ideas?

---

