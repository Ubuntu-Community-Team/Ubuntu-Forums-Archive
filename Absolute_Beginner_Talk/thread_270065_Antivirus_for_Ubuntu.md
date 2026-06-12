---
title: "Antivirus for Ubuntu"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by SpiceWeasel on 2006-10-02
I was wondering where i can get an antivirus that will let me scan my files for say, windows viruses before moving the files to my windows partition since norton is pretty much useless as most spy/adware and viruses destroy it in a heartbeat. Now i know its not high up on most opensource communities todo lists but i think it would be really helpful if there was one. The main reason i ask is because my only recent backups may be contaminated by the virus that has been continually destroying the windows partitions on my desktop which is dual booting ubuntu and xp pro. :(  Any ideas how i should go about checking files on ubuntu for viruses before moving them to windows in a dual boot system? Or isn't that possible?

---

### Post by GStubbs43 on 2006-10-02
There is Avast! Home For Linux and I think AVG, Automatix has a "Security Suite" Option as well...

---

### Post by blx_286 on 2006-10-02
> **SpiceWeasel said:**
> I was wondering where i can get an antivirus that will let me scan my files for say, windows viruses before moving the files to my windows partition since norton is pretty much useless as most spy/adware and viruses destroy it in a heartbeat. Now i know its not high up on most opensource communities todo lists but i think it would be really helpful if there was one. The main reason i ask is because my only recent backups may be contaminated by the virus that has been continually destroying the windows partitions on my desktop which is dual booting ubuntu and xp pro. :(  Any ideas how i should go about checking files on ubuntu for viruses before moving them to windows in a dual boot system? Or isn't that possible?

Try [AVG]("http://free.grisoft.com/doc/5390/lng/us/tpl/v5").

---

### Post by Marsolin on 2006-10-02
[Here]("http://linuxappfinder.com/security/anti-virus") is a list of some other anti-virus apps. [ClamAV]("http://linuxappfinder.com/package/clamav") is a popular one along with [Avast]("http://linuxappfinder.com/package/avast") that was already mentioned.

---

### Post by arkangel on 2006-10-02
[f-prot ]("http://www.f-prot.com/products/corporate_users/unix/")too

---

### Post by arkangel on 2006-10-02
> **Marsolin said:**
> [Here]("http://linuxappfinder.com/security/anti-virus") is a list of some other anti-virus apps. [ClamAV]("http://linuxappfinder.com/package/clamav") is a popular one along with [Avast]("http://linuxappfinder.com/package/avast") that was already mentioned.

wow!  there are more antivirus for linux than viruses for linux ;)

---

### Post by SpiceWeasel on 2006-10-02
Thanks think I'll try avast for starters. :)


*EDIT* What command should i use to add avast to KDE/GNOME after installing it?

---

### Post by fatsheep on 2006-10-02
I'm not sure how good ClamAV but it sure does scan FAST.

---

### Post by Craftycorner on 2006-10-12
Now, how the blazes do you install the antivirus once you download it?  add/remove programs doesn't do beans to any program that isn't in IT'S programming.

---

### Post by blendmaster on 2006-10-12
It depends on the file type. If it's bz2, use

```
sudo jfx <filename>
```

if tar

```
sudo tar <filename>
```

if deb

```
sudo -i dpkg <filename>
```

if rpm, install alien first

```
sudo apt-get install alien
```

then

```
sudo alien -d <filename>
```

However, you first want to put the file in a directory that you know, like the desktop (where I put mine). That way, you can go to the desktop 

```
cd ~/Desktop
```

and then unpack your file.

---

### Post by Ozitraveller on 2006-10-28
double clicking on the deb should install it, mine did.

---

