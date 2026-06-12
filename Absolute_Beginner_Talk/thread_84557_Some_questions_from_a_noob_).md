---
title: "Some questions from a noob :)"
date: 2005-10-31
forum: Absolute Beginner Talk
---

### Post by Joakim Christiansen on 2005-10-31
I'm quite new to linux.
I just installed Ubuntu 5.10...
I have an AMD Athlon 64, should I download the 686 kernel then?
I got the great program called Automatix, I installed nvidia drivers with that, but I got some weird stripes on my screen sometimes...
And I want to set the refreshrate to 85...
And what the hell is the root password? I didn't set any...
And how can I acces my NFTS drive? I'm not allowed...
And yeah... it crashed 2 times...

---

### Post by Joakim Christiansen on 2005-10-31
I think I should install the linux-k7 kernel?
Must i then remove the linux-386?

---

### Post by stuporglue on 2005-10-31
> I'm quite new to linux.
<snip>
I think I should install the linux-k7 kernel?
Must i then remove the linux-386?

Now, I'm not saying you shouldn't or couldn't -- I'd hate to discourage someone from trying new things...but, if you haven't got your refresh rate, don't know about the root password/sudo thing or how to access your NTFS drive, you should probably learn a bit more about Linux first. 


> I just installed Ubuntu 5.10...
I have an AMD Athlon 64, should I download the 686 kernel then?

The default kernel is almost always the best choice, in my opinion. Unless you know you are missing some functionality that the other kernel gives, why break it? 

> And what the hell is the root password? I didn't set any...
You don't need one. Search the wiki/forums for "sudo"

---

### Post by janne5011 on 2005-10-31
sorry but I have a different opinion on this. there is no need "know about linux" for fix the refreshrates, know about the passwords and so on.. I did it and I know nothing.

Try. try again.try again. search
somewhere everyobdy must start.
thanks:) 
......................
tip of the week: "ubuntu starter guide...;)

---

### Post by Kyral on 2005-10-31
You should be running the AMD64 kernel (K8 I believe)

---

### Post by paddyg on 2005-10-31
[QUOTE=Joakim Christiansen]I'm quite new to linux.
And I want to set the refreshrate to 85...
And what the hell is the root password? I didn't set any...
And how can I acces my NFTS drive? I'm not allowed...
[/QUOTE]

refresh rate:

system-->preferences-->screen resolution

or

```
sudo gedit /etc/X11/xorg.conf
```

in the ```
Section "Monitor"
```
set HorizSync / VertRefresh values according to your monitor specifications

ntfs:
[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

---

### Post by tonysathre on 2005-10-31
for mounting windows partitions look at these:
[http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs)
[http://www.ubuntuguide.org/#mountunmountfat](http://www.ubuntuguide.org/#mountunmountfat)
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

the root account cant login by default,u should have been asked to set your root password when u installed, u can set the root password with : 
sudo passwd root

---

