---
title: "cant boot ubuntu 7.1"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by solikos on 2008-03-16
Hi to all!!i have installed ubuntu 7.1 and i didn t have any problem.Until one day,when i found that i couldn't boot to ubuntu neither from deault boot nor recovery mode.
-When i try to boot,the bar(which becomes orange) doesn't load!
how can i fix this problem???At least,how can i have access to the command line in order not to lose some very important files????Thnx in advance!!!!!

---

### Post by robertchahine on 2008-03-16
does your loading bar get stuck in the 1/4?

---

### Post by Diabolis on 2008-03-16
I had the same problem, my system got corrupted because I accidentaly shutdown my pc while upgrading the kernel. I got it fixed by inserting the live-cd and upgrading my system through it.

```
sudo apt-get update
sudo apt-get upgrade
```

If you want to see why the ubuntu bar is not loading, follow this instructions:

When grubs appears, select your operating system and press **_e_** then select the line that say kernel and press **_e_** at the end erase **_splash_** and then press esc so you can boot up. Doing that will disable the ubuntu splash screen and you'll be able to see what is taking so long to get done while booting.

---

### Post by tangibleorange on 2008-03-16
Another way to see what is happening behind the splash bar is to press Alt+F2 whilst loading.

As for accessing the command line to save files, there should be an entry in your GRUB menu that is labelled "recovery mode" select that and it will boot you into a root prompt.

Good luck!

---

### Post by robertchahine on 2008-03-16
> **Diabolis said:**
>  I got it fixed by inserting the live-cd and upgrading my system through it.

```
sudo apt-get update
sudo apt-get upgrade
```

so you boot your machine from the live CD?
then you upgrade the system?

---

### Post by Diabolis on 2008-03-16
yes. I don't know exactly how the live-cd worked, but It is somehow designed to help you recover already installed systems if it detects them.
I know its surprising and very useful.

---

### Post by solikos on 2008-03-16
> **Diabolis said:**
> 
```
sudo apt-get update
sudo apt-get upgrade
```

actually an error occured when trying to upadate the kernel```
Unpacking replacement libsmbclient ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.22-14_2.6.22-14.52_all.deb
 /var/cache/apt/archives/xserver-xorg-core_2%3a1.3.0.0.dfsg-12ubuntu8.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Do you know what does it mean????

---

### Post by Diabolis on 2008-03-16
> After you get that error, try apt-get -f install to force an install of the files that didn't get loaded because of the error. Then try apt-get upgrade again, apt-get -f install back and forth until only the package that has the error is left.

from: [http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/](http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/)

---

### Post by solikos on 2008-03-16
> **Diabolis said:**
> from: [http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/](http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/)

i tried apt-get -f install,but another error occures!```
Reading package lists... Error!
E: Read error - read (14 Bad address)
E: The package lists or status file could not be parsed or opened.

```
i tried again and it showed me:```
Bus error (core dumped). 0%

```
What can i do then?

---

### Post by Diabolis on 2008-03-16
1,- Check if your disk is full, if so you need to free some space
2.- Clean the cache
```
sudo apt-get clean
sudo apt-get autoclean
```

Then try again
```
sudo apt-get -f install
```

If you don't see any progress, try this:
```
sudo apt-get update -o APT::Cache-Limit=25165824
```

I hope that works, you can read more about that command here:
[https://bugs.launchpad.net/debian/+source/apt/+bug/%2024626](https://bugs.launchpad.net/debian/+source/apt/+bug/%2024626)

---

### Post by solikos on 2008-03-16
> **Diabolis said:**
> 1,- Check if your disk is full, if so you need to free some space
2.- Clean the cache
```
sudo apt-get clean
sudo apt-get autoclean
```

Then try again
```
sudo apt-get -f install
```

If you don't see any progress, try this:
```
sudo apt-get update -o APT::Cache-Limit=25165824
```

I hope that works, you can read more about that command here:
[https://bugs.launchpad.net/debian/+source/apt/+bug/%2024626](https://bugs.launchpad.net/debian/+source/apt/+bug/%2024626)

thank you a lot mate!

---

### Post by Diabolis on 2008-03-16
I'm glad it worked. 
So did you use the fancy looking command?

---

### Post by solikos on 2008-03-16
No,in fact the autoclean command worked well!:)

---

### Post by Diabolis on 2008-03-16
Oh cool, good to know for future reference. Don't forget to mark the thread as solved.

---

