---
title: "Installation consistently fails on my B&amp;W G3"
date: 2008-05-17
forum: Apple Hardware Users
---

### Post by heroes_on_a_half_shell on 2008-05-17
hey guys,

i've got a b&w g3 that i am attempting to put ubuntu onto.  i have replaced the original hard drive with an 80 gb wd caviar se.  i have put the wd caviar se through the wd diagnostic tools, and it checks out.  i have tried ubuntu 8.04 alternate cd and the xubuntu 7.10 alternate cd. currently i am having issues in two areas:

1 - i am running into the 8 gb partition limit.  i would love to know whether or not i will be able to make one large contiguous partition out of the additional free space after i have successfully installed ubuntu.

2 - i cannot make it through the base system installation of the alternate cd install.  i keep receiving an error during this portion of the install which says:

'The debootstrap program exited with an error (return value 1).'

my installation fails with this message.  if anyone can help, i would greatly appreciate it.  if you need more info before you can help me, just ask.

---

### Post by oswaldkelso on 2008-05-18
1. Yes, Any root "/" partition MUST be in the first 8gb. The rest can be your /home partition. 

Something like this:

hda,1 7.5gb /
hda,2 72.5gb /home

2. I don't know but when you've fixed 1. You may also fix 2.

---

### Post by heroes_on_a_half_shell on 2008-05-22
<bump>

#1 has been sort of solved by using file systems other than ext3 and a 7 gb partition.  

however, i am still having problems with problem #2.

(for clarity, my first post was on a rev 2 or later blue and white [which actually installed perfectly with an ext3 file system once the partition size came down to 7 gb], whereas this post is due to a rev 1 blue and white)

---

### Post by stream303 on 2008-05-23
Are the jumpers for the new hard drive in "cable select" or "master"?  I'd doublecheck to see if it is in cable-select and try again...  

Remember that depending on manufacturer's specs, the safest way to go with an 8gb partitioning limit is to actually partition at something smaller, like 7.5 or even 7gb if it is just easier to remember.

You can always do a custom partition by keeping boot/root inside this limitation, and customize outside of it with /home /var etc.

Or a simpler way is to just install everything and during guided partitioning, move the slider to 7 - 7.5 gb or so, and later partition the rest as a general purpose data partition.  As long as root / is under 7.5 gb, you should be ok.

---

