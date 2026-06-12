---
title: "USN-776-2: KVM regression"
date: 2009-05-13
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-05-13
Description: 
                                       =========================================================== Ubuntu Security Notice USN-776-2               May 13, 2009 kvm regression [https://launchpad.net/bugs/375937](https://launchpad.net/bugs/375937) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   kvm                             1:62+dfsg-0ubuntu8.2  After a standard system upgrade you need to restart all KVM VMs to effect the necessary changes.  Details follow:  USN-776-1 fixed vulnerabilities in KVM. Due to an incorrect fix, a regression was introduced in Ubuntu 8.04 LTS that caused KVM to fail to boot virtual machines started via libvirt. This update fixes the problem. We apologize for the inconvenience.  Original advisory details:   Avi Kivity discovered that KVM did not correctly handle certain disk  formats. A local attacker could attach a malicious partition that would  allow the guest VM to read files on the VM host. (CVE-2008-1945,  CVE-2008-2004)   Alfredo Ortega discovered that KVM's VNC protocol handler did not  correctly validate certain messages. A remote attacker could send  specially crafted VNC messages that would cause KVM to consume CPU  resources, leading to a denial of service. (CVE-2008-2382)   Jan Niehusmann discovered that KVM's Cirrus VGA implementation over VNC  did not correctly handle certain bitblt operations. A local attacker could  exploit this flaw to potentially execute arbitrary code on the VM host or  crash KVM, leading to a denial of service. (CVE-2008-4539)   It was discovered that KVM's VNC password checks did not use the correct  length. A remote attacker could exploit this flaw to cause KVM to crash,  leading to a denial of service. (CVE-2008-5714)
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-776-2)

---

