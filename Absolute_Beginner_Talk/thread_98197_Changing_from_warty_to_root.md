---
title: "Changing from warty to root"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by geoffLW on 2005-12-02
Congratulations on a great interface...
I have been trying for two days now to get a new computer to boot using the 'live' cd..
I now have all my hardware recognised but need to change the command prompt from the default  ''warty@umbuntu''   to the normal ''root'' ...so that I can format the hard disk using fdisk.
Can anyone tell me how to do this  please ?

Geoff

---

### Post by invalid on 2005-12-02
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by earobinson on 2005-12-02
sudo fdisk <whatever other commands you need> will do the trick

I searched the forums for (root password) and found this [http://www.ubuntuforums.org/showthre...=root+password](http://www.ubuntuforums.org/showthre...=root+password) (and many others)
[http://www.ubuntuforums.org/showthread.php?t=98159](http://www.ubuntuforums.org/showthread.php?t=98159)



ohhhhh you can come cast your vote as a su user [http://www.ubuntuforums.org/search.php?searchid=2771264](http://www.ubuntuforums.org/search.php?searchid=2771264)

---

### Post by juicybananahead on 2005-12-02
Hi Geoff,

Ubuntu doesn't have a root account by default, you are encouraged to use sudo instead. Check out [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo) for more information.

/juicy

---

