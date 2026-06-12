---
title: "Out of curiosity"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by quinnten83 on 2007-05-18
My Palm had problems synching until I found a howto that suggested adding a visor module.
I did that and no problem.

Mu question is what is a visor module, what does it do? It seems to be related to the kernel, but in what way?
also what are the function of modules in general? And if they are an integral part of the kernel, how come they aren't always automatically loaded? I suppose it was part of the kernel, as I did not need to install anything.
I feel that understanding these things is essential for me to understand the workings of Linux. I've been reading the Linux bible, but so far everything explained is mostly functional (and when you need the info it is hard to find it again in a book, so I end up on the forums anyway).
Do I have to have a masters in Computer or Software engineering in order to understand the meaning of these things or can n00bs pierce through the veil of shrouded mystery of Linux?

---

### Post by hartz on 2007-05-18
Kernel modules are pretty much Linux "device drivers".
Refer: [http://www.google.co.za/search?q=define%3Akernel+module](http://www.google.co.za/search?q=define%3Akernel+module)

I don't know the "visor" module, but when I scanned though my kernel config file, I discovered a module called USB_SERIAL_VISOR.  I am guessing this is what you are referring to.

In my stock Feisty Fawn kernel, it has been pre-compiled as a "loadable module".  That means it is a device driver which will load only on demand.

It is worth noting that sometimes "on-demand" does not mean "automatically on demand".  Fortunately, demand can be manually and even artificially "created" by running a command like this:
```
sudo modprobe visor
```

Doing a modprobe like above can be used to make a "loadable" module load if it does not automatically get loaded.

I just did a small test.  I first checked to see if there is anything like a visor module loaded with this command (which came out clean)
```
lsmod|grep visor
```

Then I ran the above modprobe command, which did not return any errors.  The Unix way of saying nothing when all is OK is sometimes a bit strange to new-comers.  We like our computers to be quiet when nothing needs to be reported.

After the modprobe, I ran the lsmod command above to check it again, and this time it gave me both a running module and also attached to two USB modules.

You are correct, understanding modules will take you far in understanding Linux.

To view all the currently loaded modules, try this command:
```
lsmod|less
```

To view all the loadable module options, you can look in your kernel's config file with this cryptic command:
```
grep =m$ /boot/config*$(uname -r) |less
```
Note: If you want I can dissect the above command for you.

It is worth knowing that you also get other types of modules besides "loadable" ones.

The most important distinctions are "statically linked", which means that the module is compiled into the kernel, and therefore always loaded and taking up memory, but potentially performing a little faster.  You also get modules which have been excluded, which means that it is part of the linux kernel source, but when the kernel was compiled it was excluded.  (This is typically done for modules which are unstable, or for modules for hardware which is very scarce and unlikely to be required.  Excluding unneeded modules makes the kernel smaller and therefore more efficient)

The above command can be adapted to show excluded or statically linked modules, as follow;

To show Statically linked Modules:
```
grep =y$ /boot/config*$(uname -r) |less
```


For Excluded Modules:
```
grep "is not set" /boot/config*$(uname -r) |less
```

---

### Post by quinnten83 on 2007-06-03
I just figured out how to look for my previous post, so sorry for the delay in replying.
Tnx for the info. It&#347; just that seeing all that you just wrote, I wonder if i will ever understand all that is to understand about linux.
I will try to learn as much as i can though.

---

### Post by hartz on 2007-06-04
Thank you, you prompted the subject for the last Tutorial entry on my blog.  This is about half the info you need to understand the above commands.  The other half (called substitution) will fallow soon, maybe tomorrow.

P.S. Don't expect to learn everything overnight.  One day when you look back you will say "those were the days when computers were complex and I was innocent".

---

