---
title: "Kernel Panic after ndiswrapper install"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by Doc.Caliban on 2007-06-02
Hi there,

While I was waiting around for the known-working wifi drivers to download so I could install them via ndiswrapper, I thought I'd get cute and try using the latest drivers... just to see what would happen.  :-)

Now I get an error that looks something like this:

"Bug scheduling while atomic" and something like "swapper"

That goes on and on until I get a kernel panic.  This is all right after it says that it's getting the network interfaces loaded.

What I'd done is added the IPW2200 driver to the /etc/modprobe.d/blacklist and ran "ndiswrapper -m" as per the instructional page I was reading.  I'd think this will be easy to clean up if I only knew how to get to a working prompt to do so.  I'm booted into the live cd for now.  (gotta love that!)

-Doc

---

