---
title: "Gutsy upgrade problems"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by arjayes on 2007-10-22
hi i tried to upgrade to gutsy from feisty this morning 
first the update mannager opened and did not detect the upgrade 
I clicked check and after scanning it returned with the upgrade button
I clicked it 
initially a release notes page comes up then it starts downloading the upgrade tool 
two seconds into the download it gets stuck on downloading file 2 of 2 and eventually closes 
I ran it from the terminal so this is what came up.:


$ update-manager -d
extracting '/tmp/tmp_yHtyD/gutsy.tar.gz'
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 914, in on_button_dist_upgrade_clicked
    fetcher.run()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 160, in run
    if not self.extractDistUpgrader():


thank u for taking the time to read this and pls help.
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 99, in extractDistUpgrader
    for tarinfo in tar:
  File "/usr/lib/python2.5/tarfile.py", line 2056, in next
    tarinfo = self.tarfile.next()
  File "/usr/lib/python2.5/tarfile.py", line 1809, in next
    self.fileobj.seek(self.offset)
  File "/usr/lib/python2.5/gzip.py", line 388, in seek
    self.read(1024)
  File "/usr/lib/python2.5/gzip.py", line 227, in read
    self._read(readsize)
  File "/usr/lib/python2.5/gzip.py", line 275, in _read
    self._read_eof()
  File "/usr/lib/python2.5/gzip.py", line 311, in _read_eof
    raise IOError, "CRC check failed"
IOError: CRC check failed
/usr/lib/python2.5/site-packages/UpdateManager/DistUpgradeFetcher.py:83: GtkWarning: gtk_scrolled_window_add: assertion `bin->child == NULL' failed
  self.parent.scrolled_notes.add(textview_release_notes)
extracting '/tmp/tmpqcMARC/gutsy.tar.gz'
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 914, in on_button_dist_upgrade_clicked
    fetcher.run()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 160, in run
    if not self.extractDistUpgrader():
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 99, in extractDistUpgrader
    for tarinfo in tar:
  File "/usr/lib/python2.5/tarfile.py", line 2056, in next
    tarinfo = self.tarfile.next()
  File "/usr/lib/python2.5/tarfile.py", line 1809, in next
    self.fileobj.seek(self.offset)
  File "/usr/lib/python2.5/gzip.py", line 388, in seek
    self.read(1024)
  File "/usr/lib/python2.5/gzip.py", line 227, in read
    self._read(readsize)
  File "/usr/lib/python2.5/gzip.py", line 275, in _read
    self._read_eof()
  File "/usr/lib/python2.5/gzip.py", line 311, in _read_eof
    raise IOError, "CRC check failed"
IOError: CRC check failed

---

