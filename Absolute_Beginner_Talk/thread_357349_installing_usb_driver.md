---
title: "installing usb driver"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by tribeone on 2007-02-09
How do I do this ( in bold section Debain)
The Linux distribution is an RPM file built on Redhat 9 and can be used as is on RPM based distributions: rpm -U file.rpm. **On Debian use alien to convert it and then dpkg to install.** On Gentoo emerge rpm and lib-compat, and then rpm -U file.rpm

I am trying to load a usb driver for a cell phone usb data cable

---

### Post by crispy_420 on 2007-02-09
Just a tip to help you:

Could you mention specific hardware to get others to help you? 

This seems a little vague, let people know what you have so they can help you.

But as far as commands on converting rpm to deb:

Say you downloaded to a folder in home, let's call it home -> rpms

> cd /home/rpms

Now that you are in the same directory as the rpm you want to convert, we can use alien to convert rpm to deb. I'll call the rpm test.rpm as an example. You'll need to use sudo here.

> sudo alien test.rpm

After a minute you'll have a deb file from your rpm, is that what you were looking for?

---

### Post by tribeone on 2007-02-09
Ok I got ya. I have a lg vx9900 I have dwn loaded bitpim to my desktop. I already have installed alien. When I try to convert the rpm I get this:
By the way I am working with ubuntu I believe is debain

```
:~$ sudo alien -d bitpim*.rpm File "bitpim*.rpm" not found.
```

---

### Post by crispy_420 on 2007-02-10
> cd /home/"username"/desktop

sudo alien bitpim-0.9.10-0.i386.rpm                           (latest at there site)

are you sure you are in the right directory

---

