---
title: "Stellarium not working on Dapper Drake"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by popcorn09 on 2006-09-20
Hi,

I installed stellarium but it is not working. The error message I get is "Segmentation fault". Please tell me how to fix this!

The whole screen is as follows:

> /usr/bin$ ./stellarium

-----------------------------------------
| ## ### ### # # ### ### # # # # #|
| # # ## # # ### ## # # # ###|
|## # ### ### ### # # # # # ### # #|
| Stellarium 0.7.1|
-----------------------------------------

Copyright (C) 2000-2005 Fabien Chereau et al.

Please check last version and send bug report & comments
on stellarium web page : [http://www.stellarium.org](http://www.stellarium.org)

Loading configuration file /home/aneesha/.stellarium/config.ini ...
Locale is en_IN
Loading location: "Paris", (landscape is: "guereins")
Loading Hipparcos star data (118218 stars loaded).
Loading nebulas data (73 deep space objects)...
Loading Solar System data...
Loading configuration file /home/aneesha/.stellarium/config.ini ...
Looking for startup script to run.
Script completed.
Segmentation fault

Thanks!

---

### Post by deadgobby on 2006-09-20
> **popcorn09 said:**
> Hi,

I installed stellarium but it is not working. The error message I get is "Segmentation fault". Please tell me how to fix this!

The whole screen is as follows:



Thanks!
 Here is a handy dandy way to install Stellarium and I just did.
Open up Synaptic and install it that way. I was woundering about a program to star chart with. Because I got my 7 year old a Telescope and you save me the hassle. BIG THANKS. Once installed from Synaptic, open up the Terminal and type in  stelleruim. Away it goes. And now I am going to play with it and see how it ticks.
Gobby

---

### Post by popcorn09 on 2006-09-20
> **deadgobby said:**
> Here is a handy dandy way to install Stellarium and I just did.
Open up Synaptic and install it that way. I was woundering about a program to star chart with. Because I got my 7 year old a Telescope and you save me the hassle. BIG THANKS. Once installed from Synaptic, open up the Terminal and type in  stelleruim. Away it goes. And now I am going to play with it and see how it ticks.
Gobby

Well I installed it using Synaptic in the first place... :sad:

---

### Post by deadgobby on 2006-09-21
> **popcorn09 said:**
> Hi,

I installed stellarium but it is not working. The error message I get is "Segmentation fault". Please tell me how to fix this!

The whole screen is as follows:



Thanks!
 Mine look like this

@ubuntu:~$ stellarium

    -----------------------------------------
    | ## ### ### #   #   ### ###  #  # # # #|
    | #   #  ##  #   #   ### ##   #  # # ###|
    |##   #  ### ### ### # # # #  #  ### # #|
    |                       Stellarium 0.7.1|
    -----------------------------------------

Copyright (C) 2000-2005 Fabien Chereau et al.

Please check last version and send bug report & comments
on stellarium web page : [http://www.stellarium.org](http://www.stellarium.org)

Loading configuration file /home/doug/.stellarium/config.ini ...
Locale is en_US.UTF-8
Loading location: "Paris", (landscape is: "guereins")
Loading Hipparcos star data (118218 stars loaded).
Loading nebulas data (73 deep space objects)...
Loading Solar System data...
Loading configuration file /home/doug/.stellarium/config.ini ...
Looking for startup script to run.
Script completed.
doug@ubuntu:~$

 At looking where you typed
/usr/bin$ ./stellarium 
 At the terminal all you need to do is type in 
stellarium

Gobby

---

### Post by djsroknrol on 2006-09-21
I'm running it as well on Dapper without a hitch...you might try uninstalling it and reinstalling it again...

---

