---
title: "help !   I can't enter the  X windows after installing the  ubuntu 6.0.6"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by sugartown on 2006-10-16
I  installed  the  Ubuntu 6.0.6 on  my computer .BUT I just can't enter  the  X windows.all  I can  do  is  stay  in the text mode . the  graphical  card of  my  computer is ATI X700  
it is make me  down  every time  I  restart the computer hoping  sth miracal would come up  , coz this  warning appears : 
    Fail to  start the  X server (your graphical  interface ).It is  likely that it is  not  set up  correctly.Would you  like to  view the  X server output  to  diagnose the  problem? 

choose yes or no ?
both tried,but both end with  text mode welcome me  :confused:

PS :the  sysem note that :
(==)using config file : "/ etc/X11/xorg.conf"
(EE)no  devices detectid.
Fatal server error:
no screens  found


can  anyone  help me   ? 

great thanx !!!

---

### Post by junglepeanut on 2006-10-16
Search the posts for how to install the (edit) ATI driver, after running this so you can at least search in a weird resolution on the computer you are hoping to fix.

sudo dpkg-reconfigure xserver-xorg

choose vesa instead of ati.

Then answer the other questions with which ever sounds best, I would use simple for the last part as it is best if you dont know everything about your monitor.

---

### Post by maneesh77 on 2006-10-16
Did the live CD work ok before you installed??

I had a problem with the Xserver . ubuntu went straight to command line( it's scary for newbies like us)

try this command

sudo dpkg-reconfigure xserver-xorg

and follow the instructions and tell what happens us

---

