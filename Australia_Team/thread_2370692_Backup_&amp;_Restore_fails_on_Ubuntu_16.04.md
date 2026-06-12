---
title: "Backup &amp; Restore fails on Ubuntu 16.04"
date: 2017-09-06
forum: Australia Team
---

### Post by jacko777 on 2017-09-06
I am running Ubuntu 16.04 with the built in Deja-Dup program.  I have had this running now for almost a year, doing daily backups to an external HDD.
Now I have hit a wall, I have a few programs not working properly, so I Googled help and tried, unsucessfuly, to repair the faults.
So, I thought I will do a restore and cure the problems that way.  I have noticed that due to errors, the backup hasn't been run for the last 30 days.
I will paste the errors found on restore and hope someone out there knows a lot more than I do, which is basically nothing.

Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1532, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1526, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1380, in main
    do_backup(action)
  File "/usr/bin/duplicity", line 1405, in do_backup
    globals.archive_dir).set_values()
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 710, in set_values
    self.get_backup_chains(partials + backend_filename_list)
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 835, in get_backup_chains
    add_to_sets(f)
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 823, in add_to_sets
    if set.add_filename(filename):
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 105, in add_filename
    (self.volume_name_dict, filename)
AssertionError: ({1: 'duplicity-inc.20170805T231519Z.to.20170806T230615Z.vol1.difftar.gz'}, 'duplicity-inc.20170805T231519Z.to.20170806T230615Z.vol1.difftar')

A thing I noticed, looking for directory usr/bin/duplicity.  that it is not listed as a folder in /bin...... Must mean something, but what and how doI repair the machine.

Regards,

Rod

---

