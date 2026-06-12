---
title: "Asus G72gx running Ubuntu 11.4 Wireless issues"
date: 2011-07-18
forum: Asus Ubuntu Support (CLOSED)
---

### Post by LostRealist on 2011-07-18
First off, I am a complete and total noob. I have no experience whatsoever with Ubuntu or Linux. I have looked around the forums but haven't had much luck with my issue. I see people posting about network issues but none of them have the same hardware.

First of all, when I installed Ubuntu something popped up the first time I ran it that said that I don't have the hardware to run "Unity." This laptop is a newer Republic of Gamer's laptop so I assume (but I'm not very experienced, so forgive me) that it shouldn't have trouble running Unity.

Secondly, from the very first time I started it I was getting EXTREMELY slow internet speeds. Interestingly, I could load Google search results with ease. But anything else would either not load or would take 5-10 minutes.

There were a ton of updates that Ubuntu kept trying to download but it would freeze so I restarted the system whenever it would freeze. After about the third time I could never get an internet connection again.

So now I have a 17 GB partition with Ubuntu on it that is useless. Should I uninstall and re-install Ubuntu? How would I go about doing that?

If this question has already been answered or if there is a thread on a similar problem with my hardware I apologize for the duplicate. Thanks to anyone willing to help me out.

---

### Post by kptsuresh on 2011-07-18
you should remove those updates to continue using the ubuntu..becuase you were stopped update in the middle..

go to recovery mode and use this command to remove updates...

apt-get  -f install
or
apt-get remove (--purge)

after try chkdsk

then reboot

---

### Post by LostRealist on 2011-07-18
> **kptsuresh said:**
> you should remove those updates to continue using the ubuntu..becuase you were stopped update in the middle..

go to recovery mode and use this command to remove updates...

apt-get  -f install
or
apt-get remove (--purge)

after try chkdsk

then reboot

Thanks kptsuresh for responding! As soon as I get home I'm going to try this. But from there do you know how ill fix the freezing of the updates and the slow internet? Thanks again.

---

### Post by LostRealist on 2011-07-19
So I tried the commands. The first two result in "0 upgraded, 0 newly installed, 0 to remove and 189 not upgraded."

---

### Post by Synoc on 2011-07-25
for what it's worth, I HAVE a G72GX, and it works flawlessly with ubuntu 10.10. so my first reaction is that it's a software issue, did you install the 64 bit version of Ubuntu or the 32 bit? I had heard driver support for 64 bit wasn't as stelllar so I installed 32 bit.

---

