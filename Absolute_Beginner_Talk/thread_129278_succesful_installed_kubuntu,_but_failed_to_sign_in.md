---
title: "succesful installed kubuntu, but failed to sign in desktop"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by wcks48 on 2006-02-13
As said, all process still okay, but until the user sign up and sign in to kubuntu, the whole thing stucked there. the base-system keep on continue the screen of add new user after i key in the first password (as root if not mistaken). so, now i cannot enter the desktop environment. even after returned to the console but cannot make any new user add in too.. 
when back to the restart with recover mode, it shows error like "name resolution". 

urgently need help, pls.. thanx a lot.

---

### Post by bscbrit on 2006-02-13
There is no 'root' password.  When you log in, simply use the user name that you gave during the installation and the password that you specified at that time.

If it doesn't work, restart ubuntu in Recovery Mode (at the boot menu select your kernel and 'Recovery Mode' which will get you to the command line.  Enter

passwd <username>

and enter another password.  If you then reboot (using 'reboot' :-D  ) you should then be able to log on with your <username> and the new password that you specified.

---

### Post by wcks48 on 2006-02-14
Inside the console i can log in as root. But when checking the contains inside the HOME directory, nothing inside. I suspect the cause is the error occur when the system writng data of user into the HOME directory. 

another possible cause might be the partition i had done. previously, while running windows, i had 2 partitons of the single hardisk. i remained the existing WINDOWS drive and create 3 partitions from the the other part which is only used to store files. among the 3 partitions, one is for "/" root directory, one is swap, and the last is just purposely for storage that  hopefully can be accessed either from windows or kubuntu.  As i remember, the last parttion had i make it to the "\home". so will it the answer that the user data wrongly stored into the third directory? 

why the system keep on ask me to type in the user name and pasword although i had enbter it many times?
:confused:

---

### Post by erlyrisa on 2006-02-14
I maybe able to shed some light on this....

is your /home mount piont on the windows (fat32/fat16) partition. Normally linux doesn't have too much problems with fat32, however insecure, as a native file system : native being that linux writes alot more info to each file, and in a different manner, than what windows does., and if your home partition has been mounted to a fat32 filesystem, some info, like ownership or permissions maybe missing.
-I didn't have too many problems with my install - putting the home mount on a fat32 - maybe you do though?

---

### Post by bscbrit on 2006-02-14
Please cut and paste the contents of your /etc/fstab file, and the results of 'df' being run from the commandline into your next post.

---

### Post by runic on 2006-02-14
Hi, 
I have similar problem after installed Ubuntu 5.10 on drive which has 4 partitions, two NTFS, one for ubuntu and one for swap file. Installation went fine, but after I supply user name and password computer "locks", I&#8217;ve reinstalled ubuntu for second time but results are the same.

---

### Post by wcks48 on 2006-02-15
try not set the partition as \home. i had tried to let the partitioner set the swap and partitions automatically for me. it's ok now. but sadly saying, my third partition cannot be scanned both in windows and kubuntu, so my remaining space had gone... until now, no news also.

---

