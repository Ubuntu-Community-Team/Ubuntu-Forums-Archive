---
title: "ubuntu 6.10 installition is a nightmare!!"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by gossipsux on 2007-03-18
hello
i am an absolutely new user. 

i am trying to install ubuntu 6.10 but i cant!

my laptop uses
ati mobility radeon x700 256mb and it crashes..

i boot from cd
from the menu i choose install or open
ubuntu logo appears and like wondows a bar is loading...

than the screen goes totally black and an opening sound comes however the screen seems pure black.

i tried also the the other option open with vga support or sthg i cant remember anyway always the same.... ati x700 crashes...

i google a lot and after
i press
ctrl alt f6 and a console appears. 
like ms dos.

than i dont know what to do...
how can i continue..

i have already made a small 5gb partition for my ubuntu but i cant install it...
if you help me, i will be very gladfull

thank you so much

---

### Post by overdrank on 2007-03-18
> **gossipsux said:**
> hello
i am an absolutely new user. 

i am trying to install ubuntu 6.10 but i cant!

my laptop uses
ati mobility radeon x700 256mb and it crashes..

i boot from cd
from the menu i choose install or open
ubuntu logo appears and like wondows a bar is loading...

than the screen goes totally black and an opening sound comes however the screen seems pure black.

i tried also the the other option open with vga support or sthg i cant remember anyway always the same.... ati x700 crashes...

i google a lot and after
i press
ctrl alt f6 and a console appears. 
like ms dos.

than i dont know what to do...
how can i continue..

i have already made a small 5gb partition for my ubuntu but i cant install it...
if you help me, i will be very gladfull

thank you so much

Hi try the alternate cd here
[http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/)
make sure you burn the cd here
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Hope this helps and good luck!

---

### Post by gossipsux on 2007-03-18
> **paul capps said:**
> Hi try the alternate cd here
[http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/)
make sure you burn the cd here
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Hope this helps and good luck!


i will try thank you so much
if it doesnt work i will tell again...

---

### Post by gh0st on 2007-03-18
Another thing to try might be the "Safe Graphics Mode" option on the Live CD menu, I've seen that work before with troublesome video cards. Once the main system is installed through safe graphics often the card will work when booting the newly installed system.

You might have tried this already but I just thought I'd mention it anyway. Worth a go, good luck :)

---

### Post by gossipsux on 2007-03-18
> **gh0st said:**
> Another thing to try might be the "Safe Graphics Mode" option on the Live CD menu, I've seen that work before with troublesome video cards. Once the main system is installed through safe graphics often the card will work when booting the newly installed system.

You might have tried this already but I just thought I'd mention it anyway. Worth a go, good luck :)

thanx but i have already tried it
nope doesnt work :( 

thanx anyway

---

### Post by linuxjerk on 2007-03-18
Boy you got that right. After about 10 attempts I finally got it to install. Then found out the mouse doesn't work.
Come to find out that 6.1 doesn't support serial mice. Go figure!!
There is some fix but I haven't figured it out yet. 
Yes I could get a use mouse. But why should I. Windows didn't require that????????:confused:

---

### Post by gossipsux on 2007-03-18
before i try the alternate cd
i made googling alot and came to a point...

when the screen goes black
ctrl alt f5 makes me jump to console..

than i write
sudo dpkg-reconfigure xserver-xorg

a blue menu appears and asks me to select the video card manual or automatic. i have chosen manual and select vesa or vga in different attemps... because people says choose vesa than after the installition you can config your video card easily...

than asks me about my monitor etc etc
enter enter enter

than again jumps back to console ans saves the config...

than i write
startx to continue

however it says

FATAL ERROR
server is already active for display 0
if this is no longer running 
remove....

i think in the beginning something like this also appears
error in locking authority

file /home/ubuntu/.Xauthority.....

ANYONE UNDERSTANDS?
pls help me

I AM GONNA INSTALL UBUNTU
I AM REALLY TOUGH ON THIS!

thank you so much

---

### Post by gossipsux on 2007-03-18
:popcorn: if you answer :D

---

### Post by gossipsux on 2007-03-18
:confused: :confused:

---

### Post by gossipsux on 2007-03-18
> **gossipsux said:**
> before i try the alternate cd
i made googling alot and came to a point...

when the screen goes black
ctrl alt f5 makes me jump to console..

than i write
sudo dpkg-reconfigure xserver-xorg

a blue menu appears and asks me to select the video card manual or automatic. i have chosen manual and select vesa or vga in different attemps... because people says choose vesa than after the installition you can config your video card easily...

than asks me about my monitor etc etc
enter enter enter

than again jumps back to console ans saves the config...

than i write
startx to continue

however it says

FATAL ERROR
server is already active for display 0
if this is no longer running 
remove....

i think in the beginning something like this also appears
error in locking authority

file /home/ubuntu/.Xauthority.....

ANYONE UNDERSTANDS?
pls help me

I AM GONNA INSTALL UBUNTU
I AM REALLY TOUGH ON THIS!

thank you so much

:confused:

---

### Post by ebozzz on 2007-03-18
> **linuxjerk said:**
> Boy you got that right. After about 10 attempts I finally got it to install. Then found out the mouse doesn't work.
Come to find out that 6.1 doesn't support serial mice. Go figure!!
There is some fix but I haven't figured it out yet. 
Yes I could get a use mouse. But why should I. Windows didn't require that????????:confused:

Which version of Windows?

---

