---
title: "I destroyed my GDM by using &quot;dpkg-reconfigure xserver-xorg&quot;..."
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-03-26
Hello !!!

I have destroyed the GDM interface...

How can I fix this?

OR: is it NOT fixable?

I was playing around with the "dpkg-reconfigure xserver-xorg" to FIX my Ubuntu PC's resolution & I ended up NOT being able to Boot into My Ubuntu....

Can you please provide some help?

Thanks in advance.

---

### Post by Xian on 2006-03-26
[QUOTE=dvarsam]I was playing around with the "dpkg-reconfigure xserver-xorg" to FIX my Ubuntu PC's resolution & I ended up NOT being able to Boot into My Ubuntu....[/QUOTE]

What exactly does happen when you attempt to boot into Ubuntu??

---

### Post by dvarsam on 2006-03-26
[QUOTE=Xian]What exactly does happen when you attempt to boot into Ubuntu??[/QUOTE]

There was an error saying that GDM cound not start...

I did NOT write it down, but I fixed it !!!

This is how:

1. I booted fror the Ubuntu Live CD.

2. Inside the "/mnt", I performed a "mkdir linux_os"

3. I then performed a "mount -t ext3 /dev/sda1 /mnt/linux_os"

4. I then moved to the "/etc/X11" folder

5. I did a "cp /etc/X11/xorg.conf /mnt/linux_os/etc/X11/"

6. Then Rebooted my Ubuntu from the Hard Drive!

Everything worked like before.... awesome!!!


I had never done this before...!!!

I just copied the appropriate file from the Ubuntu LiveCD to my Ubuntu Hard Drive & EVERYTHING worked perfectly!!!

Thanks for your help!

P.S.> With Ubuntu, everything is possible!!!

---

### Post by az on 2006-03-27
sudo /etc/init.d/gdm stop

That shuts down the X server.  You sometimes cannot properly autodetect the hardware if the x server is running.

sudo dpkg-reconfigure -phigh xserver-xorg

That configures X using the default autoconfigured options.  This is how the live cd and the installer configure your X. 

sudo dpkg-reconfigure xserver-xorg 
(without the -phigh switch) will ask you a bunch of questions.  Use that to tweak or if autodetection did not work.

sudo /etc/init.d/gdm start

Will restart X.

---

### Post by dvarsam on 2006-03-27
Dear "Azz",

I did not know man, thanks!!!

If I knew it earlier, I would have tried your commands!

But I will make a note on them, in case I need them in the future...

Thanks again!

---

