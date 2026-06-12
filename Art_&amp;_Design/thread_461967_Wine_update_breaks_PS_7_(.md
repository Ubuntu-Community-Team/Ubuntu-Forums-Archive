---
title: "Wine update breaks PS 7 :("
date: 2007-06-02
forum: Art &amp; Design
---

### Post by mech7 on 2007-06-02
Anybody have the same? with me it cant load fonts anymore and the close buttons does not work anymore :(

---

### Post by hikaricore on 2007-06-03
You could downgrade if needed.

But before you do, try running:

```
wineprefixcreate
```

From a terminal, then when it's finished try running photoshop again and see if it made any difference.

It may or may not help, sometimes it fixes odd little issues after an upgrade.

from the **wineprefixcreate** man page
> WINEPREFIXCREATE(1)                                                  Windows on Unix                                                  WINEPREFIXCREATE(1)

NAME
       wineprefixcreate - create or update the Wine configuration

SYNOPSIS
       wineprefixcreate [options]

DESCRIPTION
       wineprefixcreate  creates or updates a Wine configuration directory.  When running Wine, the base name of the configuration directory is specified
       in the WINEPREFIX variable, hence the name of this tool.

       wineprefixcreate is launched automatically by wine(1) if you don&#8217;t have an existing configuration. However, it can sometimes be useful to  run  it
       explicitly to create a different directory, or update an existing one.


---

