---
title: "Applying a patch that is not a file"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by clcaus on 2007-05-22
I am trying to patch a file using a snippet of code I found (this is a fix for the Macbook suspend issue). The code is as follows:

```
---
--- linux-2.6.19.1/drivers/ata/libata-core.c    2006-12-11 20:32:
53.000000000 +0100
+++ linux-2.6.19.1.patched/drivers/ata/libata-core.c    2006-12-27 21:50:
48.000000000 +0100
@@ -5127,7 +5127,7 @@
int ata_host_suspend(struct ata_host *host, pm_message_t mesg)
{
       int i, j, rc;
-
+if(0){
       rc = ata_host_request_pm(host, mesg, 0, ATA_EHI_QUIET, 1);
       if (rc)
               goto fail;
@@ -5151,7 +5151,7 @@
                       }
               }
       }
-
+}
       host->dev->power.power_state = mesg;
       return 0;

---
```

The file I am trying to patch is libata-core.c.

I am unsure how to copy and paste this code into the file. Any suggestions?

---

### Post by nikosapi on 2007-05-22
First cd into the directory linux-2.6.19.1/drivers/ata/ and apply the patch using the patch program like this:
```
patch -p3 < /path/to/file.patch
```

Or you could always do it manually. For the first chunk go to line 5127 and where you see the + sign that means you have to add that specific line there.

So at line 5127 you will see:
```
int ata_host_suspend(struct ata_host *host, pm_message_t mesg)
{
       int i, j, rc;

       rc = ata_host_request_pm(host, mesg, 0, ATA_EHI_QUIET, 1);
       if (rc)
               goto fail;
```

Which should be changed to:
```
int ata_host_suspend(struct ata_host *host, pm_message_t mesg)
{
       int i, j, rc;
if(0){
       rc = ata_host_request_pm(host, mesg, 0, ATA_EHI_QUIET, 1);
       if (rc)
               goto fail;
```

See, you subtracted the empty line and replaced it with "if(0){". Then just do the same for the chunk starting at line 5151.

Hope this helps!

---

### Post by clcaus on 2007-05-23
Worked great. Now unfortunately wifi is broken and when I try and recompile it, I get the following:

```
cd: 1: can't cd to /lib/modules/2.6.20-15-e83-generic/build
Makefile.inc:66: *** /lib/modules/2.6.20-15-e83-generic/build is missing, please set KERNELPATH.  Stop.
```

---

