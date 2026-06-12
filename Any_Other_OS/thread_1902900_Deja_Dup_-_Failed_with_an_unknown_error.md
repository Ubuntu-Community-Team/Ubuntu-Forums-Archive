---
title: "Deja Dup - Failed with an unknown error"
date: 2012-01-01
forum: Any Other OS
---

### Post by GisliKarl on 2012-01-01
Everytime I try to take a backup the program returns me with this error message. Does anyone have any idea how to fix it? (I'm running Linux Mint 11 which is based on Ubuntu 11.04).

> Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1265, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1258, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1231, in main
    full_backup(col_stats)
  File "/usr/bin/duplicity", line 411, in full_backup
    sig_outfp = get_sig_fileobj("full-sig")
  File "/usr/bin/duplicity", line 392, in get_sig_fileobj
    remote_sig_filename)
  File "/usr/lib/python2.7/dist-packages/duplicity/dup_temp.py", line 71, in get_fileobj_duppath
    td = tempdir.TemporaryDirectory(dirpath.name)
  File "/usr/lib/python2.7/dist-packages/duplicity/tempdir.py", line 116, in __init__
    self.__dir = tempfile.mkdtemp("-tempdir", "duplicity-", temproot)
  File "/usr/lib/python2.7/tempfile.py", line 318, in mkdtemp
    _os.mkdir(file, 0700)
OSError: [Errno 13] Permission denied: '/home/gislikarl/.cache/deja-dup/c88b32aa4c5f9fad6a650b40c9dd4dc2/duplicity-68qOWe-tempdir'

---

### Post by Perfect Storm on 2012-01-01
Moved to Other OS/Distro Talk.

---

### Post by GisliKarl on 2012-01-13
I managed to fix this problem simply by going into the settings and changing the name of the folder to store the backups to. Then you can either move your existing backup files or create a new backup from scratch.

---

