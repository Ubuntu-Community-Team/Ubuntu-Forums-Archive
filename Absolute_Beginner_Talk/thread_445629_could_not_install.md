---
title: "could not install"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by jk_bscomp on 2007-05-16
hello everyone,,,,I hope you could help me with my problem coz i am having trouble in installing in ubuntu ....I dont know what is the problem but everytime i install smthing in my terminal declaring  
   
         sudo apt-get install <application to be installed>
 
it always flag a message of 

         E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
         E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?

    I hope you could help me with this one.....Pls help me to what procedures i should do so that i can able to download again........


            Your help is highly appreciated....

---

### Post by Najand on 2007-05-16
You cannot use two package manager at the same time. Close Synaptic before using apt-get in terminal.

---

