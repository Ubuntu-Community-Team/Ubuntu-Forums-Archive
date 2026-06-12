---
title: "libplayererror2 removal help"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by lauchea2 on 2007-11-14
I'm trying to install a software call Player (sometimes also known as Robotic-Player)

One of the library it need is called: Libplayererror2

There is apparantly one already installed in Ubuntu but it is of older version. The player software need a newer version to work. So I download it and when it comes to installing, it just would not let me.

The message came back from terminal provided by the .deb installation file that it tries to overwrite the file but then it stopped and just stay stuck on 

(Reading database...)


On the top just beneath the progress bar it says "fail to install"
What do I do? I'm thinking of deleting the older version's file and then install the new one in. But how do I do that??

Am I doing it the right way or is there another method that is better. If you know of any other solution, please let me know. Thanking you

Regards,

Andy Lau

---

### Post by 1337455 10534 on 2007-11-14
Em;
sudo apt-get purge libplayererror2

And find a better version on [http://packages.ubuntu.com/gutsy/libs/libplayererror2](http://packages.ubuntu.com/gutsy/libs/libplayererror2), this is the Gutsy version btw!!!!!!!

---

### Post by lauchea2 on 2007-11-15
It won't let me remove the libplayererror library on its own but when I tried to remove the "player" itself that uses it. Bam it's gone.

Thanks for your help!!


> **1337455 10534 said:**
> Em;
sudo apt-get purge libplayererror2

And find a better version on [http://packages.ubuntu.com/gutsy/libs/libplayererror2](http://packages.ubuntu.com/gutsy/libs/libplayererror2), this is the Gutsy version btw!!!!!!!

Yeah that's the newer version I stumble across

---

