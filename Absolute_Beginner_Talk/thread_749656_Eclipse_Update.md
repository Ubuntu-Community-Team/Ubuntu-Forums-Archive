---
title: "Eclipse Update"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by nikRbokR on 2008-04-08
Alright... so after weeks of slogging to get Gutsy to install and update correctly on my external drive, I think I've run into a problem that has messed me up :(

I installed Java 6 (JDK and JRE) from the Add/Remove program.  Then, I installed Eclipse from the Add/Remove program as well.  I wanted to update Eclipse so that I could install the Andriod Plugin by Google.  However, as I went to install the Callisto Discovery Site update from the very beginning, it gave me an error:
```
unable to complete action for feature "Eclipse Platform" due to errors
```

Could someone please guide me... I need help.

---

### Post by spiderbatdad on 2008-04-08
I would go back to add/remove and de-select  eclipse.
open synaptic package manager and click the search tool...type in eclipse

select: 
ecj
ecj-gcj
eclipse
eclipse-common-nls
eclipse-gcj
eclipse-jdt
eclipse-jdt-gcj
eclipse-jdt-nls
eclipse-pde
eclipse-pde-gcj
eclipse-pde-nls
eclipse-platform
eclipse-platform-gcj
eclipse-rcp
eclipse-rcp-gcj
libswt3.2-gtk-gcj
libswt3.2-java
libecj-java
libecj-gcj

Installs eclipse under Applications->Programming

---

### Post by nikRbokR on 2008-04-08
Well... Eclipse does show up under Applications --> Programming when I did it from Add/Remove... but I'll try.

---

### Post by nikRbokR on 2008-04-08
ah... I messed it up... I went into Synaptic Manager to install other things that came under eclipse... but im trying to fix it :(

---

### Post by nikRbokR on 2008-04-09
Unfortunately... the problem persists.

Here is the exact error message:
```
Unable to complete action for feature "Eclipse Platform" due to errors.
  Unable to complete action for feature "Eclipse RCP" due to errors.
    Unable to create file "/usr/lib/eclipse/features/org.eclipse.rcp_3.2.2.r322_v20070104-8pcviKVqd8J7C1U/eclipse_update_120.jpg". [/usr/lib/eclipse/features/org.eclipse.rcp_3.2.2.r322_v20070104-8pcviKVqd8J7C1U/eclipse_update_120.jpg (No such file or directory)]
    Unable to create file "/usr/lib/eclipse/features/org.eclipse.rcp_3.2.2.r322_v20070104-8pcviKVqd8J7C1U/eclipse_update_120.jpg". [/usr/lib/eclipse/features/org.eclipse.rcp_3.2.2.r322_v20070104-8pcviKVqd8J7C1U/eclipse_update_120.jpg (No such file or directory)]
  Unable to complete action for feature "Eclipse RCP" due to errors.
    Unable to create file "/usr/lib/eclipse/features/org.eclipse.rcp_3.2.2.r322_v20070104-8pcviKVqd8J7C1U/eclipse_update_120.jpg". [/usr/lib/eclipse/features/org.eclipse.rcp_3.2.2.r322_v20070104-8pcviKVqd8J7C1U/eclipse_update_120.jpg (No such file or directory)]
    Unable to create file "/usr/lib/eclipse/features/org.eclipse.rcp_3.2.2.r322_v20070104-8pcviKVqd8J7C1U/eclipse_update_120.jpg". [/usr/lib/eclipse/features/org.eclipse.rcp_3.2.2.r322_v20070104-8pcviKVqd8J7C1U/eclipse_update_120.jpg (No such file or directory)]
  Unable to create file "/usr/lib/eclipse/features/org.eclipse.rcp_3.2.2.r322_v20070104-8pcviKVqd8J7C1U/eclipse_update_120.jpg". [/usr/lib/eclipse/features/org.eclipse.rcp_3.2.2.r322_v20070104-8pcviKVqd8J7C1U/eclipse_update_120.jpg (No such file or directory)]

```

I think the problem is that it tries to 'usr/lib'.  I guess this is problem.

There are a few screenshots that show the error messages.

Please help me... I really want this to work! :D

---

### Post by conscious on 2008-04-09
Are you sure you're running Eclipse with the administrative privileges? You can't write to /usr unless you are.

---

