---
title: "ubuntu panic button?"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by morganpatrick on 2006-06-25
Hello,

I'm running ubuntu dapper. I like it a lot, and when I installed it everything worked fine. I have all my /home files in a seperate partition, and /boot is its own partition as well.

Now,

I did a bunch of stuff that set my ubuntu all akimbo. I installed Kubuntu, then accidentally removed ubuntu, then restored ubuntu, removed kubuntu, and now lots of things have ceased to work. Amarok won't play my mp3s. I can't get into my mysql admin. My clock isn't working anymore. My boot screen is still Kubuntu. So even though I restored everything it's clearly not the way it was.

I really think I should just overwrite the build and start over, rather than keep messing with this stuff. Can I just run the live CD and restore everything to the initial settings? If so, how do i do this in the least painful way -- that is, how do I do this without screwing up my system even more?

---

### Post by T700 on 2006-06-25
Been there; done that!  :-)

Since you really don't have much invested at this point, my personal suggestion would be to do a fresh install and overwrite everything.  Just my opinion--your mileage may vary.

Paul

---

### Post by mlind on 2006-06-25
I would do like this
[LIST]
[*]Install all Ubuntu dependencies
```

sudo aptitude install ubuntu-base ubuntu-standard ubuntu-desktop

```
[*]Install app called **debfoster**
```

sudo aptitude install debfoster

```

[*]Execute debfoster and carefully go through dependencies once and answer **s** (skip) for every package
```

sudo debfoster

```

[*]Once I get the feeling how this app works, I'd run debfoster again and purge all Kubuntu specific depencendencies, by answering **p** (purge) this time
[/LIST]

Be very careful **not** to purge ubuntu-base, ubuntu-standard or
ubuntu-desktop packages. Or anything xorg related. Only kubuntu and kde stuff.

What you're trying to accomplish here is to remove all Kubuntu specific packages.

---

### Post by morganpatrick on 2006-06-25
thanks for the responses.

I like the idea of removing kubuntu packages, but I think I'm going with the fresh install route.

I ran an update and already i have two kernels in grub. I'm trying to keep things tidy. If I run this reinstall is grub going to add another two kernels, or think this is a secondary os? Also, can I run this install without changing my partitions or messing with my /home partition?

---

### Post by mlind on 2006-06-25
[QUOTE=morganpatrick]thanks for the responses.

I like the idea of removing kubuntu packages, but I think I'm going with the fresh install route.

I ran an update and already i have two kernels in grub. I'm trying to keep things tidy. If I run this reinstall is grub going to add another two kernels, or think this is a secondary os? Also, can I run this install without changing my partitions or messing with my /home partition?[/QUOTE]

By default Ubuntu's grub autodetects kernels on your /boot directory and
constructs boot menu (menu.lst) automatically when update-grub is invoked.
(This is done automaticaly by installer). If your you have /boot on separate
partition, remember to format it and enable bootable flag.

You can run install without modifying your partitions if you wish. If your /home is on
separate partition then you just choose to leave it unmodified when reinstalling.

---

### Post by jimrz on 2006-06-25
[QUOTE=morganpatrick]thanks for the responses.

I like the idea of removing kubuntu packages, but I think I'm going with the fresh install route.

I ran an update and already i have two kernels in grub. I'm trying to keep things tidy. If I run this reinstall is grub going to add another two kernels, or think this is a secondary os? Also, can I run this install without changing my partitions or messing with my /home partition?[/QUOTE]

since you have 2 kernels, i assume the 2nd came from an update. if you use the same install cd you will get the 2nd again when you do your updates. not sure if the iso image at ubuntu downloads has been updated to the new kernel or not. if it has and you really don't want the older one, you could d/l the iso and install from it.

---

### Post by richbarna on 2006-06-25
[QUOTE=T700]Been there; done that!  :-)

Since you really don't have much invested at this point, my personal suggestion would be to do a fresh install and overwrite everything.  Just my opinion--your mileage may vary.

Paul[/QUOTE]

Lol, Me too. Go for the fresh install.
Then do what I do now, read up on stuff before any major changes :D 

I recommend [www.psychocats.net]("http://www.psychocats.net/ubuntu/index.php")

---

