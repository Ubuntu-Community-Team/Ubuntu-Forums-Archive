---
title: "problem removing a program"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by apradhan on 2007-05-31
Hi !

I recently installed the program k3d and had some installation errors. So I tried to remove it using the console.

adu@adu-laptop:~$ sudo apt-get remove k3d
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  k3d
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  k3d
0 upgraded, 0 newly installed, 1 to remove and 85 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 44.5MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 122986 files and directories currently installed.)
Removing k3d ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 932, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing k3d (--remove):
 subprocess pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 865, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 k3d
E: Sub-process /usr/bin/dpkg returned an error code (1)
adu@adu-laptop:~$ 


Could anyone help me with what all this python stuff is about ??? Is there any way i can fix this ?

Thanks a lot

---

### Post by oliviacond on 2007-05-31
have you tried 'apt-get autoremove'?

---

### Post by [VuwB.UC|Cj] on 2007-05-31
'apt-get autoremove' ?? what's that?

---

