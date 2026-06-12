---
title: "Unable to change permissions"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by mediax on 2006-08-29
I am trying to change permissions on 4 files to allow read access to all users (the files are going to be uploaded to my website).

In Nautilus, I highlight the files, select File, select Properties and click on the Permissions tab - all seems fine so far.  However, when I click the Read boxes for Group and Other, a tick appears, but almost immediately disappears. The changes are not saved.  I am the owner of the files, so what am I doing wrong? :confused:

I'm a newbie to Linux, but am rapidly faling in love with Ubuntu.  I spent long enough using DOS for problems like this to be fun ;)

---

### Post by taurus on 2006-08-29
It's better to do all that from a command line, Applications -> Accessories -> Terminal.  

```

ls -la <filename>

```
Otherwise, run

```

chmod 755 <filename>

```

---

### Post by Bachstelze on 2006-08-29
If you re not the owner of the files, you'll have to do it as root from a command line :

```
sudo chmod 644 filename
```

---

### Post by mediax on 2006-08-30
Thanks for the pointers.

I think part of the problem might be that the files were created from a Windows application and/or stored on a usb datastick?

Ubuntu shows me as the file owner and my group as the group, but with a little experimentation I found that I could change the owner permissions on the original files, but not those for group or others.

In the end, I uploaded the files to my website and used the chmod facility in my ftp program.  Worked like a charm!

Thanks again for the help.

---

