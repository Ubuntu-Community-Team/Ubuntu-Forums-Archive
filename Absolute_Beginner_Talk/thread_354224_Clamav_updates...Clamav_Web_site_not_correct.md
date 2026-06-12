---
title: "Clamav updates...Clamav Web site not correct?"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by three-cushion on 2007-02-05
I have clamav installed, Ver 0.88.4. I install using a "clean" <sources.list> file that includes all the repositories, Universal, etc.

Each use of clamav gives me the "Your version is out-of-date.. . So I try what that URL suggests; put another descriptive file (deb:  //ftp....sarge/volatile...) in the sources.list file.. 

I do this BUT, the resulting ```
 sudo apt get update
``` 
only causes a lot of trouble... can't install this b/c THAT is not installed and won't be... so on & so on... A real pain.

If the extra deb statement doesn.t work what will?

---

### Post by dcstar on 2007-02-07
> **three-cushion said:**
> I have clamav installed, Ver 0.88.4. I install using a "clean" <sources.list> file that includes all the repositories, Universal, etc.

Each use of clamav gives me the "Your version is out-of-date.. . So I try what that URL suggests; put another descriptive file (deb:  //ftp....sarge/volatile...) in the sources.list file.. 

I do this BUT, the resulting ```
 sudo apt get update
``` 
only causes a lot of trouble... can't install this b/c THAT is not installed and won't be... so on & so on... A real pain.

If the extra deb statement doesn.t work what will?

You can basically ignore the clamav message, there will (eventually) be a new version placed in the official Ubuntu repositories and the software will function just as well on the current version.

---

