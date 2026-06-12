---
title: "[SOLVED] disk partitioning question"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by _lik_ on 2008-01-28
1. Ok, I am about to install Ubuntu, but I get confused when it comes to disk partitioning part. The first option (among three) asks me to set the amount I would like to free for Ubuntu, but the scroll button will not go below 40 GB. I have one 160 GB hard disk, but about 7 GB goes for HP recovery. Is there any way I can make the amount for Linux lower than 40 GB?

2. I tried also to make a partition in Vista, So I "created" about 20 GB (I guess it will be more than enough since I am the beginner). When it comes to disk partitioning part (Ubuntu installation), I pick manual and then select the new partition I created. But it can not be proceeded because "root (something) is not defined". 

Can anybody help me with this? Either 1 or 2? And please be specific as much as possible (what exactly do I have to type in certain field when it comes to disk partitioning part)
Thanks

---

### Post by logos34 on 2008-01-28
2.  You have to specify '/' as the root mount point.

Or start over and choose 'guided' install on 'largest continuous free space'--it should pick the empty 20 gb partition you created with vista.

post back if you have any questions

---

### Post by Amstell on 2008-01-28
> **_lik_ said:**
> 1. Ok, I am about to install Ubuntu, but I get confused when it comes to disk partitioning part. The first option (among three) asks me to set the amount I would like to free for Ubuntu, but the scroll button will not go below 40 GB. I have one 160 GB hard disk, but about 7 GB goes for HP recovery. Is there any way I can make the amount for Linux lower than 40 GB?

2. I tried also to make a partition in Vista, So I "created" about 20 GB (I guess it will be more than enough since I am the beginner). When it comes to disk partitioning part (Ubuntu installation), I pick manual and then select the new partition I created. But it can not be proceeded because "root (something) is not defined". 

Can anybody help me with this? Either 1 or 2? And please be specific as much as possible (what exactly do I have to type in certain field when it comes to disk partitioning part)
Thanks

option 1.  the best way to do this is to reformat everything.  That allows for a clean disk.  Do that through gparted.

option 2.  the reason you are getting that is because root is not defined.  You need to define it as "/"  that sets up your system.

Cheers

---

### Post by _lik_ on 2008-01-28
> **Amstell said:**
> option 1.  the best way to do this is to reformat everything.  That allows for a clean disk.  Do that through gparted.

option 2.  the reason you are getting that is because root is not defined.  You need to define it as "/"  that sets up your system.

Cheers

1. So you are saying that I use entire disk just for Ubuntu?

2. if I decide for the second option I just need to type "/" and that's it?

---

### Post by Amstell on 2008-01-28
1.  no.  backup everything you have reinstall windows.  Partition it with windows on how much you want windows to have and leave the rest open.  Once windows is done install ubuntu and use gparted to partition a swap partition and a root partition "/"

2.  Yes all you have to do is "/"  thats how you specify the file system

Cheers

---

### Post by _lik_ on 2008-01-28
> **Amstell said:**
> 1.  no.  backup everything you have reinstall windows.  Partition it with windows on how much you want windows to have and leave the rest open.  Once windows is done install ubuntu and use gparted to partition a swap partition and a root partition "/"

2.  Yes all you have to do is "/"  thats how you specify the file system

Cheers

Ok, the first drops out (because it's way too complicated for me). And for the second, are there any other "problematic" parts after i finish with disk partitioning? (it would be nice if I know in advance, because it's really hard to switch back and forth. I am doing all this from one laptop). And do I type exactly "/" or just / ? (I know it's dumb, but...)

---

### Post by Amstell on 2008-01-28
> **_lik_ said:**
> Ok, the first drops out (because it's way too complicated for me). And for the second, are there any other "problematic" parts after i finish with disk partitioning? (it would be nice if I know in advance, because it's really hard to switch back and forth. I am doing all this from one laptop). And do I type exactly "/" or just / ? (I know it's dumb, but...)

Make sure you have created a swap partition of like 1 -2 gb.

And yes all you have to do is specify your ext3 as "/"

that will create your file system

ex.

/etc/
/lib/
/home/user name/
/usr
etc....

GOod luck with the laptop, they are a pain in the *** sometimes

---

### Post by _lik_ on 2008-01-28
ok, the last thing. How do I create a swap partition (of 2 GB)?

---

### Post by Amstell on 2008-01-28
just creat a new partition before your ext3 and instead of selecting ext3 choose swap partition.  This works kind of like ram does but gives you better performance.  I use 2gb of swap and have 2 gb of ram installed and my system runs great!

---

### Post by _lik_ on 2008-01-29
Well this does not work. In "prepare partition" menu I have the option to select "free space". I double click on it and it shows me the dialog menu where I have ext3 for "use as". In mout point I type "/" and click ok. It shows me the message 

The mount point you entered is invalid.
Mount points must start with "/". They cannot contain spaces.

After that I double click again on the same place and it shows me the menu where I type insert home (for ex.) as a mount point. I click next but it shows me the same message like before. I tried to pick swat instead ext3 but I do not have an option to specify 2GB there. This looks depressing

---

### Post by Amstell on 2008-01-29
> **_lik_ said:**
> Well this does not work. In "prepare partition" menu I have the option to select "free space". I double click on it and it shows me the dialog menu where I have ext3 for "use as". In mout point I type "/" and click ok. It shows me the message 

The mount point you entered is invalid.
Mount points must start with "/". They cannot contain spaces.

After that I double click again on the same place and it shows me the menu where I type insert home (for ex.) as a mount point. I click next but it shows me the same message like before. I tried to pick swat instead ext3 but I do not have an option to specify 2GB there. This looks depressing

you want to type / not "/"

did you type "/"

???

---

### Post by _lik_ on 2008-01-29
> **Amstell said:**
> you want to type / not "/"

did you type "/"

???

Ok. I did type EXACTLY "/" :) but now I corrected it. Now, how do I create swap from here?

---

### Post by Amstell on 2008-01-29
do the swap first...that way you allocate the correct disk space for your ext 3.

just hit create new partition and select swap of 2gb then once that is created finish off the rest of your drive with an ext3 using / not "/"

:)

your doing good....keep it up and let me know how it turns out....you'll love linux.

---

### Post by _lik_ on 2008-01-29
I do not see 2 GB anywhere. But it does say swap. So do I double click again swap (it used to say free space before I did swap) and then edit and instead swap pick ext3, /,...

---

### Post by Amstell on 2008-01-29
yeah when you choose swap just make the size 2 gb.....edit that yourself....then choose ext3 and it will fill in the rest.

---

### Post by _lik_ on 2008-01-29
Look, I am not that advanced as you are :) How do I create 2GB? Where do I go?

---

### Post by Amstell on 2008-01-29
i'm sorry, not trying to be advanced as i am fairly new also.

what you want to do is select free space and select swap.  once that is selected just look for the size of the partition.  probably under size or something of that nature.

[http://gaynor.org/images/images/Screenshot.png](http://gaynor.org/images/images/Screenshot.png)

i know this screenshot is nothing like it but notice how the swap and ext3 are different.

Does that help at all?

---

### Post by Paqman on 2008-01-29
> **_lik_ said:**
> Look, I am not that advanced as you are :) How do I create 2GB? Where do I go?

If you have some free space just click on that, set the size for the new partition to 2048MB or so, and pick "swap" as the format. If you don't have free space you'll have to edit an existing partition to make some free space then do the above.

Take a look at [this guide](http://www.sp0rk.co.uk/Archive/Issue10/stayingin_install_ubuntu6.php) for some specific instructions about how to set up your partitions. This guide also suggests creating a separate partition for your home directory, which is optional but very handy.

---

### Post by _lik_ on 2008-01-29
> **Amstell said:**
> i'm sorry, not trying to be advanced as i am fairly new also.

what you want to do is select free space and select swap.  once that is selected just look for the size of the partition.  probably under size or something of that nature.

[http://gaynor.org/images/images/Screenshot.png](http://gaynor.org/images/images/Screenshot.png)

i know this screenshot is nothing like it but notice how the swap and ext3 are different.

Does that help at all?

Yes, it does help. On mine, the size of swap is 21467 MB. Is that good? So now I just edit it and instead of swap I end up having that ext3. Right?

---

### Post by Amstell on 2008-01-29
no no no....make the swap 2000 mb.   that is exactly 2gb..   it will make it more like 1.9 gb but that won't matter


just make it 2000mb

then make the rest  your ext3

---

### Post by _lik_ on 2008-01-29
> **Amstell said:**
> no no no....make the swap 2000 mb.   that is exactly 2gb..   it will make it more like 1.9 gb but that won't matter


just make it 2000mb

then make the rest  your ext3

This was close. Ok, I did what you said and now a new free space appeared. So I just put there ext3. Is this finally it?

---

### Post by Amstell on 2008-01-29
yes....what is your free space allocated?  

18-20gb i am guessing

make sure the root system is set to /

did that work

---

### Post by _lik_ on 2008-01-29
> **Amstell said:**
> yes....what is your free space allocated?  

18-20gb i am guessing

make sure the root system is set to /

did that work

It is 19428 MB. On the new 'free space' I created ext3 / (I typed linux after / :)). Is that what you call root system? I guess that would be it now?

---

### Post by Amstell on 2008-01-29
thats perfect....exactly what you want.....

how did that work out for you?

---

### Post by _lik_ on 2008-01-29
> **Amstell said:**
> thats perfect....exactly what you want.....

how did that work out for you?

Bad. After I click next I got message:

No root file system is defined.

Please correct this from the partitioning menu.

---

### Post by Amstell on 2008-01-29
make sure your ext3 is set to

/

you did do that right?

---

### Post by _lik_ on 2008-01-29
> **Amstell said:**
> make sure your ext3 is set to

/

you did do that right?

I did but after backslash I typed word Linux. Now I deleted it and now it worked. Great. Just stay for a while. Maybe something else pops up.

---

### Post by Amstell on 2008-01-29
that should work....it will install and get your grub working...i have to get up and go to school tomorrow so ....plus the beers are starting to work on me....feel free to im me if you want

im = amstel92109

i'll be up until my beer is gone.

cheers

---

### Post by _lik_ on 2008-01-29
Ok. It's late even here in NJ. thanks a lot for this. You could write a book about how to set partition for ubuntu :)

---

### Post by Amstell on 2008-01-29
to be honest its easier the more you do.  I have setup so many  linux partitions its crazy.  Just keep at it and AIM me if you need help.  Or Private Message me if you need help.  I am fairly new but use linux exclusively.  Take care and I'm off to bed.

Cheers and good luck

don't give up on ubuntu, its the best and you'll love it.

cheers

AIM = amstel92109

---

