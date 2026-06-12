---
title: "rpm compatibility"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by carverj on 2007-03-19
Hi all,
          Just wondering if there is a simple way to install rpm packages in Ubuntu? The particular program (xen virtual machine) doesn't seem to be avaialable in our repo's!

---

### Post by 23meg on 2007-03-19
Xen is available in the Universe repository. You should only use RPMs as a last resort; you can convert them using *alien*.

---

### Post by etank on 2007-03-19
I found this thread that may help [http://www.ubuntuforums.org/showthread.php?t=9260&highlight=xen](http://www.ubuntuforums.org/showthread.php?t=9260&highlight=xen).

If you really want to install from an rpm then you should look into [alien]("http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/"). I do suggest that where possible you find a deb for the apps you want.

---

### Post by carverj on 2007-03-19
Yup, your informative posts led me to do further research. It seems that Xen may be helpful for a business virtualization solution. One Ubuntu user claims kvm is the go for home, and another preferred virtualbox (although no AMD64 packages were available).

My situation is that I have used vmware (but have been unable to configure it myself after numerous attempts), xen scripts at uni (all I had to do was type xm721 create -c virtpc1 in command line, and had a virtual fedora machine in shell) and would like to get something working on Ubuntu. 

  I am not at the level yet were I have configured my own kernel (some virtual machines seem to necessitate this). Any howto or help would be greatly appreciated!

---

