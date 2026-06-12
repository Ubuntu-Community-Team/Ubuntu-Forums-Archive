---
title: "Something i notice during Installing 7.04"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by futureal2032 on 2007-10-02
[B]hey...while i was installing Ubuntu 7.04 i noticed something while partitioning the disk. Thought i would share it with people.

here is step by step:[/B]

[COLOR="Red"]Step 1. I clicked on "Install" i con on the desktop ..after booting from Live CD.
Step2. Ok i setup the locale, keyboard layout, time zone etc.
Step3. I came to the disk partition tool..i chose "Manual Configuration" option.[/COLOR]

[COLOR="Blue"]""" I had kept 10.5 GB of free, unpartitioned disk space for Ubuntu on my hard disk.
Usually when i used Redhat or Fedora previously on my system.
i used to do following partitions.

100Mb         /boot
2GB             /
3GB             /usr
5gb             /home
500mb        /swap    * I have 256MB RAM

and it used to work fine... as i have a tendency of downloading lot stuff like music or videos.
""""[/COLOR]

S[COLOR="Red"]tep4. So naturally i decided to use the same partition scheme as above for Ubuntu too.

The partition tool successfully created swap, /boot and / patitions.

but it shows the remaining space as unusable. and does not let me use the remaining apsace for any kind of partition (not even fat or fat32)
[/COLOR]
I tried it many times and in many ways (i.e. creating swap first or creating / first etc.) but no use.

[COLOR="Blue"]well.. so finally i created

100Mb    /boot
500Mb    swap
and rest of the space as /
[/COLOR]
[B]and installed Ubuntu 7.04.. its running without problems.
But i want to know if anyone else has come across this?

anyways just wanted to inform abt this.

[/B]

---

### Post by hyper_ch on 2007-10-02
did you use primary or extended partitions?

You can only have up to 4 primary ones... and if you need more partitions, one of those needs to become an extended one so that you can create within more partitions.

---

### Post by Jose Catre-Vandis on 2007-10-02
Suggest you use Gparted or Parted Magic CD to create partitions in advance of install then reassign them in manual partitioning

Personally I only ever bother with / and swap, but it's up to you :)

---

### Post by hyper_ch on 2007-10-02
jose:

Well, a seperate /home is recommended and a seperate /boot is required if you want to full encrypt your disk.

---

### Post by futureal2032 on 2007-10-02
well...
1. i dont have more than 4 primary parittions on my disk...
2. Since it wont' let me create any kind of partition, primary or extended in the remaining space terming it "unusable".
3. yes i even tried creating only /boot as primary and / as extended. still faced the same problem.
4. I always prefer having /boot (for security and system repair reasons) and /home for my files (it takes the burden of / and runs system smoothly)

---

### Post by hyper_ch on 2007-10-02
Can you post your partition scheme?

---

### Post by Jose Catre-Vandis on 2007-10-03
> **hyper_ch said:**
> jose:

Well, a seperate /home is recommended and a seperate /boot is required if you want to full encrypt your disk.

A default install of ubuntu doesn't give you a separate /home, and no-one said anything about encrypting your disk, however, I take your point :)

---

### Post by hyper_ch on 2007-10-03
default doesn't mean it's the best thing to do ;)

---

### Post by Jose Catre-Vandis on 2007-10-07
could get tricky if you have multiple installations (I have 3xlinux and 2xwindows)
that would mean @14 partitions on my PC instead of 6:)

---

