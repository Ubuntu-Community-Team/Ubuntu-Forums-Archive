---
title: "partion problems on iBook G4"
date: 2007-02-14
forum: Apple PPC Users
---

### Post by mr tim esquire on 2007-02-14
ive made a fresh install of Tiger on my i book g4 and left space for the ubuntu install
Using the partion tool on the Ubuntu 6.01.6 install CD i make seperate ubuntu and swap partions of 6gb and 1gb. Ive tried using ext3 and hfs for the '/' bit the installer starts but keeps telling me 'no NewWorld boot partition found the yaboot boot loder requires an Apple_Bootstrap partition using the hfs file system'
so i go back to the partitioner and try with this third partition as a 128mb segment which comes before the tiger install but keep getting the same problem with install
can any one help
please

---

### Post by hellstead on 2007-02-15
what i did was:
resize my osx partition leaving a 10gb 'unallocated' region for ubuntu
then i just let the ubuntu installer assign the partitions.
it's been a while since i did it, but i do remember the phrase "use largest free space" or something like that.

i think you can delete the partitions you've made from within the installer, and then let it do all the nerdy stuff for you :D

good luck!

---

### Post by mr tim esquire on 2007-02-15
Thanks that worked great!
i used the partioner to delete the partitions i had previously made for ubuntu, then went back and selected 'use the largest free partition'

---

### Post by grazie on 2007-02-15
Using the inslaller to set up your partitions is nearly always the best way for first timers. Later on, once you've got to know Linux a little better, you can resize and/or add partitions and the bootstrap partition will still be there.

---

