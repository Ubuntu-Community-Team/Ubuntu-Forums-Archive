---
title: "Where do I get MS fonts?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by barbecued_ribs on 2007-08-06
How do you get the MS fonts and make them the dafault font in Firefox? A lot of sites don't look good with whatever font is installed.

---

### Post by Kingsley on 2007-08-06
You gotta install msttcorefonts.

---

### Post by Hallvor on 2007-08-06
Type:

> sudo apt-get install msttcorefonts

.. in the terminal.

---

### Post by barbecued_ribs on 2007-08-06
> **Hallvor said:**
> Type:



.. in the terminal.

it says
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate

---

### Post by mcduck on 2007-08-06
> **barbecued_ribs said:**
> it says
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate

HAve you enabled Universe & Multiverse repositories? Go to System/Administration/Software Sources and enable them.

---

### Post by barbecued_ribs on 2007-08-06
> **mcduck said:**
> HAve you enabled Universe & Multiverse repositories? Go to System/Administration/Software Sources and enable them.

there's no software sourrces in administration

---

### Post by Hallvor on 2007-08-06
This one?

[IMG]https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=menu-sw.png[/IMG]

---

