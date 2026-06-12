---
title: "oh the humanity!(help with automatix needed)"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by dougmwpsu on 2006-07-04
it's just one problem after another here... 
after finally getting my internet kinda working.. i tried running automatix to get all the important software. it fails on the truetype fonts becuase it cannot connect to any of the(working) servers. i think it is an instance of this error:

[http://ubuntuforums.org/showthread.php?t=76655&page=2](http://ubuntuforums.org/showthread.php?t=76655&page=2)

now, aptget is stuck on the truetype installation.  when i try to run automatix or a  dpkg related command it gives me this message:

dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
 
when i do that, the true type install tries to finidh again, and i'm back where i started. there were some instrucrtions in that linked thread on how to manually install the fonts... will i even be able to do them without dpkg working? if i am, and if it will clear up my problem.. how on earth do i do step 3?

   1. Get the following files from a friend, another pc or download manually from the internet by some means (like in my earlier post above):-
      andale32.exe comic32.exe impact32.exe verdan32.exe
      arial32.exe courie32.exe times32.exe webdin32.exe
      arialb32.exe georgi32.exe trebuc32.exe
   2. Create the following directory and put them into it: /tmp/mstt/
   3. Manually launch the postinstall script, telling it to use your local copy:
      /usr/sbin/update-ms-fonts /tmp/mstt
   4. Remove your temp directory
      rm -rf /tmp/mstt/
   5. To ensure apt/dpkg is happy rerun
      apt-get install msttcorefonts

---

### Post by enyaw on 2006-07-04
[QUOTE=dougmwpsu]it's just one problem after another here... 
after finally getting my internet kinda working.. i tried running automatix to get all the important software. it fails on the truetype fonts becuase it cannot connect to any of the(working) servers. i think it is an instance of this error:

[http://ubuntuforums.org/showthread.php?t=76655&page=2](http://ubuntuforums.org/showthread.php?t=76655&page=2)

now, aptget is stuck on the truetype installation.  when i try to run automatix or a  dpkg related command it gives me this message:

dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
 
when i do that, the true type install tries to finidh again, and i'm back where i started. there were some instrucrtions in that linked thread on how to manually install the fonts... will i even be able to do them without dpkg working? if i am, and if it will clear up my problem.. how on earth do i do step 3?

   1. Get the following files from a friend, another pc or download manually from the internet by some means (like in my earlier post above):-
      andale32.exe comic32.exe impact32.exe verdan32.exe
      arial32.exe courie32.exe times32.exe webdin32.exe
      arialb32.exe georgi32.exe trebuc32.exe
   2. Create the following directory and put them into it: /tmp/mstt/
   3. Manually launch the postinstall script, telling it to use your local copy:
      /usr/sbin/update-ms-fonts /tmp/mstt
   4. Remove your temp directory
      rm -rf /tmp/mstt/
   5. To ensure apt/dpkg is happy rerun
      apt-get install msttcorefonts[/QUOTE]

I really don't know how to help except to point you toward ArnieBoy.

Have you followed the ArnieBoy Automatix install procedure.  Try the following link.   Hope this helps.:) 

[http://www.ubuntuforums.org/forumdisplay.php?f=77]("http://www.ubuntuforums.org/forumdisplay.php?f=77")

---

### Post by xael on 2006-07-04
Much of the software installed by Automatix can be removed by "sudo apt-get remove packagename".

---

### Post by enyaw on 2006-07-04
[QUOTE=xael]Much of the software installed by Automatix can be removed by "sudo apt-get remove packagename".[/QUOTE] 

Great follow up xael.   arnieboy has great direction for just that purpose.  It seems I'm always installing and removing something so I use the following often.

[http://www.ubuntuforums.org/forumdisplay.php?f=77]("http://www.ubuntuforums.org/forumdisplay.php?f=77")

---

### Post by cowley on 2006-07-04
hi, i dont know if you r still having problems but around 6 hrs ago i was trying to install things via automatix and things were just not right, tho ok now.  i wonder whether there was actually a problem on the automatix side.  try again and see how you get on

simon

---

### Post by dougmwpsu on 2006-07-05
i already figured out how to install the fonts manually just by putting them in the font diectory.  once i did that, the corefont package installer stopped messing up my system and reported that everythign was a ok.

one more bug squashed!

---

