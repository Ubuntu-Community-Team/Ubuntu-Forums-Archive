---
title: "SSH help needed"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by Koobi on 2006-02-01
i've used telnet a lot but i've never really used SSH extensively.

the thing is, i'm working on some remote files and i need to duplicate a folder (this folder has files in it as well as folders, which, in turn contain more folders) and all its contents while maintaining it's directory structure.


for an example, if i was just using terminal, i'd do this:
```

cp /path/to/folder /path/to/newFolder

```

what would the SSH equivalent of that look like?

thanks for your time

---

### Post by Gcool on 2006-02-01
For this you can use scp (secure copy).

The command would be something like this:

scp user@source:/directory/file user@destination:/directory/file

If you want to copy complete directory's, just add the -r option ( scp -r ....)

---

### Post by Koobi on 2006-02-01
hey, thanks.
but just to double check, would this work?

```

scp -r user@host:/public_html/original user@host:/public_html/duplicate

```

---

### Post by Gcool on 2006-02-01
Shouldn't be a problem, i think.

---

