---
title: "In the Dark"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by thedivvyman on 2007-05-19
Hi -  when  playing  either  Supertux  or  Frozen  Bubble,  after  about  ten  minutes  of play  the  screen  goes  dark,  It  seems  to last  about  ten  to  fifteen  seconds,  at  which  point  things  return  to  normal.  This  is  repeated  after  another  15  to  twenty  minutes.
 At  first I  thought  it  was  part of  the  game  in  Supertux,  but  it  does  it  when  playing  Frozen  Bubble  too.
Anyone  any  ideas?

Thanks

---

### Post by mahy on 2007-05-19
What's your graphics card and your driver?

---

### Post by jordanmthomas on 2007-05-19
It sounds like your screensaver is kicking in.
Try turning off the auto-screensaver (system --> preferences --> screen saver) and see if it still happens when you're playing.  

screensavers tend to ignore keys you press while playing sdl games like that.

---

### Post by thedivvyman on 2007-05-19
Thanks  for  response.
Radeon 9600  graphic  card,  don't  know  about  the  driver  though.
Don't  think  its   the  screen  saver,  cos  it   goes  dark  slowly,  as  though  you  were  turning  a  dimmer  switch,  if  you  know  what  I  mean.  I  will  try  turning  screensaver  off  to  see  if  it makes  any  difference.
I  can  live  with  the  problem  -  thought  it  might  be  a  common  prob.

Thanks

---

### Post by jordanmthomas on 2007-05-19
gnome-screensaver does dim as it goes to its screensaver (just for the record)

To find the driver you're using, post the output of
```
cat /etc/X11/xorg.conf | grep Driver
```
You should be looking for either ati, radeon or fglrx

---

### Post by thedivvyman on 2007-05-19
brian@brian-desktop:~$ cat /etc/X11/xorg.conf | grep Driver
        Driver          "kbd"
        Driver          "mouse"
  Driver        "wacom"
  Driver        "wacom"
  Driver        "wacom"
        Driver          "ati"
brian@brian-desktop:~$


Thanks

---

### Post by jordanmthomas on 2007-05-19
You're using the (open source, good for you) ati driver.  I'm not sure what this means in relation to your problem or if there's a solution for it because of the driver you're using.  I guess we'll just have to wait for mahy to make a return.

---

### Post by thedivvyman on 2007-05-19
OK -  thanks  -  I'll  turn  off  the  screensaver  and  let  you  know  if  it  makes  any  differnce.

Thanks  to  all

---

### Post by thedivvyman on 2007-05-19
Hi-  just  tried  both  games  with  the  screensaver  off -  problem  solved.
Thanks  to  one  and  all.
Brilliant  forum,  friendly,  quick  replies  and  very  helpful -  thanks  once  again.

---

