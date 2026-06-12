---
title: "why is everything sooo osooooo slow"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by Rorgy on 2006-04-22
dont get me wrong i love ubuntu...but everything just seems sooo slow

if somebody could tell me how to show my computer specs (so i can post them) that would be great

anyhoo

everything is slow..it is most noticable on the internet
we have fast internet, and on all the other computers in the house running windows, the page loads right away, fast, and u can scroll easily.
on my ubuntu computer the page takes a few seconds longer to load, and on pages like myspace, and some forums....it takes forever to scroll...u use my scroll button on the mouse and to scroll down a page it takes like 30 long seconds

other slow things include....i maximize a window, and i see it go up, but its at least 2-5 seconds before anything shows up...sometimes more...

its very frustrating

i know before u can even try to help me u will probly want my computer specs but i dont remember how to get those

---

### Post by xXx 0wn3d xXx on 2006-04-22
[QUOTE=Rorgy]dont get me wrong i love ubuntu...but everything just seems sooo slow

if somebody could tell me how to show my computer specs (so i can post them) that would be great

anyhoo

everything is slow..it is most noticable on the internet
we have fast internet, and on all the other computers in the house running windows, the page loads right away, fast, and u can scroll easily.
on my ubuntu computer the page takes a few seconds longer to load, and on pages like myspace, and some forums....it takes forever to scroll...u use my scroll button on the mouse and to scroll down a page it takes like 30 long seconds

other slow things include....i maximize a window, and i see it go up, but its at least 2-5 seconds before anything shows up...sometimes more...

its very frustrating

i know before u can even try to help me u will probly want my computer specs but i dont remember how to get those[/QUOTE]

1. If you don't have much ram/cpu, use XFCE.
2. Use InitNG ([www.wiki.ubuntu.com/InitNG](www.wiki.ubuntu.com/InitNG))
3. Disable uneeded services from starting
4. Make sure you have the latest drivers for your video card.
5. Prelink
6. Make sure DMA is enabled
7. Tweak your ext3 filesystem for a performance boost.
8. Compile the newest kernel from kernel.org and disable all uneeded modules/features.
9. Have a specific kernel for your processor (686,386,w/e)
10. In terminal type
> sudo apt-get clean
This will clean all tempoary packages.

---

### Post by Bloch on 2006-04-22
Hi MasterChief
I'm interested in the steps you mention to speed up the system.
(and I can add one I learned: Applications --> System Tools --> Configuration Editor --> apps --> metacity --> general and tick reduced_resources to get a wireframe when moving/resizing windows. IUt helps on my system)

But can you explain step 3 and step 5?
I never heard of prelinking.
How do I disable unwanted services, and what services typically are not required?

---

### Post by xXx 0wn3d xXx on 2006-04-22
[QUOTE=Bloch]Hi MasterChief
I'm interested in the steps you mention to speed up the system.
(and I can add one I learned: Applications --> System Tools --> Configuration Editor --> apps --> metacity --> general and tick reduced_resources to get a wireframe when moving/resizing windows. IUt helps on my system)

But can you explain step 3 and step 5?
I never heard of prelinking.
How do I disable unwanted services, and what services typically are not required?[/QUOTE]
[ Disable uneeded services ](http://ubuntuforums.org/showthread.php?t=89491&highlight=disable+services)
[ Prelink ](http://ubuntuforums.org/showthread.php?t=74197&highlight=prelink)

---

### Post by adamkane on 2006-04-22
Check which kernel Ubuntu installed. Ubuntu usually install a 386 kernel, which is too slow.

```

uname -r

``` 
This should say 2.6.12-10-686 or 2.6.12-10-k7

If not, then:

Intel Pentium:

```

sudo apt-get install linux-686 linux-image-686 linux-headers-686 linux-restricted-modules-686

``` 
AMD K Series (Duron, Athlon, Sempron):
 
 ```

 sudo apt-get install linux-k7 linux-image-k7 linux-headers-k7 linux-restricted-modules-k7
 
``` 
Older legacy PC (Intel Pentium Pro or 486):
 
 ```

 sudo apt-get install linux-386 linux-image-386 linux-headers-386 linux-restricted-modules-386
 
``` 
Reboot.

This is all you really need to do.

If you still want more speed, then speed up Ubuntu this way:
(Disable services, speed up hard drive)
[http://www.ubuntuforums.org/showthread.php?t=89491]("http://www.ubuntuforums.org/showthread.php?t=89491")

I got into trouble disabling hotplug services. There's a way to do it, but not really worth the trouble. Don't bother with pre-linking. It's not worth the trouble either.

---

### Post by Bloch on 2006-04-22
Thanks for those tips, Adam & MasterChief. 
 I keep seeing advice like "install XFCE" or "upgrade your hardware" whenever the speed issue is mentioned. I'd be happy to use the Xubuntu/xfce desktop, but I wouldn't recommend it to a newbie. Gnome is much more user-friendly, and worth the slight drop in responsiveness.

> i know before u can even try to help me u will probly want my computer specs but i dont remember how to get those

I'd like to hear your specs. Applications --> System Tools --> System Information   should get it. Or else press delete repeatedly when booting and get the information from the blue and white system-setup screen

---

### Post by Rorgy on 2006-04-23
i tried going applications>system tools> system information.....i dont see it

i already tried looking for a button like this and i couldn't see it anywhere

and bloch said it the best....i like user friendly
i have had linux for about 2 years, and i have never really done anything with it, i am still a freaking nuub....i can do almost anything as long as u do it gui style...but when it comes to hardware shit or using the terminal im a moron...so the more userfriendly ...the better

---

### Post by Bloch on 2006-04-23
Sorry Rorgy;
That System Information program is one I must have installed myself - you can install it too 
Applications --> Add Applications  and under System Tools you will find it. (it would be better if it was included in the installation, but I suppose space is limited on one disk)

You can also get the info on the terminal by entering:
cat /proc/cpuinfo 
for the cpu (central processing unti - the main chip) specs
and 
lspci
for your video card.

---

### Post by skinnygmg on 2006-04-23
go here to learn how to change settings in firefox to load pages faster

[http://www.freerepublic.com/focus/f-news/1299854/posts](http://www.freerepublic.com/focus/f-news/1299854/posts)

---

### Post by Rorgy on 2006-04-28
[QUOTE=skinnygmg]go here to learn how to change settings in firefox to load pages faster

[http://www.freerepublic.com/focus/f-news/1299854/posts](http://www.freerepublic.com/focus/f-news/1299854/posts)[/QUOTE]


this had a very minimal effect

ill post my sys info after work

---

