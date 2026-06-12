---
title: "Can't install Wine from repository"
date: 2012-07-10
forum: Any Other OS
---

### Post by jorx on 2012-07-10
> **Dedas said:**
> When I try to install the wine package with apt-get I get a dependency error for wine1.4. Synaptic also wants to install a lot of i:386 packages. 

I did an upgrade from Ubuntu 11.10 to 12.04.

Also, if I try to install playonlinux, synaptic wants to remove xorg for example.

I have no warnings for broken packages.

I'm left clueless, please help. :)

I get the same problem!

Just installed a fresh linux mint 13 - "Cinnamon" variant.
First thing I go to install- Wine 1.4. And I get this error?


E: Unable to correct missing packages 

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.0.0_1.0.1-4ubuntu5_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.0.0_1.0.1-4ubuntu5_amd64.deb) 
404 Not Found [IP: 91.189.92.179 80] 


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.0.0_1.0.1-4ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.0.0_1.0.1-4ubuntu5_i386.deb) 
404 Not Found [IP: 91.189.92.179 80]

---

### Post by SavageCHRIS on 2012-07-10
> **jorx said:**
> I get the same problem!

Just installed a fresh linux mint 13 - "Cinnamon" variant.
First thing I go to install- Wine 1.4. And I get this error?


E: Unable to correct missing packages 

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.0.0_1.0.1-4ubuntu5_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.0.0_1.0.1-4ubuntu5_amd64.deb) 
404 Not Found [IP: 91.189.92.179 80] 


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.0.0_1.0.1-4ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.0.0_1.0.1-4ubuntu5_i386.deb) 
404 Not Found [IP: 91.189.92.179 80]

This should fix your problem

[http://www.ivegotavirus.com/how-to-fix-wine-in-linux-mint-13-maya/](http://www.ivegotavirus.com/how-to-fix-wine-in-linux-mint-13-maya/)

---

### Post by Perfect Storm on 2012-07-10
Split'n'move to Other OS/Distro Talk.

---

### Post by jorx on 2012-07-15
** EDIT ** **
it worked! 

I had to refresh Synaptic- which updated all the packages listed via repositories.
Then it worked! Finally! 
I'm still having other issues, but linux mint is useable for me now.

cheers!



** ORIGINAL MESSAGE BELOW **
hey SavageCHRIS- 
thanks for the link! but it still doesn't fix my problem :( 
would it work with the latest ubuntu out of the box? because this is enough of a problem for a distro change!
I already have that line:

```
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
```in my repositories, but get the same issue.
cheers,
Jordan

---

