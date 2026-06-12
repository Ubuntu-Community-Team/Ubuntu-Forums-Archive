---
title: "automatix2"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by timsflhtc on 2007-01-02
i'm a newbie with ubuntu. i've been reading a lot on this site and finally installed kubuntu 6.06. love the way it works and helps me understand how programing goes.;)  i've installed automatix2 both thru command and download (different times). each time i am able to get the software i want or need to use, then when i shutdown and reboot, go to use automatix, it claims i have kubuntu 6.01 (this is good) and the version of auto is for kubuntu 6.1 (bad):-k  and shuts down the program. so i will uninstall the 6.1 version and reload the 6.06. i am still able to run anything else i want to except dvd movies. i'm tackle that problem later. my system is from microcenter, ecs mainboard with 64bit amd, 1 gig ram, 6200(?) series geforce pcie video card. all hardware was recognised and installed. i can get more specs on the machine wednesday as i am at work right now. my wife asked me "you're never satisfied with your puter are you?!?" then she played with it a little and said when i get the bugs worked, would it work on hers? thanks for your help and advise. this seems like a great group here.:D

---

### Post by taurus on 2007-01-02
Can you post your /etc/apt/sources.list here from a terminal?

```
cat /etc/apt/sources.list
```

---

### Post by timsflhtc on 2007-01-02
i can do it wednesday early morning as i am at work right now. thanks. do i open a terminal and type in what you have asked for?

---

### Post by taurus on 2007-01-02
Yes, open a terminal and paste the output of that command here.  In other words, I want to see what you have in /etc/apt/sources.list because I bet you have edgy in there instead of dapper for automatix!!!

---

### Post by timsflhtc on 2007-01-02
:-k so, you think i have edgy instead of dapper for automatix2? could be, it'll be 1 am central when i can check. i'll let you know. thank you.

---

### Post by Quillz on 2007-01-02
Do you recall if you install 6.06 or 6.10? If the former, you have Dappy Drake. If the latter, you have Edgy Eft.

---

### Post by taurus on 2007-01-02
If you have edgy in there, then replace it with dapper and update your list and install automatix2 again...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude install automatix2
```

p.s.  1 AM central time would be like 2 AM here so I am probably in a dreamland then...  :twisted:

---

### Post by Sef on 2007-01-02
> ecs mainboard with 64bit

Did you install the 32-bit version of Kubuntu or the 64-bit version of it?

---

### Post by timsflhtc on 2007-01-02
no to the 64bit, read that was not stable. originally installed automatix2 for dapper and allowed it to update itself and all worked well. upon reboot and start of auto, it claims to be edgy not dapper. will check and set up post when i get home. i have originally installed dapper, due to longer support (?), i thought that is what i read. will check my dvd in the morning. downloaded dapper alternate dvd 3.4 gig. install went well.

---

### Post by timsflhtc on 2007-01-03
Sorry about the miss quote, I am running 6.06 and Automatix claims to be for 6.1

Well, here is the post:


deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
#
# deb cdrom:[Kubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807)]/ dapper main restricted


deb cdrom:[Kubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807)]/ dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

#AUTOMATIX REPOS START

deb [http://kubuntu.org/packages/amarok-143](http://kubuntu.org/packages/amarok-143) dapper main

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://kubuntu.org/packages/kde-355](http://kubuntu.org/packages/kde-355) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
#AUTOMATIX REPOS END
tim@ubuntu:~$   

On kubuntu forum, I was asked if I updated automatix thru adept. No I let auto take care of it.:confused: :confused:

---

### Post by taurus on 2007-01-03
You need to remove these two lines from your /etc/apt/sources.list since you are using Dapper, not Edgy (the second line just a duplicate of the next line in /etc/apt/sources.list...

```

deb http://www.getautomatix.com/apt edgy main
deb http://www.getautomatix.com/apt dapper main

```
Save it and update your list again.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by timsflhtc on 2007-01-03
Wow! Now that I know what I am looking for, I found in Adept that Edgy was there as a repository. i removed it and will uninstall Auto and reload to see what happens. Thanks for the eye opener.:p :p

---

### Post by cllsr on 2007-01-03
Is anyone else having problems getting to [http://www.getautomatix.com](http://www.getautomatix.com) ?

---

### Post by theadventuresofanidealist on 2007-01-03
cannot acess getautomatix either.the site is prob down. is there any other links to get automatix2?

---

### Post by arnieboy on 2007-01-03
The automatix host has been causing problems in the recent past. We used to feel we were getting good value for our money but we might need to rethink on that one. We are working with our hosts to resolve the issues as of now.

---

### Post by timsflhtc on 2007-01-03
I am trying the update you suggest:

tim@ubuntu:~$ gksudo gedit /etc/apt/sources.list
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
sudo: gedit: command not found
](*,) ](*,)  I realized I cannot have Adept and a Terminal open together as it cannot lock the program and finish. Now I have run your suggetion to remove: deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
and run: sudo aptitude update
sudo aptitude upgrade. Now it does not show upgrade to Edgy. :KS :KS :KS 
All looks well now.
Now to work on running DVDS!!
THANKS I am starting to enjoy this. But driving my wife nuts.

---

### Post by arnieboy on 2007-01-03
Update: The AX server is back up.

---

### Post by timsflhtc on 2007-01-03
:) :p  All's well!! Everything is working, right down to my DVD!!!!

---

