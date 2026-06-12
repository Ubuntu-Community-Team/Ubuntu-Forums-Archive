---
title: "Need help installing NMS please"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by jmendez2 on 2007-04-25
Hi everyone,
I am completely new to Ubuntu and so far so good, it has helped me with my daily things.
I am however having quite some difficulty installing a network management system, this one in particular;
 
[http://www.opennms.org/documentation/installguide.html](http://www.opennms.org/documentation/installguide.html)

The first problem:  Every time I try to install the Java SDK, I get an error saying

This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    j2sdk-1_4_2-doc.zip j2sdk-1_4_0-doc-ja.zip j2sdk-1_4_2-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.4.2/download.html](http://java.sun.com/j2se/1.4.2/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.

What should I do to finish this first problem?

Any help is greatly appreciated.  Thank you.

---

### Post by stump138 on 2007-04-25
I would try to install the java sdk via synaptic or terminal first.  The downloads I see are .rpm's which means that you'd have to convert with alien first (which can sometimes be flaky).

```
sudo aptitude update && sudo aptitude install j2sdk1.4
```

I'd start there :)

---

### Post by stump138 on 2007-04-25
Taking another look at the packages OpenNMS requires, it appears that they are all available via synaptic.  Tyr searching out the packages there and install from GUI or terminal as you like :)

---

### Post by jmendez2 on 2007-04-27
Sweet, I will begin work on it and let you know what happens.  Thanks guys.

---

### Post by jmendez2 on 2007-05-03
ok, I ran synaptic to install the sdk but during the installation it gave me an erro:

  j2sdk-1_4_2-doc.zip   j2sdk-1_4_0-doc-ja.zip   j2sdk-1_4_2-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit
     [http://java.sun.com/j2se/1.4.2/download.html](http://java.sun.com/j2se/1.4.2/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.

I went to the site and for linux OS, ther are two options to download, a rpm.bin version and a .bin version.  I download the .bin version.

what do I need to do for root.root to own this file once downloaded.

Thanks for the help guys.

---

### Post by jmendez2 on 2007-05-03
one more question.  When installing these programs do I need to install them on my computer or connect to the server that will house the NMS and install them there?

:confused:

---

