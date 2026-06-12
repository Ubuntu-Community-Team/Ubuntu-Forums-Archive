---
title: "Problem with alien tool"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by bikram on 2007-09-27
Hi,

I am trying to convert a .rpm to .deb. I learnt I needed alien. I got it installed. But when I say "alien -myfile.rpm" it gives me the following error:
 Error executing "LANG=C rpm -qp --queryformat %{SUMMARY} myfile.rpm": at /usr/local/share/perl/5.8.8/Alien/Package.pm line 482

I tried other options with alien but nothing seems to work. Any help would be greatly appreciated.

Thanks.
Bikram

---

### Post by overdrank on 2007-09-27
> **bikram said:**
> Hi,

I am trying to convert a .rpm to .deb. I learnt I needed alien. I got it installed. But when I say "alien -myfile.rpm" it gives me the following error:
 Error executing "LANG=C rpm -qp --queryformat %{SUMMARY} myfile.rpm": at /usr/local/share/perl/5.8.8/Alien/Package.pm line 482

I tried other options with alien but nothing seems to work. Any help would be greatly appreciated.

Thanks.
Bikram

Hi if  you could tell us what you are trying to install we might can help and maybe find a deb file.

---

### Post by stchman on 2007-09-27
> **bikram said:**
> Hi,

I am trying to convert a .rpm to .deb. I learnt I needed alien. I got it installed. But when I say "alien -myfile.rpm" it gives me the following error:
 Error executing "LANG=C rpm -qp --queryformat %{SUMMARY} myfile.rpm": at /usr/local/share/perl/5.8.8/Alien/Package.pm line 482

I tried other options with alien but nothing seems to work. Any help would be greatly appreciated.

Thanks.
Bikram

You must use sudo.

To convert a .rpm to a .deb use the following command:

```
sudo alien --scripts --keep-version -d myfile.rpm
```

---

### Post by bikram on 2007-09-28
HI,

 Thanks for your reply. Actually I have used sudo. I'll try again and i'll reply back.  And do I need any other package to be installed to use Alien?

Regards,
 Bikram

---

### Post by forestpixie on 2007-09-28
not as far as i know, it should be just alien

---

