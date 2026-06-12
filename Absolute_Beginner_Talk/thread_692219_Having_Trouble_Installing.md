---
title: "Having Trouble Installing"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by hobohitman on 2008-02-09
I am trying to install the GUI 7.10 Version on my sytem. I already have it dual booting Vista and the Server edition of 7.10, and Grub is installed on my system. I have found that no matter how much I tinker around with CLI I cant really figure it out and I would like to switch to the GUI version so I can adapt better, however, I cant boot off of the DvD with the ISO on it. It doesnt fail to boot like it is corrupt, I just dont get the option to. My machine goes from the "Dell" startup page to the Grub Loader window. I can still boot off of the Server Edition CD.

Could anyone tell me how I can either replace the server edition with the desktop, or how I can set up a triple boot?

Thanks

---

### Post by gate on 2008-02-09
> the DvD with the ISO on it
 Did you actually burn the ISO file on the disk, so if you open it you see a .iso file, or did you actually burn the ISO *to* the dvd, so when you open it you see things like a folder called isolinux?

  In other words, when you put the disk in on windows and open it, what files do you see?

---

### Post by hobohitman on 2008-02-09
I see a single file called 

ubuntu-7.10-desktop-amd

It is an ISO file.

---

### Post by jan quark on 2008-02-09
then the disc is burned not correctly

have a look at this for burning the iso correctly


[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by hobohitman on 2008-02-09
Thanks a bunch! I realize now that when I did it all I did was copy the file, not burn it the right way. I am still confused with vista a little bit and I guess I just didnt do it right. I just burned the ISO using Roxio and I am getting ready to use it. Do I have to remove the partition for my server edition? Or can I just make more room for this version and have a triple boot?

---

### Post by gate on 2008-02-09
It just needs a partition, it doesn't matter that there is another Linux on there (ubuntu server or whatever) GRUB will take care of the booting. You will need room on there for the install, but you only need to remove the Ubuntu server partition if you want to replace it, not if you want to triple boot.

---

