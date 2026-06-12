---
title: "Error in Synaptic: libwxgtk2.6 not installable!!"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by Jax Kovak on 2006-07-24
Hi,

I'm trying to install amule from synaptic, but when I select it and try to install it gives me the following message and then cant/wont install anything:

> amule:
 Depends: libwxgtk2.6  but it is not installable
 Recommends: amule-utils but it is not going to be installed

Can anyone tell me how to fix this please? Iv tried using this:

```
apt-get update && apt-get install amule
```

...which was suggested on the amule web site, but this finishes with the following:

> Errors were encountered while processing:
 /var/cache/apt/archives/libwxbase2.6_2.6.3-2_i386.deb
 /var/cache/apt/archives/libwxgtk2.6_2.6.3-2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Subsequently trying to run amule then gives me the following error message:

```
amule: /usr/lib/libwx_gtk2u_core-2.6.so.0: version `WXU_2.6.2' not found (required by amule)
amule: /usr/lib/libwx_gtk2u_core-2.6.so.0: version `WXU_2.6.3' not found (required by amule)
```

Iv now tried removing amule with synaptic (Which says there are broken packages) but still nothing seems to work.

Any help please.

Thanks

Jax

---

### Post by Metacarpal on 2006-07-24
Hi

I ran into the same problem while installing AMule once.  Here's how I fixed it:

In your System menu, go to Administration > Synaptic Package Manager.  Search for libwxgtk2.6

Then click the box next to it.  If the box was white, mark it for installation.  If the box was grey, mark it for re-installation.

Then search up libwxgtk2.6 and mark it for (re)installation.  Then click Apply, and wait for the install process to complete.  You should be able to install AMule afterward.

---

### Post by Jax Kovak on 2006-07-24
Thanks Metacarpal, but that package is marked as "Not Installed (locked)"

I have no idea how to unlock it!

---

