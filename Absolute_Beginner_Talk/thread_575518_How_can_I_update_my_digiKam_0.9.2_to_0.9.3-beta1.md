---
title: "How can I update my digiKam 0.9.2 to 0.9.3-beta1?"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Mr. Johnson on 2007-10-14
How can I update my digiKam with full of photos from 0.9.2 to 0.9.3-beta1?

And also when the revamped digiKam comes out, will I be able to update too and keep my photos in the same place?

Cheers :KS

---

### Post by ramjet_1953 on 2007-10-14
As this is not in the repos, you will need to download the tarball and then extract it.

You will need to have downloaded the build-essential package before compiling.

[COLOR="Red"]sudo apt-get install build-essential[/COLOR]

You will also need to manually satisfy dependencies, which can involve downloading quite a few extra packages and the associated .dev packages, also before you compile.

Once all of this is done satisfactorily, you will need to complete the following steps.

1. Open a terminal and change to the directory where you extracted the tarball.

2. type this command in[COLOR="Red"]./configure[/COLOR]

3. If it completes successfully, type this command in [COLOR="Red"]make[/COLOR]

4. If this completes successfully, type this in [COLOR="Red"]sudo make install[/COLOR]

5. If this also completes successfully, you can now run the application.

If any of the above steps fail, you almost certainly have not met dependencies. Look at the error outputs for clues.

As you can see, not something for the inexperienced.
If this is overwhelming for you, I suggest that you wait until a deb is released for Ubuntu.

Regards,
Roger :cool:

---

### Post by jure1873 on 2007-12-29
I've installed the latest digikam with a little help from prevo.
I used prevo to create debs to install libkdcraw and libkexiv2, then I downloaded the source for 0.9.3 from digikam's website and used checkinstall to create a deb package, because the one in ubuntu 8.04 is 0.9.3-rc1 and I preferred to install the stable release.

aptitude install prevu
prevu libkdcraw
prevu libkexiv2
dpkg  --force-depends --remove libkdcraw1
dpkg  --force-depends --remove libkexiv2
tar xvfj digikam-0.9.3.tar.bz2
cd digikam
./configure && make && checkinstall -D

--- 
The problem is that when I try to do a dist-upgrade I get this:

The following packages are BROKEN:
  libkexiv2-3
The following NEW packages will be automatically installed:
  kipi-plugins libkdcraw1 libkexiv2-1 sane-utils
The following NEW packages will be installed:
  kipi-plugins libkdcraw1 libkexiv2-1 sane-utils
The following packages will be upgraded:
  digikam
1 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 2063kB/9511kB of archives. After unpacking 8466kB will be used.
The following packages have unmet dependencies:
  libkexiv2-3: Conflicts: libkexiv2-1 but 0.1.5-1ubuntu2 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
libkexiv2-3
libkexiv2-dev

---

### Post by gwi on 2008-01-23
There is a digikam repository for (K)Ubuntu, maintained by Achim Bohnet at [http://www.mpe.mpg.de/~ach/kubuntu/]("http://www.mpe.mpg.de/~ach/kubuntu/").
Instructions can be found at [http://www.digikam.org/?q=download/binary/]("http://www.digikam.org/?q=download/binary/").

The 0.9.3 final release is out, but it is not yet in the repository, 0.9.3 beta2 is the latest.

Achim, if you are reading this: when do you expect to have a package for 0.9.3 in your repository?

---

