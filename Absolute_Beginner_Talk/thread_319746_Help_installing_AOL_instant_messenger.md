---
title: "Help installing AOL instant messenger"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by jengo on 2006-12-16
Hello, I need a little help

i downloaded the newest aim from here:

[http://www.aim.com/get_aim/linux/latest_linux.adp](http://www.aim.com/get_aim/linux/latest_linux.adp)

their advice for installing it (i downloaded the deb 3.x version) doesnt work. thanks

oh btw, im installing it because i need to use the AIM Phoneline service. Thanks.

---

### Post by xyz on 2006-12-16
I checked your link.
Could you reproduce how you went about installing it so as to be able to compare what you did with the AOL Instant Messenger Help?

---

### Post by Sef on 2006-12-16
> oh btw, im installing it because i need to use the AIM Phoneline service. 


Here is one of the specs for AIM Phoneline service:
> Windows: Windows XP Home or Professional OR Windows XP 64 bit OR Windows 2000 with DirectX 9.0 or later

So it won't work on Ubuntu unless DirectX 9.0 can work with Wine and even then it likely will not work.  Though maybe with vmware it will work.

---

### Post by jengo on 2006-12-17
it says on the site that the new linux version works with the phoneline service.

Aymore help guys? oh it just says "package not found" when i try installing it.

---

### Post by Sef on 2006-12-17
> Aymore help guys? oh it just says "package not found" when i try installing it.

Did you change to the directory where you downloaded it too?  To change directories, cd /path_to_directory/


> it says on the site that the new linux version works with the phoneline service.


Different parts of the site say different things then.

---

### Post by jengo on 2006-12-17
okay i kinda figured it out, but i got these errors.

 > diego@diego-laptop:~/Apps$ sudo dpkg -i aim_1.5.286-2_i386.deb
Password:
dpkg-deb: file looks like it might be an archive which has been
dpkg-deb:    corrupted by being downloaded in ASCII mode
dpkg-deb: `aim_1.5.286-2_i386.deb' is not a debian format archive
dpkg: error processing aim_1.5.286-2_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 aim_1.5.286-2_i386.deb


Should i try install the RPM instead?

---

### Post by maxamillion on 2006-12-17
.rpm is not natively supported under any debian based distro but they are able to be installed via a utility called alien, though I don't recommend it.

I would imagine there is some dependency that is unresolved by the package, check the website and make sure you have all listed required libraries or otherwise.

/me

---

### Post by jengo on 2006-12-17
okay, i installed the tarball file. when i try to run the app i get this error:

> diego@diego-laptop:~/Apps$ /home/diego/Apps/usr/bin/aim
/home/diego/Apps/usr/bin/aim: error while loading shared libraries: libXprt.so.1: cannot open shared object file: No such file or directory


how can i install this "libxprt.so.1" or how can i check what dependencies i need?

---

### Post by maxamillion on 2006-12-17
They should list requirements on the installation page on the aim website. (which would be the dependencies I speak of)

As far as libXprt.so ... the repositories nor google has ever heard of it so I assume it was something added by the aim package and would be causing an error because the installation did not complete successfully.

---

### Post by jengo on 2006-12-17
stupid *** aim, anyway i think i am going to try to install it through wine, thanks anyway maxamillion and everyone else. Even though i doubt that will work

---

### Post by dannystaple on 2006-12-17
> **jengo said:**
> okay i kinda figured it out, but i got these errors.

 

Should i try install the RPM instead?
Okay - Jengo, before going with the wine install, lets consider a few things. Those errors you saw look like the download was corrupt, and is normally what you get if you set the "ascii mode" flag on an FTP download of binary data - text generally can be sent with less encoded information than programs, so part of the information is stripped off, if that stripping off occurs on programs, then it is generally destructive.

Try deleting your deb, and downloading the deb again.

As for the missing library - libxprt, if you google for it, you will find it is actually part of the netscape package, and should probably be distributed in the binary aim packages (the .deb and .rpm). Using alien is not recommended when a deb is available, but I have had perfectly good results using it for a number of packages.

Another though - and don't take this badly, what is your goal? I mean by that, not what software you want installed, but what it actually is you wish to do with it? There are plenty of alternatives, that may be usable and possibly better for what you wish to achieve. Getting hung up on one awkward package or tool, and loosing site of the original aim (no pun intended) may just be an exercise in "yak shaving".

---

