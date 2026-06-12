---
title: "need to prevent &quot;Cold Boot Attacks on Encryption Keys&quot;"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by say2sky on 2008-03-04
I am using encryption for /home, /swap and /root partition on my Ubuntu 7.10 system but these day some research papers and USB boot application have show it is easy to get encryption key in ram by reboot linux system.


here is the paper and the operation process
> 
Creating bootable USB drives for capturing the contents of memory
[http://mcgrewsecurity.com/projects/msramdmp/](http://mcgrewsecurity.com/projects/msramdmp/)

Cold Boot Attacks on Encryption Keys
[http://citp.princeton.edu/memory/](http://citp.princeton.edu/memory/)


My question is 
How user can do to prevent this kind of encryption key disclosure? Can we rewrite the ram during shutdown process and how?

---

### Post by neurostu on 2008-03-04
As far as I know the only way for any of these attacks to work is for person to have **physical access** to the computer. You can buy a case that locks (can't be opened without a physical key) you can keep it in a locked room.  I'm sure you could create something that would fill your RAM with garbage data, but I think the idea is that the RAM needs to have the encryption key stored in it so that it can interpret the data from the HDD.  If you don't have this then you can't read or write to the HDD.  I'm not sure how you could shut down without being able to read from your HDD.

Also I think the keys might be stored in your ram for boot, or else how could your pc read the HDD on boot, (BUT I COULD BE WRONG, I'm not an expert in cryptography)

If you're worried about someone stealing or seizing your PC and then reading the contents of your HDD, then there really isn't anything you can do... once they have you HDD they will probably have as much time as they need to just brute force the encryption.

---

### Post by kool_kat_os on 2008-03-04
> **say2sky said:**
> I am using encryption for /home, /swap and /root partition on my Ubuntu 7.10 system but these day some research papers and USB boot application have show it is easy to get encryption key in ram by reboot linux system.


here is the paper and the operation process


My question is 
How user can do to prevent this kind of encryption key disclosure? Can we rewrite the ram during shutdown process and how?

thanks for the info...lol

---

### Post by say2sky on 2008-03-04
> **neurostu said:**
> As far as I know the only way for any of these attacks to work is for person to have **physical access** to the computer. You can buy a case that locks (can't be opened without a physical key) you can keep it in a locked room.  I'm sure you could create something that would fill your RAM with garbage data, but I think the idea is that the RAM needs to have the encryption key stored in it so that it can interpret the data from the HDD.  If you don't have this then you can't read or write to the HDD.  I'm not sure how you could shut down without being able to read from your HDD.

Also I think the keys might be stored in your ram for boot, or else how could your pc read the HDD on boot, (BUT I COULD BE WRONG, I'm not an expert in cryptography)

If you're worried about someone stealing or seizing your PC and then reading the contents of your HDD, then there really isn't anything you can do... once they have you HDD they will probably have as much time as they need to just brute force the encryption.

Thanks for your info. And you are absolutely right about brute force to access info on HDD.

Your info about fill RAM with garbage data is what I want and I think it is not too hard work but perhaps it need a little bit more time to shutdown the system. If so why not just have this kind of choice for user to use or not  and let encryption  root system to become much more tighter to other.

---

