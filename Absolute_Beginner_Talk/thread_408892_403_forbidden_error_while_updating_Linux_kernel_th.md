---
title: "403 forbidden error while updating Linux kernel through daily updates."
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by keith11 on 2007-04-13
Hello:

I was trying to install the updates I was notified about as soon as I logged into my Kubuntu Feisty beta box today. Two of the updates included the linux kernel image for 386 and the generic one. As soon as the updates reached the task of upgrading the kernel it gave me the following error:

[COLOR="Red"]W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-386_2.6.20-14.23_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-386_2.6.20-14.23_i386.deb)
  403 Forbidden [IP: 91.189.89.6 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-generic_2.6.20-14.23_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-generic_2.6.20-14.23_i386.deb)
  403 Forbidden [IP: 91.189.89.6 80][/COLOR]

I am not sure what is wrong here. Any help will be greatly appreciated. Thanks.

Keith.

---

### Post by yabbadabbadont on 2007-04-13
It is probably because the updates broke a whole bunch of people's machines so that they couldn't boot.  Search through todays forum posts and you will see what I mean.  I imagine they removed access to the deb files until they can get the issue fixed.

---

### Post by hardyn on 2007-04-13
thats okey... 

all hell broke loose last night with a bad kernel... it should be fixed today... but hold on a few more days before doing that update.

cheers.

---

### Post by yabbadabbadont on 2007-04-13
[http://ubuntuforums.org/showthread.php?t=408253](http://ubuntuforums.org/showthread.php?t=408253)

See this for details.

---

### Post by Bachstelze on 2007-04-13
No problem here with the 2.6.20-14-generic, I suggets tou switch to the generic kernel as it wil give you better performance than the 386 one anyway.

---

### Post by hardyn on 2007-04-13
No, it wont...

the 386 kernel is now a generic uniprocessor kernel.  this started with edgy.

The generic kernel doesn't play nice with alot of Asus and Sony notebooks.

---

### Post by keith11 on 2007-04-13
Thank you Yabbadabbadont and Hardyn for your quick responses. I think I will wait unitl the error is fixed.

Keith.

---

### Post by keith11 on 2007-04-13
Thank you Yabbadabbadont and Hardyn for your quick responses. I think I will wait unitl the error is fixed.

Keith.

---

