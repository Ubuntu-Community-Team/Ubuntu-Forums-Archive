---
title: "Ubuntu doesn't recognize CD-RW drive."
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Metric on 2007-05-19
Hello. I have two CD drives. A liteonit 32x12x40x CD-RW drive, and a DVD-ROM drive. None of my programs recognize the liteonit drive. I tried burning a CD and playing an audio CD, both tries went to my DVD Drive. Can anyone help me figure out how to get my CD-RW drive to work? I really need to burn a CD. 

Thanks :KS

---

### Post by Happy_Man on 2007-05-19
Could you post the output of ```
cat /etc/fstab
```?

---

### Post by Ozeuss on 2007-05-19
is the drive mounted at all? does it show when you open Places->Computer ?
check the content of /etc/fstab.

---

### Post by Bachstelze on 2007-05-19
First things first, guys...

Is the drive *recognized* at all ?

```
dmesg | grep CD
```

---

### Post by Metric on 2007-05-19
Yes, It is recognized in Places>Computer, but I'm pretty sure that's it.

---

### Post by Bachstelze on 2007-05-19
Then it should just be a matter of how your burning application is configured. What application is it, anyway ?

---

### Post by Metric on 2007-05-19
GnomeBaker

---

### Post by Bachstelze on 2007-05-19
I've little to no knowledge of it so I'm afraid I can't help you. I suggest you use k3b instead, it is usually considered much better.

---

### Post by Metric on 2007-05-19
I installed K3B but when I opened it, It said no CD/DVD writer found... :(

---

### Post by Bachstelze on 2007-05-19
Please run the command I posted above and paste the results.

---

### Post by Metric on 2007-05-19
> [  166.529780] scsi 2:0:1:0: CD-ROM            LITE-ON  DVD SOHD-16P9SV  F$01 PQ: 0 ANSI: 5
[  166.647797] Uniform CD-ROM driver Revision: 3.20
[  166.648071] sr 2:0:1:0: Attached scsi CD-ROM sr0
maku@maku-desktop:~$ 


:)

---

### Post by Bachstelze on 2007-05-19
Hmm, SCSI ?

```
ls /dev/scd*
```

what does that give ?

---

### Post by Metric on 2007-05-19
> /dev/scd0
'-')/

---

### Post by Bachstelze on 2007-05-19
Then in k3b, go to Settings > Configure k3b, then in the Devices section. If your burner isn't autodetectd, click the Add Device button and enter /dev/scd0 in the field. Click OK and see what happens...

---

### Post by Metric on 2007-05-19
> Could not find an additional device at
/dev/scd0

D;

---

### Post by Bachstelze on 2007-05-19
Yeah, actually I ge the same error here, though my burner works fine. Then I don't know, I'm afraid...

---

### Post by Metric on 2007-05-19
Oh my. Well, thanks a lot for trying.

---

