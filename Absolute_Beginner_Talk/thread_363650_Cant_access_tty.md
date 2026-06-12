---
title: "Cant access tty"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by Nickelodeon on 2007-02-17
I currently have Windows Xp installed and I want to dual boot. I'm a complete beginner to Linux (though very experianced with Windows) and I thought I'd try out Ubuntu. 

Except *that* only lasted a few minutes - when I try to boot from the live CD it says: "Cant access tty"

What am I doing wrong?

---

### Post by Nickelodeon on 2007-02-17
Did I post this in the wrong place?

---

### Post by mikewhatever on 2007-02-17
The place is right, it's just possible that at the moment, nobody knowing the answer is around. Meanwhile, try searching the forums for that error and see what you can find.

here you go :)  [http://ubuntuforums.org/search.php?searchid=14734977](http://ubuntuforums.org/search.php?searchid=14734977)

---

### Post by Nickelodeon on 2007-02-17
Starnge thing is this problem props up on many places, yet no definitive answers ? I know lots of people have had similar problems, but .....

---

### Post by Nickelodeon on 2007-02-19
Bump. Anyone?

---

### Post by clevedonal on 2007-04-01
I had a 'cant access tty, job control turned off" problem too, in my kubuntu/dapper drive. 
I got my win2000 partition working again using
(win2000 setup disc>setup/instal l> repair > CL: 'fix mbr' worked). 
i then reinstalled Grub, which came up but boot halted on 'cant access tty etc'
i was going to wipe dapper and install edgy, but, on one of the boards here i found a recommendation for 'Qparted' as a better partition tool than the one that comes with Ubuntu. 
Ran 'Qparted' live cd, and one of the options is 'check/repair filesystem', i ran this first and it reported that it had been successful. 
Exit/reboot from Qparted and i am now able to log in normally again. 

i dont know if this will be of help to anyone, but it might be worth a try?

al

---

