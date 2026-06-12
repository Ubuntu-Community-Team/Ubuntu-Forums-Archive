---
title: "I have messed up the synaptic package manager...."
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Eduardo Serra on 2007-04-19
I dont know what I have done but now every time I try to add/remove programs or enter the syanptic package manager I get this error


"Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'."

By the way, I was trying to add more repositories.... Im ot even sure I got it done or not.... Im still running edgy

Oh, I just remembered, when I try to go t o synaptic package manager I get this error instead...
"An error occured

The following details are provided
:E: Malformed line 4 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem."

---

### Post by scanez on 2007-04-19
There seems to be an error in your sources.list files. What is line 4 in /etc/apt/sources.list.d/edgy-universe.list?

---

### Post by Seisen on 2007-04-19
Post your whole source list.

---

### Post by Eduardo Serra on 2007-04-19
Ok, on the sources.list.d folder I have 4 files... edgy-multiverse.list, edgy-multiverse.list.save, edgy-universe.list, edgy-universe.list.save..... Heres my edgy-multiverse.list file

"# automatically added by gnome-app-install on 2007-03-22 22:17:13.320799
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe multiverse #Added by software-properties"

---

### Post by scanez on 2007-04-21
What's in the edgy-universe.list file? i.e. the one that was mentioned in the error you posted

---

### Post by luizfar on 2007-04-21
> **Eduardo Serra said:**
> The following details are provided
:E: Malformed line 4 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem."

Just check the line 4 of the file /etc/apt/sources.list.d/edgy-universe.list

---

### Post by racerx8518 on 2007-04-23
I started getting the same error message after I tried the automatic upgrade to feisty. An error occured in the upgraded talking about
 Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

 Then it told me line 3 in source.list was bad and line 3 in source.list.d/edgy-universe.list was bad.
 
 I copied and pasted my backup source.list and that fixed the first error. I came here read this.. copied and pasted the source.list.d from here..changed it to error in line 4. I went back to the original one.  Commented out line 3,  which was this. deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security
   
  and that got me another long message. which went away magically as I was writing this help message, after I closed everything down.  
 it all works fine now, except I still can't upgrade to feisty.  
 Thanks for the help.

---

