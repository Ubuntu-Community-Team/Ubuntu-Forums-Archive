---
title: "Macbook 3.1/LTS 16.04 (lubuntu) No wifi after broadcom procedure"
date: 2016-09-24
forum: Apple Hardware Users
---

### Post by kristina-shamgunova on 2016-09-24
Hello,
my wifi does not work. I went through the procedure described in the broadcom sticky thread. ([here]("https://ubuntuforums.org/showthread.php?t=2214110"))
Now my mac will scan for wifi connections but never succeeds in connecting after authorization.
The connection works fine on other devices and my key is 100% correct.
I'm super unexperienced and have no lead on what could be the problem.
Wireless script info file is attached to the thread.

I can't thank enough for responses. Thank you thank you thank you!
Greets,
Kristina.

---

### Post by jeremy31 on 2016-09-24
*Thread moved to **Apple Hardware Users**.*
I would try ```
sudo apt-get install bcmwl-kernel-source
```
Reboot

As your chipset is only partially supported by b43 according to [https://wireless.wiki.kernel.org/en/users/drivers/b43](https://wireless.wiki.kernel.org/en/users/drivers/b43)

---

### Post by kristina-shamgunova on 2016-09-24
Yup, I did it, but it did not work. 
If you have a different idea I will provide you with most information, I just don't know what could be useful for you.
Thanks!

---

### Post by jeremy31 on 2016-09-24
Lets set the regulatory info for Germany, if that is correct
```

sudo iw reg set DE
```
```
sudo sed -i 's/^REG.*=$/&DE/' /etc/default/crda

```

Reboot and run the script again if it still fails to work

---

### Post by kristina-shamgunova on 2016-09-24
I did what you told me to and the situation did not change,
but while testing the connection with the LAN cable unplugged there was a brief connection (few seconds). I might not have noticed these brief connections before.
I'll attach the new info file.

Thank you as always.

---

### Post by kristina-shamgunova on 2016-09-24
Oh my. It works.
Thank you and sorry for the confusion.
Greets 
Kristina

---

### Post by erotavlas on 2017-04-01
> **kristina-shamgunova said:**
> Oh my. It works.
Thank you and sorry for the confusion.
Greets 
Kristina

Hi,
I'm going to install lubuntu 16.04 LTS 64 bit on the same macbook as yours (3,1). Can you specify if all the hardware with question mark [here]("https://help.ubuntu.com/community/MacBook3-1/Xenial") works properly?
Thank you

---

