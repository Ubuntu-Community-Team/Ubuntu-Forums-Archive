---
title: "Re: files list file for package 'xxx' is missing final newline"
date: 2012-03-27
forum: Any Other OS
---

### Post by stitch on 2012-03-27
> Ok, i've had this error for several weeks now and have not been able to install ANY updates. Did some searching and couldn't find much info, so decided to check it out myself. The 'missing final newline' was a bit of a giveaway really, so i created a python script to check how many files inside /var/lib/dpkg/info/ were actually missing the final newline character.

I then modified my script to append a newline to the files that were missing it, which fixed my problem. Not sure how these files managed to get corrupted but hey-ho. Is this a satisfactory answer or will i be misleading new users by posting this script???

[PHP]
#!/usr/bin/python


# 8th November, 2009
# update manager failed, giving me the error:
#       'files list file for package 'xxx' is missing final newline' for every package.
# some Googling revealed that this problem was due to corrupt files(s) in /var/lib/dpkg/info/
# looping though those files revealed that some did not have a final new line
# this script will resolve that problem by appending a newline to all files that are missing it
# NOTE: you will need to run this script as root, e.g. sudo python newline_fixer.py

import os

dpkg_path = '/var/lib/dpkg/info/'
paths = os.listdir(dpkg_path)
for path in paths:
    path = dpkg_path + path
    f = open(path, 'a+')
    data = f.read()
    if len(data) > 1 and data[-1:] != '\n':
        f.write('\n')
        print 'added newline character to:', path
    f.close()
[/PHP]

Hi, I know this thread is very old, but I recently had the same problem with Linux Mint, and I wish to thank you for this rapid solution.
You saved me :)

Thanks Again

stitch

---

### Post by Perfect Storm on 2012-03-28
Moved to Other OS/Distro Talk.

---

