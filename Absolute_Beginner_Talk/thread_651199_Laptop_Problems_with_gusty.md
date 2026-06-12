---
title: "Laptop Problems with gusty"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by deepank on 2007-12-27
Hi,

Some issues that are there with my newly installed Gusty Gibbon on my Dell Inspiron 6400 laptop are : 

1. No splash screen is shown while booting up and my screen goes black for about 30 seconds and then my login screen comes up. 

2. I cannot hibernate the laptop. Whenever I click on hibernate screen goes blank and remains as it is till I manually power down the laptop.

---

### Post by jan quark on 2007-12-27
Having the same issue on my Dell Inspiron 1501.
Its not that crucial but perhaps can someone fix this?

---

### Post by deepank on 2007-12-27
So are there no solutions up till now for this. I was under the impression that Dell supported Ubuntu these days. :(

---

### Post by spiderbatdad on 2007-12-27
i have seen these issue covered and solved numerous times in other posts. You need to do some searching.

---

### Post by mikecomua on 2007-12-27
That's weird... If the 6400 is the e1405, and that is my model, than that is INCREDIBLY weird. Almost everything works like a charm on my system

---

### Post by deepank on 2007-12-27
@spiderbatdad
Will you be kind enough to point me to those posts

---

### Post by eolson on 2007-12-27
do a search on
   Laptop sleep
   Laptop hibernate

also check out the Dell support forum and the Hardware and Laptop forum\

There are a ton of posts  way too many to link to.

---

### Post by TWO on 2007-12-27
> **deepank said:**
> Hi,

Some issues that are there with my newly installed Gusty Gibbon on my Dell Inspiron 6400 laptop are : 

1. No splash screen is shown while booting up and my screen goes black for about 30 seconds and then my login screen comes up. 

2. I cannot hibernate the laptop. Whenever I click on hibernate screen goes blank and remains as it is till I manually power down the laptop.

1)I was told that the lack of splash screen was a feature of Ubuntu Gutsy in order to speed up the start up process. Not sure how much of a difference this makes. Anyway, I asked on another forum and this was the advice I received:

To enable the splash screen, do the following.
Press Alt-F2 and type "gconf-editor" (without the quotes).

Navigate to /apps/gnome-session/options.

Check the box next to the value "show_splash_screen"

As I was advised by the person who told me, be careful when using that editor, as you can mess things up quite easily.
Even with the splash screen, your screen will go blank before it. I'm not sure how healthy it is but it seems to be the case for a lot of people.

2)As far as hibernate goes, I heard that there can be problems with it on Ubuntu. Anyway, do you have a  Swap drive? I may be wrong but I assume that you can't hibernate without one...
I have a Dell too with a spec not worth mentioning without a Swap drive so I can't Hibernate either.

---

### Post by spiderbatdad on 2007-12-27
[http://ubuntuforums.org/showthread.php?t=417964&page=2](http://ubuntuforums.org/showthread.php?t=417964&page=2)

[http://ubuntuforums.org/showthread.php?t=471855&highlight=dell+hibernate](http://ubuntuforums.org/showthread.php?t=471855&highlight=dell+hibernate)

[http://ubuntuforums.org/showthread.php?t=579781&highlight=dell+hibernate](http://ubuntuforums.org/showthread.php?t=579781&highlight=dell+hibernate)



Have you tried changing POST-VIDEO to "False" in /etc/default/acpi-support?

---

