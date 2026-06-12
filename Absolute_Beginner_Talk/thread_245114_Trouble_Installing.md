---
title: "Trouble Installing"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by chimerical_brio on 2006-08-27
I am having trouble installing two programs: Beagle and Banshee. I kind of suspect that this problem is more widespread than just affecting these two programs, but I haven't checked.

When I try to install Beagle with both apt-get in the terminal or with Synaptic, I receive the following message:

"The following packages have unmet dependencies:
beagle: Depends: libgconf2.0-cil (< 2.5.0) but 2.8.2-0ubuntu5 is to be installed
Depends: libglade2.0-cil (< 2.5.0) but 2.8.2-0ubuntu5 is to be installed
Depends: libglib2.0-cil (< 2.5.0) but 2.8.2-0ubuntu5 is to be installed
Depends: libgnome2.0-cil (< 2.5.0) but 2.8.2-0ubuntu5 is to be installed
Depends: libgtk2.0-cil (< 2.5.0) but 2.8.2-0ubuntu5 is to be installed"

When I receive it in Synaptic, it's preceded by the message that some other packages need to be installed (libevolution-cil, libgecko2.0-cil, libgmime2.1, and libgmime2.1-cil). This happens as soon as I mark Beagle for installation. However, when I try to mark these extra changes, I receive the above error message.

It's a similar situation with Banshee, but with a few different packages. Any ideas? Thanks.

---

### Post by sbassett on 2006-08-27
Do you have your multiverse and universe sources activated?

---

### Post by chimerical_brio on 2006-08-27
That was exactly what I needed to do. Thanks a lot!

---

