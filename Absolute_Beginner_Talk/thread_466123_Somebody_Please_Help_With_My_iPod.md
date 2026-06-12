---
title: "Somebody Please Help With My iPod"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by tylerjroach on 2007-06-06
I am going on vacation tomorrow and i cannot get my ipod to work correctly. When I plug it in it will not mount unless i do:
```
sudo mount /dev/sda2 /media/ipod
```

It then mounts but in amarok it says i do not have permission to create a lockfile and therefore it will not open it.

If i restart my computer i have to put in the first code for Ubuntu to even recognize it.

Once I do that and it is connected i cannot eject it. It says permission denied and comes up with three error messages all saying i cant eject it, unmount it, or do anything with it.

Is there something I need to add in fstab  or does anyone know what I need to do.
Please help. I have been working on this for hours. I need it to work. Thank You.

---

### Post by greenstar on 2007-06-06
Might be related to this:
[http://ubuntuforums.org/showthread.php?t=422711](http://ubuntuforums.org/showthread.php?t=422711)

I had this problem with my external hard drives. The workaround proposed below worked for me. See here for details:
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/99538/comments/6](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/99538/comments/6)

In summary, do this:

```
sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi.original
```Reboot & see if you have better luck.

Hope this helps,
Greenstar

---

### Post by tylerjroach on 2007-06-06
Thank you for you response. I will keep this in mind if I ever have this problem again. I decided to do a clean install and my ipod worked immediately. The previous Feisty installation I had was only about a week old so I dont know what went wrong in installing my iPod. I do remember that my ipod was plugged in during the first installation. Could this have anything to do with my problem. My second install, i didn't have my ipod plugged in and it is working great. Just a thought.

---

### Post by greenstar on 2007-06-07
Oops! Double-post.

---

### Post by greenstar on 2007-06-07
You're welcome.

You can pass the favor on by helping someone else who has an unanswered post. :)

If I were a gambling man, I'd wager that having your Ipod plugged in during OS installation might've had something to do with your problem, but I can't say that for sure. I've had odd problems before when I left too many things plugged into a box during installation. USB Flash drives & digital cameras come to mind.

Greenstar

---

