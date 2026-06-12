---
title: "[SOLVED] trying to burn a  SystemRescueCd"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by broekskw on 2008-02-05
going to try to burn is SystemRescueCd from terminal and following direction from this site but (ok call me old)

Burning with cdrecord is easy. First, type cdrecord -scanbus in order to get the identifier numbers of your device. Then, type cdrecord dev=x,y,z -v systemrescuecd-x86-x.y.z.iso in a console. 

 1001,0,0 100100) 'JLMS    ' 'DVD-ROM LTD163D ' 'GHR6' Removable CD-ROM
        1001,1,0 100101) 'ATAPI   ' 'CD-RW 48X16     ' 'A.QZ' Removable CD-ROM
so did that command and got this output,now what is the identifier number of this cd-r drive??
and then how do i burn this iso image to cd-r, have downloaded the file with a .exe (wget.exe)
but this command will not work for me ( cdrecord dev=x,y,z -v systemrescuecd-x86-x.y.z.iso)

all this terminal talk i find that i have a hard time to follow, most of the time i just cut and past others commands in and all works out most of the time, but i need to sit down and try to get a grip on this programming stuff:guitar:

---

### Post by Linux_Man on 2008-02-05
I assume it is an ISO image and if so then just burn it with K3B/Brasero and it should work fine, no need for the terminal stuff if its an ISO it is just there because it will work on just about every version of Linux from Gentoo to Ubuntu.

---

### Post by broekskw on 2008-02-05
ok am i missing something here, on this web site i tells you to down load the SystemRescueCd iso image with wget program, so i downloaded the wget.exe file but now i am lost, what is this wget.exe file and how do i open it , then dose this file download the iso image??:confused:

---

### Post by Linux_Man on 2008-02-05
Ok, seems like the writer had every intent in confusing you :lolflag: Go here [http://sourceforge.net/project/showfiles.php?group_id=85811&package_id=88964](http://sourceforge.net/project/showfiles.php?group_id=85811&package_id=88964) and download the  	systemrescuecd-x86-0.4.3.iso file and burn it using that program, I got the link from [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download) just so you know (with all the talk about malicious commands I thought I'd better be safe)

---

### Post by broekskw on 2008-02-05
thanks Linux_Man:popcorn: how come some site do that, any how thanks again:lolflag:

---

### Post by seventhc on 2008-02-05
I think you downloaded the win32 version of wget. Do you have the iso image or only the exe? The exe won't do anything if you're using ubuntu.

---

### Post by broekskw on 2008-02-05
Linux_Man thats the smae site i tried to down load from,could not find the iso image link:confused:

better clean my glasses:lolflag:

---

### Post by Linux_Man on 2008-02-05
Some sites do that to make it be more platform independent so it will work with every Linux (GNU) system, really all it does is be confusing as most distros these days have graphical CD burners and such all the writer was telling you to do is how to do those things via a terminal which confuses some if not most people.

---

### Post by Linux_Man on 2008-02-05
Ok, when you get to the Sourceforge site, your going to want to click on the 0.43 text, then it will expand and show you the .ISO link, click on it, save it and burn it using GnomeBaker, K3B or Braseo.

---

### Post by seventhc on 2008-02-05
here is the iso image :) [http://downloads.sourceforge.net/systemrescuecd/systemrescuecd-x86-0.4.3.iso?modtime=1200868245&big_mirror=1](http://downloads.sourceforge.net/systemrescuecd/systemrescuecd-x86-0.4.3.iso?modtime=1200868245&big_mirror=1)

---

### Post by Linux_Man on 2008-02-05
Thanks for posting that, I would have but I wasn't sure if that would work to download the ISO image because of the mirror configuration.

---

### Post by broekskw on 2008-02-05
thanks seventhc and Linux_Man, with this i should be good to go for anything that comes up
1-gparted cd
2-supergrub boot disc
3-systemrescuecd

:lolflag:

---

### Post by seventhc on 2008-02-05
@Linux_Man : you're welcome :)

@broekskw : Glad you got it:)  Hopefully you won't have to use these tools if your lucky.  :lol: :popcorn:

maybe mark this thread as solved. ;) (I think you do it up top by tools. )

---

