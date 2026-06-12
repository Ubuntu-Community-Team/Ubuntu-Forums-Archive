---
title: "Ubuntu depositaries seem to be more outdated than debian depositories"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-08-05
Some applications like HAVP (HTTP antivirus scanning) is at 0.82 but the version found in ubuntu depositories is at 0.76. As compared to Debian's depositories, the version is at 0.79 for 'testing' and 0.82 for 'unstable'. 

Any chance that packages found in the ubuntu depositories will be more updated more frequently? If not, can we install debian packages in ubuntu system? 

Thanks !

---

### Post by Dr. Nick on 2006-08-05
Its usually not a good idea to mix debian/ubuntu packages, it can cause headaches. In alot of cases the repositories for ubuntu contain the latest stable version while the debian testing and unstable contain the newest versions that are not totally bug free yet. 

Their seems to be some packages that are updated more frequently then others, I believe it is up to the package maintainer to decide when to update and repackage the new versions and add them to the repositories.

---

### Post by Anduu on 2006-08-05
Like Dr.Nick said Debian is more on the "bleeding edge'....Ubuntu is built on stable software.

Do not mix the two.

---

### Post by Akhran on 2006-08-05
Thanks for the replies. 

Are there also three branches of depositories for Ubuntu, aka Debian's 'stable', 'testing', 'unstable'? Don't mind trying out the testing branch of Ubuntu if there is one :)

---

### Post by Jagot on 2006-08-05
Essentially there is Ubuntu stable and Ubuntu testing.  The next release is Edgy.  You can look at the progress and download the iso here:

[http://www.ubuntu.com/testing/](http://www.ubuntu.com/testing/)

---

### Post by Akhran on 2006-08-05
How is the stability as compared to Debian's Testing?

Thanks.


> **Jagot said:**
> Essentially there is Ubuntu stable and Ubuntu testing.  The next release is Edgy.  You can look at the progress and download the iso here:

[http://www.ubuntu.com/testing/](http://www.ubuntu.com/testing/)

---

### Post by Anduu on 2006-08-05
> **Akhran said:**
> How is the stability as compared to Debian's Testing?

Thanks.

You can go here and see for yourself...[http://www.ubuntuforums.org/forumdisplay.php?f=144](http://www.ubuntuforums.org/forumdisplay.php?f=144)

---

### Post by Dr. Nick on 2006-08-05
If im not mistaken it is basically stable/unstable

dapper being stable and edgy would be unstable.

I personally would consider dapper "testing" and edgy "unstable"

When I played with debian I never had trouble while using testing, I never used debian stable because it was all so outdated.

Ubuntus next versions always start off realtively stable once developement opens as alot isnt changed, then their is a few weeks in the middle where it can either be smooth sailing, or constant crashing, depending on your luck and when you choose to upgrade. It may be at a point now where it is decently stable as some early betas are out.

If you have decent knowledge then it is usually not a huge deal when you get crashes, just watch what packages are being altered when you update, thier are times when packages will try to remove xorg because the versions at that point in time dont match up, you just have to realize this before pushing "Y" to continue the update, or you will end up with command line only waiting until you can update and get xorg back ;)

---

