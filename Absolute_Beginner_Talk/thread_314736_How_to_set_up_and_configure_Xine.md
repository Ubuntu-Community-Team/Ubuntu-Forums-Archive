---
title: "How to set up and configure Xine"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by Scottty on 2006-12-08
Hello

I want to set xine up to play DVD's does anyone know the best place to go to configure and setup xine.

thanks
Scott

---

### Post by riven0 on 2006-12-08
> **Scottty said:**
> Hello

I want to set xine up to play DVD's does anyone know the best place to go to configure and setup xine.

thanks
Scott

What happens if you do *sudo apt-get install gxine libdvdcss* ?

---

### Post by Scottty on 2006-12-08
This is what I got when I typed sudo apt-get Install gxine libdvdcss
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss has no installation candidate
user@user-desktop:~$ 


Where should I go from here?

Scott

---

### Post by riven0 on 2006-12-08
> **Scottty said:**
> This is what I got when I typed sudo apt-get Install gxine libdvdcss


Where should I go from here?

Scott

Did you make sure to add all your repositories? I'm guessing you're using edgy, so got to synpatic package manager >> settings >> repositories. Make sure all the options listed under Internet are checked. Then click Reload on the toolbar. 

Now copy and past this in the terminal: *sudo apt-get update && sudo apt-get install gxine* 

Hopefully it'll work.

EDIT: Took out the libdvdcss. I think it should work without it.

---

### Post by Scottty on 2006-12-08
I followed your advice and this is what I got at the command line.

```

sudo apt-get update && sudo apt-get install gxine 

```

> 
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Translation-en_US                   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Translation-en_US             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/multiverse Translation-en_US             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Translation-en_US
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/universe Translation-en_US
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy Release  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates Release
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Packages                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Fetched 3B in 0s (4B/s)  
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?



I went into the settings of synaptic and everything was already checked

Thanks for getting back to me so soon riven0

Did I install anything here. or am I still not getting what I need?

Scott

---

### Post by riven0 on 2006-12-08
> **Scottty said:**
> I followed your advice and this is what I got at the command line.

```

sudo apt-get update && sudo apt-get install gxine 

```



I went into the settings of synaptic and everything was already checked

Thanks for getting back to me so soon riven0

Did I install anything here. or am I still not getting what I need?

Scott

sorry for getting back to you late on this. Did you by chance happen to have synpatic open when you were trying to install gxine? This will give you that error.

---

### Post by Scottty on 2006-12-10
cool thanks, i think I may have had synaptic open at the time
I will retry when I get home from work

Thanks
Scott

---

### Post by Scottty on 2006-12-14
Thanks

It was because I had synaptic open. Or so it seems. Xine seems to work great with avi's and mp4 files so far.

Scott

---

