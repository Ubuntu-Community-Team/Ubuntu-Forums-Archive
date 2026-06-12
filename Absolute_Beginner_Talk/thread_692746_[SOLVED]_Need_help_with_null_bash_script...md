---
title: "[SOLVED] Need help with null bash script.."
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2008-02-10
Hi,

i have:

#!/bin/sh

mv /media/hdd_4/.my\ name/Incoming/* /media/hdd_4/.my\ name/sort/

how can i add  if there is no file in /Incoming/* don't run the mv command...

thanks..

---

### Post by rzrgenesys187 on 2008-02-10
Here is a page with a bunch of commands to find if a file exists [http://www.faqs.org/docs/bashman/bashref_68.html](http://www.faqs.org/docs/bashman/bashref_68.html)

Here is the if statement
```
if [ -e /media/hdd_4/.my\ name/Incoming/* ]; then
mv /media/hdd_4/.my\ name/Incoming/* /media/hdd_4/.my\ name/sort/
fi
```

---

### Post by hopelessone on 2008-02-10
thanks...was looking for that..

---

### Post by ghostdog74 on 2008-02-10
> **hopelessone said:**
> Hi,

i have:

#!/bin/sh

mv /media/hdd_4/.my\ name/Incoming/* /media/hdd_4/.my\ name/sort/

how can i add  if there is no file in /Incoming/* don't run the mv command...

thanks..

you can just pipe to null
```

mv /media/hdd_4/.my\ name/Incoming/* /media/hdd_4/.my\ name/sort/  2>/dev/null

```

---

