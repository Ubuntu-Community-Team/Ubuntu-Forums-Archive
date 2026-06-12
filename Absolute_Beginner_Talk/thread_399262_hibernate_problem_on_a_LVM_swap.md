---
title: "hibernate problem on a LVM swap"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by tomcheng76 on 2007-04-02
Hi guys,
  My problem is that when i try to hibernate, it first goes to screensaver mode and
then it shows a black screen with this sentences
```

Hibernate: pnp: failed to access device 00:0c
```

and then the PC shutdown

after turning on the PC again, everything is just like a normal boot except i lost my swap which means i have to mkswap again ~~

then i try to follow the solution here
[https://launchpad.net/ubuntu/+bug/66637](https://launchpad.net/ubuntu/+bug/66637)

i found out that they are all using sdXX or hdXX, which is not my case /dev/mapper/VolGroup00-LogVol01

Also, /dev/disk/by-uuid/ dont have the symbolic link goes to /dev/mapper/VolXXX

i manually add it but it doesnt help

Now i am currently using "/dev/mapper/VolXXX" in fstab and resume file, giving the "user friendly" UUID up :( 

i keep searching and i finally find something like this
[http://www.suspend2.net/HOWTO-7.html#ss7.3](http://www.suspend2.net/HOWTO-7.html#ss7.3)

Could anyone tell me what is the problem using a LVM swap for hibernate to save and resume ?

Any help is great!
Thanks for reading

---

