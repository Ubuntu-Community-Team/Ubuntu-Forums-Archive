---
title: "Dapper, Edgy - No splash screen"
date: 2006-10-24
forum: Apple PPC Users
---

### Post by abachman on 2006-10-24
Hi all!

I'm with ubuntu/kubuntu until the first minutes of this distribution and nothing changed, still the best out there, no doubt. :mrgreen: 
For me only one very little problem remained until dapper and now with edgy. The splash screen is not shown, will say I can see the first four or five boot messages, then nothing happens (system is booting up in the background) then kdm comes up with no problem. So what can I do to get the splash screen working.
I have an iMac, G4, 15'' Flat Panel, with Nvidia GeForce 2MX graphics, the lines in my /etc/yaboot.conf are:
...............
image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="quiet splash"
Hope somebody got things working, thanks for your help.

---

### Post by jimbren on 2006-10-26
Have you gotten anywhere with this?  I have a similar problem on my fresh upgrade to edgy.  I get no splash screen and no boot messages at all.

---

### Post by stmiller on 2006-10-27
That's the usplash. I noticed on my edgy upgrade that the usplash was missing also. Try searching around for how to restore the usplash. I'm looking too...

---

### Post by anders_gud on 2006-10-27
I lost my splash too...
usplash No usable theme found for 1280 x 854
solution:
sudo apt-get install usplash-theme-ubuntu

---

### Post by stmiller on 2006-10-27
:)  Ah! Thanks.

---

### Post by jimbren on 2006-11-10
In isntalled the usplash theme and I still don't get anything but the cursor when booting.  I think it is a problem with my menu.lst file, but I really don't know where to start with it.  

Here's what the entry looks like:
```
title           Ubuntu, kernel 2.6.17-10-386
root            (hd0,0)
kernel          /vmlinuz-2.6.17-10-386 root=UUID=cdf44a9d-e5fb-41ac-9f77-c6dc50b
f71af ro quiet splash
initrd          /initrd.img-2.6.17-10-386
savedefault
boot

```

Thanks,

jimbo

---

### Post by erick.red on 2006-11-10
apt-get install usplash-theme-ubuntu, that it execs durinf upgrade form dapper to edgy, i mean the system automatic do thats...

so i did again and still without working.

erick

---

### Post by seatea on 2006-11-11
This sort of worked  for me. [HTML]http://www.ubuntuforums.org/showthread.php?t=290998[/HTML]

---

