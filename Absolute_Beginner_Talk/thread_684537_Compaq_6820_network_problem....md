---
title: "Compaq 6820 network problem..."
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by rookie76 on 2008-02-01
I have just installed 7.10 on a new Compaq 6820 laptop and I can't get the network card to connect through my router.  The router works fine... I have another machine running Ubuntu and I don't have any problems with it.  The Network card in the Compaq 6820s is an Intel 82562GT.  Can anyone help?

---

### Post by gvartser on 2008-02-01
What do you mean by unable to connect through your router.

Is it the internet that is unreachable?

Is the network working at all, can you reach any other machine on your network?

/g

---

### Post by gvartser on 2008-02-01
Maby this could be of interest.

[http://ubuntuforums.org/showthread.php?t=551720&highlight=Intel+82562GT](http://ubuntuforums.org/showthread.php?t=551720&highlight=Intel+82562GT)

/g

---

### Post by rookie76 on 2008-02-01
> **gvartser said:**
> Maby this could be of interest.

[http://ubuntuforums.org/showthread.php?t=551720&highlight=Intel+82562GT](http://ubuntuforums.org/showthread.php?t=551720&highlight=Intel+82562GT)

/g

Thanks for the help!  The problem that is described this tread is what I am experienceing.  However, I tried the steps set out in the tread but I am running 7.10 (64 bit) with the 2.6.22-14 kernel.  I could not locate the "linux-headers-2.6.20-15-generic for i386:" for the version I am running.

Man, I never had this much trouble on the last two machines I setup.  Thanks for pointing me in the right direction!

---

### Post by gvartser on 2008-02-04
did you try to use the kernel header for the version that you are running?

To see whats available:
```
apt-cache search linux-headers
```

To install the kernel headers: 
```
sudo apt-get install linux-headers-<version> 
```

Best regz,
/g

---

### Post by rookie76 on 2008-02-04
I think that is the problem I'm having.  The thread you showed me gives instruction on how to download the headers for 2.6.20-14 but I am using 2.6.22-14.  When I change the address on the link to the download to reflect the kernel I'm using I am unable to download the headers.  I think if I can download the appropriate headers to a flash drive I should be off to the races.  Any ideas?

---

