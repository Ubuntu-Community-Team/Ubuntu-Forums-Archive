---
title: "installing ubuntu"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by eschmidt90 on 2007-01-19
so, I have succesfully partitioned my disk, and I have a 10 gb partition for ubuntu.

however, I reach the step where it says; "Select the partition to mount ubuntu on and select where to mount whar", this is step 5.  It will not let me go beyond this step, the forward button remains inactive.

any help?

this is the step where it is asking for a partition to place root/swap/boot/home...etc

TIA

-Erik

---

### Post by floke on 2007-01-19
Which CD are you using? If you are using the LiveCD version then there's an option to instail on the largest available free space - assuming that this is what your 10Gs are for, then select that option and see what it does...

---

### Post by meng on 2007-01-19
If there's no option for you to select a partition and move on, try the Alternate CD installer instead.

---

### Post by floke on 2007-01-19
BTW: What version of Ubuntu are you trying to install. I am unable to install Feisty due to a bug in the installer, so I wouldn't go with that as a first install of Ubuntu. You're much better off with Edgy or Dapper.

---

### Post by eschmidt90 on 2007-01-19
ok, I got the forward button to activate, but now it says that I need a NewWorld boot partition using HFS

I set up a partition using HSF, and I set /boot to this partition, but the error still appears

any ideas?

---

### Post by floke on 2007-01-19
Whing version of ubuntu are you trying to install? And with which disc (Live CD / Alternate)?

---

### Post by eschmidt90 on 2007-01-19
I don't remember what version of ubuntu I'm using, I think its the one before 6.10

I am running from LiveCD

---

### Post by eschmidt90 on 2007-01-19
never mind, the version is 6.10, and I'm installing from the LiveCD

---

### Post by eschmidt90 on 2007-01-19
bump

---

### Post by meng on 2007-01-19
You don't need a separate /boot partition, I can't fathom why the installer should insist you do.
(And please don't get bump-happy, you have to be patient sometimes.)

---

### Post by floke on 2007-01-20
Hey dude, no need to get bumpy. I live in the UK so there's probably a time difference between us - and even I have to sleep sometimes :) 

I would (a) check the disc (there's an option to do this from the initial menu) ; and/ or (b) do what Meng says and use the alternate installer.

I've installed 6.10 from the Live CD lots of times with no issues. Did you use the Gparted tool to partition it from the Live CD, and do you select 'use largest available space' when it asks you where it wants to go (I expect you do but its worth an ask).

If this aint doing it then use (b) I guess - though its a mystery :confused:

---

### Post by eschmidt90 on 2007-01-20
attached is a screenshot of what I've been doing

I tried selecting "use largest available space,but it says there is no root partition

what is this alternative install of which you speak?

---

### Post by floke on 2007-01-21
I've never seen this screen before.
The way I've (re)installed has been this.
(a) use Live CD Gparted tool to partition hard drive (or to delete old partitions with ubuntu on if reinstalling)
(b) click install icon on Live CD desktop
(c) Answer questions about location etc. - but when you get the option of telling ubuntu where to install - I think it gives you three choices (1) use entire disc; (2) use largest available free space; (3) manually select where to install - Here I select '2' i.e. to use largest available free space (which was created in step 1).
(d) That's it! Wait for ubuntu to install.

My guess here is that you have selected the manual choice option- but if this is not the case then you can get an alternate install disc - this is a text based, rather than a GUI based, installation method - available from ubuntu website - download - choose area - choose mirror - you should then have 3 choices - one is alternative installation options - choose this - then from  the following list choose the option for you e.g. i386 architecture etc,

Hope this helps

---

