---
title: "[SOLVED] xubuntu alternate installation fails when loading inst components"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by muckvoc on 2007-10-16
Hi everyone, 
i'm an absolute beginner trying to install linux on a toshiba pIII 128mb ram laptop with  15 gb of hard drive. i've tried ubunto live cd and switched to xubuntu alternate feisty fawn after failure.

now it's stopping when loding the installer components from the cd.

the cd is fine. maybe the cd-rom drive kind of stops working?

any help would be great, thanks!

---

### Post by overdrank on 2007-10-16
> **muckvoc said:**
> Hi everyone, 
i'm an absolute beginner trying to install linux on a toshiba pIII 128mb ram laptop with  15 gb of hard drive. i've tried ubunte live cd and switched to xubuntu alternate faisty fawn after failure.

now it's stopping when loding the installer components from the cd.

the cd is fine. maybe the cd-rom drive kind of stops working?

any help would be great, thanks!

Hi and welcome, you mean by stopping it is giving a error? If so the checksum the cd
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
If not then I have installed on low memory systems and I thought they had froze or stopped and it takes a long time. I installed on a 128mb system yesterday and it tool over three hours. So if you are not getting errors from the installation I suggest wait until you do. Also check the disc! Good Luck! :KS
Quote from the Xubuntu site
```
Minimum system requirements

To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only required you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 64 MB RAM, but it is strongly recommended to use at least 128 MB RAM.
```

---

### Post by muckvoc on 2007-10-16
thanx for the answer,

i did the checksum, it's ok. i do think i meet the requirements as well. it does give an error but nothing like a code.I'll do it again:

I install in txt mode
it starts
it does the keyboard
scans the cd- rom
loads ad. comps
now there it is:


"problem reading data from cd-rom. make sure it's in drive. check integrity. retry?" done - same.

installation step failed: load installer components from cd

i end up in the menue...

i could try an older version: 6.06.01......

any other suggestion? thanks!!!

---

### Post by muckvoc on 2007-10-16
ohhh sorry, done the checksum again and it is wrong,

problem solved i guess, thanks a lot!!!

---

### Post by muckvoc on 2007-10-16
ok next stage:

the checksum is ok when dowloaded, but turns wrong when burned to cd. i am using the infra recorder as suggested at ubuntu.com.
(i'm downloading and burning with a different laptop)

the installation with ubuntu 7.04 just freezes (waited 4hrs now) and shows no error message so far.
installation with xubuntu feistyfawn stops at loading the installation components as described above.
in both cases the cd integrity check from the menu shows a problem in the checksum.

i've burned 6 cds with different speed... so far.

help. how can the checksum be wrong every time?
what am i doing wrong here?:confused:
thanx

---

### Post by muckvoc on 2007-10-16
here is the error message:

[465.320000] SQUASHFS error: zlib_inflate returned unexpected result 0xfffffffffd, srclength 65536, avail_in 336, avail out 65536


i don't have any idea what this means, there's more messages like that...:(

help would be great!!!!!!!!!!!

---

### Post by overdrank on 2007-10-16
> **muckvoc said:**
> here is the error message:

[465.320000] SQUASHFS error: zlib_inflate returned unexpected result 0xfffffffffd, srclength 65536, avail_in 336, avail out 65536


i don't have any idea what this means, there's more messages like that...:(

help would be great!!!!!!!!!!!

HI and that error does coincide with the checksum. Have you tried a different mirror for the download.

---

### Post by muckvoc on 2007-10-16
yes, i've tried the german, france and europe ones

thanks for the quick reply!

when checking the sum after the download it is ok, just the burned disc used on the 2. laptop is corrupted.

i'am downloading once more.

by now i am thinking it might be either the burning or the reading device......possible?

---

### Post by muckvoc on 2007-10-17
ok it is an checksum / corrupted file problem, I'll start a new thread on the topic...... and call this one closed.
downloaded again (different mirror) and it is corrupted again.

Thanks for the help to overdrank!!

---

