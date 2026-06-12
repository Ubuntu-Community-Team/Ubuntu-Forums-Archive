---
title: "Cron and SVN"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by externalsupport on 2007-01-03
Hi all,

I have a cron job that is set to run every 15 minutes that is supposed to run the svn update command so I can keep out website source and hosting directories in sync. The cron job is running but for some reason svn update isn't happening. 

Here is the contents of cron job

30 * * * * export DISPLAY=:0 && /usr/bin/upload_sync

and the contents of svn_update

#!/bin/bash
svn update --username scassidy --password password /var/www/internet/upload_area/


if I run svn_update everyhing works perfectly but from cron it does not update. If I pipe the output to a file like this 

30 * * * * export DISPLAY=:0 && /usr/bin/upload_sync > ~/upload_sync_output.txt

then the file is created so I know that cron is doing as it should but svn update does now happen. 

Does anyone have any idea why this is happening?

Thanks

Ste

---

### Post by chluehr on 2008-06-24
Yes.

In my case, it was due to a charset conversion error.
Try appending  ```
2>/tmp/cron_err
``` to the svn call and you'll see the error.
I was able to solve it by setting some locale environment variables:

```
export LANG=de_DE.UTF-8
export LC_CTYPE=de_DE.UTF-8
export LC_ALL=
```

Your mileage may vary.

Kind regards, Chris

---

