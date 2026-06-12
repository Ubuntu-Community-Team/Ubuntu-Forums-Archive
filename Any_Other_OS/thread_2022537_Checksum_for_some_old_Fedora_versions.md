---
title: "Checksum for some old Fedora versions"
date: 2012-07-11
forum: Any Other OS
---

### Post by tech291083 on 2012-07-11
Hi,

I have some old Fedora DVDs with me whose checksum I want to verify but the official Fedora site does not seem to have the checksum for Fedora core 5. Can anyone please help me?

I went to the below page, which has a link called

[See old versions of Fedora]("http://archive.fedoraproject.org/")


But as I went about clicking on links one by one I got to the below page, which does not seem to have Fedora 5 on the list. 


[http://archive.fedoraproject.org/pub/fedora/linux/releases/](http://archive.fedoraproject.org/pub/fedora/linux/releases/)

Thanks..

---

### Post by qyot27 on 2012-07-12
[http://archive.fedoraproject.org/pub/archive/fedora/linux/core/5/](http://archive.fedoraproject.org/pub/archive/fedora/linux/core/5/)

Go into the right architecture, the 'iso' subdirectory.  The SHA1SUM file is there.

However, I don't know if you can use it that way with a burned disc.  It may require downloading the isos themselves again and running a verify operation.

---

### Post by tech291083 on 2012-07-13
I have only DVDs left with of all old Fedora versions, no iso images any more. Do checksums change once the iso images are burned to a CD/DVD? If so, this is news to me. Thanks.

---

### Post by qyot27 on 2012-07-13
Checksums get computed against singular files, and the ones provided on the Fedora FTP there are summed against the .iso files, not against all the files/directories the ISO contains.  Therefore, they have to be checked against an ISO file.  Whether it would change if you recreated an ISO from a burnt disc is tricky since it depends on the method used to create the original images.

That's why I said you may have to re-download the ISOs (they're right there in the directory with the SHA1SUM file), run the checksum on the ISOs, and then use normal disc-burning software to verify that the ISO and the disc are correct.

---

### Post by tech291083 on 2012-07-13
> **qyot27 said:**
>   Therefore, they have to be checked against an ISO file.  Whether it would change if you recreated an ISO from a burnt disc is tricky since it depends on the method used to create the original images.


Ok, I got your point. have a software called imgburn on my Win 7 pc and I can use that to create iso images from CD/DVD then I will be able to check their checksums. Thanks a lot for the help so far, appreciated.

Hi,

As mentioned earlier I extracted original iso images from DVDs using the imgburn software in on my Windows pc, but the checksum seems to have changed now. Is it normal? Surprisingly the DVD works well. This is getting more interesting now. Thanks.

[http://www.imgburn.com/](http://www.imgburn.com/)

---

### Post by qyot27 on 2012-07-14
Download the relevant ISO image(s) from the Fedora FTP site, check them against the SHA1SUM file to make sure they're correct.

Use ImgBurn to verify the disc(s) against the ISOs that were just downloaded and checked.


This is the only method that ensures a low margin of error.

---

