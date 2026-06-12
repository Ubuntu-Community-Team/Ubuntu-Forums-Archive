---
title: "Very especific help request (installing Edgy)"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by Jormanks on 2007-04-03
Hi.

Well, i have this problem installing Edgy, again.

It's regarding the mount points. Please see the pictures attached... please.

---

### Post by jhenager on 2007-04-03
So what happens if you try Next in the last screenshot? Is there a reason you aren't just letting the installer do it for you?

---

### Post by Jormanks on 2007-04-03
Nothing happens.
Nothing.
It just says "no root file system" when i hit next. Nothing happens.

And why the Feisty installer doesn't look like this one?
I think that is very difficult to understand, and much more when resizing partitions.

---

### Post by jjalocha on 2007-04-03
I had the same problem when I tried to install Edgy. If I remember correctly, I had to fall back to the alternate CD. Now I always install with the alternate CD only, I had too many problems with the desktop CDs on my (difficult) system.

---

### Post by jkeyes0 on 2007-04-03
I'm not 100% on this one, but I believe you have to checkmark the "Format" button on the line you've labeled as /. Something has to be wiped clean to install Ubuntu on.

---

### Post by Jormanks on 2007-04-03
> **jjalocha said:**
> I had the same problem when I tried to install Edgy. If I remember correctly, I had to fall back to the alternate CD. Now I always install with the alternate CD only, I had too many problems with the desktop CDs on my (difficult) system.

Thanks, I'll try it..... but.... i really don't understand why it has to be like that.

Anyways, thanks again

---

### Post by Jormanks on 2007-04-03
> **jkeyes0 said:**
> I'm not 100% on this one, but I believe you have to checkmark the "Format" button on the line you've labeled as /. Something has to be wiped clean to install Ubuntu on.

Nope, it stays the same. I also resized the partitions and then rebooted....

---

### Post by dstew on 2007-04-03
One possible guess--if you press the forward button when there is no root file system, it locks you out, so that now even if you make one / it will not go forward. You have to go back first, then forward, then select root, then forward again.

I had to keep going back and forth like this with the 6.10 installer on a notebook recently if I picked something it did not like.

---

### Post by zvacet on 2007-04-03
In the last screenshot you choose wich partition will be your rot but you didn´t chek box under reformat.Maybe that is reason you can not go forward,because your partition is not formated.

---

### Post by jhenager on 2007-04-03
Here's what I would suggest. Pick one of your drives for Ubuntu. Move any existing data to another drive. Let Installer partition it for you, and allow it to erase and use the whole drive.

---

### Post by Jormanks on 2007-04-03
> **zvacet said:**
> In the last screenshot you choose wich partition will be your rot but you didn´t chek box under reformat.Maybe that is reason you can not go forward,because your partition is not formated.

Did it...


> **jhenager said:**
> Here's what I would suggest. Pick one of your drives for Ubuntu. Move any existing data to another drive. Let Installer partition it for you, and allow it to erase and use the whole drive.

Can't afford it....

> **dstew said:**
> One possible guess--if you press the forward button when there is no root file system, it locks you out, so that now even if you make one / it will not go forward. You have to go back first, then forward, then select root, then forward again.

I had to keep going back and forth like this with the 6.10 installer on a notebook recently if I picked something it did not like.

Doesn't work...

I'll try to format the partitions with gparted and proceed to install

:D

---

### Post by Jormanks on 2007-04-03
I think i got it....installed feisty...

Gonna reboot now

---

### Post by rusty4r on 2007-04-03
I had this same problem the first two times I tried to install edgy but for some reason it worked the third time. I was selecting a previously formatted partition and It stuck on me too. I went back and checked for it to format the partition but that still didn't work. So a couple of hours later I tried the install again from sratch (booting with the desktop cd) and I chose to format the partition right away and it worked.

---

