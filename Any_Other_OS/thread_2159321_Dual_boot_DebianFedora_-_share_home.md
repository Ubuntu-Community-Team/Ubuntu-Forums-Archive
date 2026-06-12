---
title: "Dual boot Debian/Fedora - share /home?"
date: 2013-07-02
forum: Any Other OS
---

### Post by kabukiM0n0 on 2013-07-02
Hey chaps

Quick question. 

I'm attempting to install Fedora along side my #!
Reading a little about what would happen if I used the same /home ... well yup, that's not wise - unless I want to crunch my system. Anyway, from what I read /shared is the way to go.
Can this be done without having to reinstall and start from scratch?

Thanking you alls. 

Km

EDIT: thinking about it ... shouldn't this go in the 'other OS' section :/ apologies.

---

### Post by oldfred on 2013-07-02
Moved to otherOS.

Depends on versions. I think Fedora changed to use 1000 as UID for first user. It used to be 500 and that caused issues unless you manually changed it.
       Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

    

 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

### Post by AdamWill on 2013-07-02
> **kabukiM0n0 said:**
> Hey chaps

Quick question. 

I'm attempting to install Fedora along side my #!
Reading a little about what would happen if I used the same /home ... well yup, that's not wise - unless I want to crunch my system. Anyway, from what I read /shared is the way to go.
Can this be done without having to reinstall and start from scratch?

Thanking you alls. 

Km

EDIT: thinking about it ... shouldn't this go in the 'other OS' section :/ apologies.

I'm not quite sure what you're asking. You seem to have decided not to use the same /home (which I'd certainly agree with), but then you say "from what I read /shared is the way to go." What do you mean by this exactly? /shared is not a standardized or commonly-recognized path AFAIK. Sounds like you possibly read about someone's personal 'innovative' approach and assumed it was a standard thing?

---

### Post by ajgreeny on 2013-07-02
As long as the user's UID and username is the same in both OSs it is probably best to make links from the data folders (Documents, Music, Photos, Pictures, etc) of the separate /home partition of debian, if you have it separate, to the /home of fedora, and in the case of fedora you possibly don't need a separate partition as the amount of data will be very small as it will in reality be on debian, not fedora, so space used will be very little.

To do this you will need to automount the separate /home partition of debian in /mnt/debian in fedora, then delete any same named folders in fedora's /home folder, and finally run command ```
 ln -s /mnt/debian/home/*username*/Documents /home/*username*/Documents
``` from fedora.  You can also try the same for the folders used for config of apps like firefox, ie ~/.mozilla but if the versions of FF differ you could have minor problems.

---

