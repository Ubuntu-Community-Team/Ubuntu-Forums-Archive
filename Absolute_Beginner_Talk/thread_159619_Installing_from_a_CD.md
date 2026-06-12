---
title: "Installing from a CD"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by Bhante Santi on 2006-04-13
I am trying to install CBeta Chinese Tripitaka reader from CD. It is Linux compatible according to the makers. I eventually found the button to get synaptic to look for the setup.exe on the CD but it gives this error message:

"Unable to locate any package files. perhaps this is not a Debian disc"

It's not a Debian disc, but it's supposed to be Linux compatible according to the packaging.

What can I do?

Bhante Santi.

---

### Post by Ferri on 2006-04-13
Perhaps there's some "linux" folder on the CD or some compressed package.
If so, probably it won't be a Debian package and fou'll have to do something like "./configure && make && sudo make install" from the command line.
You should also look for some help in the documentation included with the disk (it may be a file inside the CD like "readme" or something like that).

---

