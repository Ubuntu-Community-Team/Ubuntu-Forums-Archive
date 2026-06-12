---
title: "is setting up wireless in Edgy the same as Dapper for Broadcom chipsets?"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-10-26
I remember it was a hassle in dapper with broadcom airforce one wireless driver to set up the wireless. is anyone having the same problem in edgy or is the problem less of a problem and how did anyone set theirs up?

---

### Post by Jagot on 2006-10-26
I'm currently having problems.  I have a BCM4318 which I got working in Dapper easily with ndiswrapper, but cannot seem to do the same in Edgy.  Still working on it . . .

---

### Post by qamelian on 2006-10-26
It was for me with a BCM4306. Just used bcm43xx-fwcutter to extract firmware from the Windows driver to /lib/firmware and all was good.

---

### Post by maddbaron on 2006-10-26
oh ok, i'll wait then i'll download the iso then install once i can copy the solution to a text file so i can connect.

hope you find a solution

---

### Post by maddbaron on 2006-10-26
I am noticing the 4306 is easier to solve but I have the 4318 which is a problem...the way it was set up in dapper just doesnt seem to work in edgy from what I read recently

---

### Post by Jagot on 2006-10-26
Just got the BCM4318 working with ndiswrapper - it appears the version in the repositories does not work.. If you go the ndiswrapper route you'll need to install the latest version - [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

---

### Post by maddbaron on 2006-10-26
> **Jagot said:**
> Just got the BCM4318 working with ndiswrapper - it appears the version in the repositories does not work.. If you go the ndiswrapper route you'll need to install the latest version - [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

you got yours from the site by downloading it or did you follwo the instructions in the wiki?
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

I went to download it and it said error in the links....

also if its not a problem could you post the code you used to set up your wireless please?

---

### Post by stevieb on 2006-10-26
doesn't bcm4318/19 use bcm43xx-fwcutter and not ndiswrapper?

---

### Post by Jagot on 2006-10-26
I got mine directly from the ndiswrapper site - didn't follow the wiki guide.

I've just been to the site again and it is producing errors now but it wasn't earlier.  I've attached the file to this post.

Firstly make sure that you've completely got rid of the nidswrapper from the repo's if you downloaded that first, as I did.

Follow the install file instructions to compile and install - it's a non standard compilation.

Then:

```
sudo ndiswrapper -i ~/Desktop/bcmwl5/bcmwl5.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

---

### Post by Jagot on 2006-10-26
> **stevieb said:**
> doesn't bcm4318/19 use bcm43xx-fwcutter and not ndiswrapper?

You should be able to do it with either, but bcm43xx has never worked for me so I've always used ndiswrapper.

---

### Post by matt_risi on 2006-10-27
I'm also having troubles with my 4318, except it's not detecting it at all. Installed it in Dapper without much issue, any ideas?

---

### Post by Jagot on 2006-10-27
> **matt_risi said:**
> I'm also having troubles with my 4318, except it's not detecting it at all. Installed it in Dapper without much issue, any ideas?

Which method are you trying to use?

---

### Post by Aranel on 2006-10-27
Took me a full minute to set mine up.

I've got a BCM4306 (Linksys WPC54G v1.2). I just took the bcmwl5.sys file off the CD that came with it, installed bcm43xx-fwcutter, extracted the firmware to /lib/firmware/, entered modprobe bcm43xx, and BOOM! Connected.

---

### Post by stevieb on 2006-10-27
haven't gotten around to trying it yet; tried to upgrade to edgy last night, but it crashed.  trying a fresh install tonight, and intend to use the method aranel describes, but with wlapsta-o, as my 4319 is internal and i don't have a cd with driver.  i'll post once i have a result.
-steve

-steve

---

### Post by matt_risi on 2006-10-27
I haven't tried any of the above methods, as Edgy isn't even detecting that the card is even present. (It doesn't show up in the networking dialogue). I'm clueless as to why, the install went perfect aside from this.

---

### Post by matt_risi on 2006-10-27
Issue resolved for me:

[http://www.ubuntuforums.org/showthread.php?t=285809&highlight=edgy+bcm4318](http://www.ubuntuforums.org/showthread.php?t=285809&highlight=edgy+bcm4318)

---

### Post by stevieb on 2006-10-27
installed edgy tonight; the following guide got my broadcom 4319 running on my lenovo 3000 c100:
[http://www.ubuntuforums.org/showthread.php?t=197102&highlight=howto+broadcom]("http://www.ubuntuforums.org/showthread.php?t=197102&highlight=howto+broadcom")

didn't even have to reboot!
-steve

---

### Post by Paul_UK on 2006-12-02
We have "upgraded" two Dell D600 laptops which use broadcom wireless from 6.06 to 6.10.  The wireless was set up with fw-cutter in 6.06 and worked fine, but since the upgrade it keeps disconnecting for no obvious reason.  I can't find anything here about it.

6.10 is too buggy, and there is no way back to 6.06 other than a reinstall.....

---

### Post by stevieb on 2006-12-02
i ended up using ndiswrapper for edgy, and got it to work fine (was using fwcutter with dapper).  i haven't had problems with edgy being buggy, although the upgrade didn't work for me; i needed a fresh install.

-steve

---

