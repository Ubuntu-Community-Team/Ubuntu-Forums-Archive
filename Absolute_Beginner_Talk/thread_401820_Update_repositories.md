---
title: "Update repositories"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by sirius0 on 2007-04-05
I will soon be on broadband. ( a month or so) I was just wondering though; as I am on dial up for now.
Can the update repository be downloaded via wget?
If so and this is allowable then what exactly is the address?
(is it this? [http://in.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/](http://in.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/))
Can this fit on a cd or should I use the directory list switch to turn off AMD64 ( I am on i386)?

Obviously I am planning on using wget for windows on the work network (naughty aren't I?)

---

### Post by heimo on 2007-04-05
This guide isn't quite what you're looking for as it requires some programs not available on Windows. But here it is anyway, "building DVD Images of Ubuntu Repositories":
[http://www.howtoforge.com/dvd_images_of_ubuntu_repositories](http://www.howtoforge.com/dvd_images_of_ubuntu_repositories)

---

### Post by irwa82 on 2007-04-05
Hi,

$ sudo apt-get update

this will update your repository list to the latest.

then do the following

 $ sudo apt-get --no-download --show-upgraded upgrade > debfiles.txt

NOTE: i could not test the above just looked in the man page as my system is up to date.

then at work download all the packages that it was going to update from packages.ubuntu.com

then at home copy the files to /var/cache/apt/archives/

Then do the upgrade and it should not have to download any files as it will find them on the hard drive.

Also if you are still looking for a broadband provider then look for one that has a package repository for a lot of popular many distros have mirrors and won't charge for downloads from their mirrors. My isp does this and it is great no bandwidth used for getting my software and updates.

---

### Post by sirius0 on 2007-04-09
The community aspect of UBUNTU in action!
Thank you for those great posts.
Thank you also for the tip on how to do a DVD  and that one about ISPs possibly having a mirror.
:)

---

