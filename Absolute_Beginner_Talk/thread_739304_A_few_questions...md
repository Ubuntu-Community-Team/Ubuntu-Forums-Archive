---
title: "A few questions.."
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-03-29
First, 
Openoffice has released version 2.4 now. When I download the .deb file. I run this..

```
tom@Laptop:~$ cd ~/Desktop/ooo
tom@Laptop:~/Desktop/ooo$ ./update
dpkg: requested operation requires superuser privilege
tom@Laptop:~/Desktop/ooo$ sudo ./update
[sudo] password for tom:
dpkg - warning: downgrading openoffice.org-calc from 1:2.3.0-1ubuntu5.3 to 2.4.0-12.
dpkg: regarding .../openoffice.org-calc_2.4.0-12_i386.deb containing openoffice.org-calc:
 openoffice.org-calc conflicts with openoffice.org-bundled
  openoffice.org-core provides openoffice.org-bundled and is present and installed.
dpkg: error processing ./DEBS/openoffice.org-calc_2.4.0-12_i386.deb (--install):
 conflicting packages - not installing openoffice.org-calc
dpkg - warning: downgrading openoffice.org-writer from 1:2.3.0-1ubuntu5.3 to 2.4.0-12.
dpkg: regarding .../openoffice.org-writer_2.4.0-12_i386.deb containing openoffice.org-writer:
 openoffice.org-writer conflicts with openoffice.org-bundled
  openoffice.org-core provides openoffice.org-bundled and is present and installed.
dpkg: error processing ./DEBS/openoffice.org-writer_2.4.0-12_i386.deb (--install):
 conflicting packages - not installing openoffice.org-writer
Skipping deselected package openoffice.org-graphicfilter.
Skipping deselected package openoffice.org-javafilter.
Skipping deselected package openoffice.org-core01.
Skipping deselected package openoffice.org-core03u.
Skipping deselected package openoffice.org-emailmerge.
dpkg - warning: downgrading openoffice.org-base from 1:2.3.0-1ubuntu5.3 to 2.4.0-12.
dpkg: regarding .../openoffice.org-base_2.4.0-12_i386.deb containing openoffice.org-base:
 openoffice.org-base conflicts with openoffice.org-bundled
  openoffice.org-core provides openoffice.org-bundled and is present and installed.
dpkg: error processing ./DEBS/openoffice.org-base_2.4.0-12_i386.deb (--install):
 conflicting packages - not installing openoffice.org-base
Skipping deselected package openoffice.org-core02.
Skipping deselected package openoffice.org-core05.
Skipping deselected package openoffice.org-headless.
Skipping deselected package openoffice.org-core09.
Skipping deselected package openoffice.org-core07.
Skipping deselected package openoffice.org-pyuno.
Skipping deselected package openoffice.org-core04u.
Skipping deselected package openoffice.org-gnome-integration.
Skipping deselected package openoffice.org-core03.
Skipping deselected package openoffice.org-onlineupdate.
Skipping deselected package openoffice.org-core04.
Skipping deselected package openoffice.org-core10.
Skipping deselected package openoffice.org-core08.
Skipping deselected package openoffice.org-kde-integration.
Skipping deselected package openoffice.org-core06.
dpkg - warning: downgrading openoffice.org-math from 1:2.3.0-1ubuntu5.3 to 2.4.0-12.
dpkg: regarding .../openoffice.org-math_2.4.0-12_i386.deb containing openoffice.org-math:
 openoffice.org-math conflicts with openoffice.org-bundled
  openoffice.org-core provides openoffice.org-bundled and is present and installed.
dpkg: error processing ./DEBS/openoffice.org-math_2.4.0-12_i386.deb (--install):
 conflicting packages - not installing openoffice.org-math
Skipping deselected package openoffice.org-xsltfilter.
dpkg - warning: downgrading openoffice.org-impress from 1:2.3.0-1ubuntu5.3 to 2.4.0-12.
dpkg: regarding .../openoffice.org-impress_2.4.0-12_i386.deb containing openoffice.org-impress:
 openoffice.org-impress conflicts with openoffice.org-bundled
  openoffice.org-core provides openoffice.org-bundled and is present and installed.
dpkg: error processing ./DEBS/openoffice.org-impress_2.4.0-12_i386.deb (--install):
 conflicting packages - not installing openoffice.org-impress
Skipping deselected package openoffice.org-debian-menus.
dpkg - warning: downgrading openoffice.org-draw from 1:2.3.0-1ubuntu5.3 to 2.4.0-12.
dpkg: regarding .../openoffice.org-draw_2.4.0-12_i386.deb containing openoffice.org-draw:
 openoffice.org-draw conflicts with openoffice.org-bundled
  openoffice.org-core provides openoffice.org-bundled and is present and installed.
dpkg: error processing ./DEBS/openoffice.org-draw_2.4.0-12_i386.deb (--install):
 conflicting packages - not installing openoffice.org-draw
Skipping deselected package openoffice.org-core05u.
Skipping deselected package openoffice.org-testtool.
Errors were encountered while processing:
 ./DEBS/openoffice.org-calc_2.4.0-12_i386.deb
 ./DEBS/openoffice.org-writer_2.4.0-12_i386.deb
 ./DEBS/openoffice.org-base_2.4.0-12_i386.deb
 ./DEBS/openoffice.org-math_2.4.0-12_i386.deb
 ./DEBS/openoffice.org-impress_2.4.0-12_i386.deb
 ./DEBS/openoffice.org-draw_2.4.0-12_i386.deb
tom@Laptop:~/Desktop/ooo$ 
```

Do I need to unistall veriosn 2.3?
Would an update come through later on for this instead of doing it manually?



Next question,

When I turn my laptop off at night with the battery fully charged, in the morning, when I turn it back on, my battery life is around 83%
What does Ubuntu do when its off?
It never done it with Vista.


Finally,

I have a HP printer. 
When I plug it in via USB in my laptop, would it automatically work? (I haven't tried yet as i have to get it out)
Does HP support drivers for their printers? 
I have the disk which comes with it, for windows, would that help in any way?



Thanks,
Tom :KS

---

### Post by bren on 2008-03-29
> When I turn my laptop off at night with the battery fully charged, in the morning, when I turn it back on, my battery life is around 83%
What does Ubuntu do when its off?
It never done it with Vista.

most likely this is a battery problem, not an OS problem

if you are sure this doesn't happen in Vista then try removing the battery from the laptop overnight (starting fully charged) and see what is there in the morning


> I have a HP printer.
When I plug it in via USB in my laptop, would it automatically work? (I haven't tried yet as i have to get it out)

hp support is good on linux i understand
search for your model no on this forum if you problems
but just plug it in then go SYSTEM | ADMIN | PRINTING | Add new printer

> 
I have the disk which comes with it, for windows, would that help in any way?

no

---

### Post by Tom--d on 2008-03-29
Thank you for your reply :)

With the battery, It have never noticed it in Vista (doesnt mean that it hasn't happend tho). 
Tonight, I will take it out and give it a try.


Any help on the openoffice situation?

---

### Post by Joeb454 on 2008-03-29
It will come through as an update at some point. I think it's intended to be included in the next Ubuntu release also. :)

---

### Post by Tom--d on 2008-03-29
Ah.
ok, I will wait till then :)

Thanks

---

