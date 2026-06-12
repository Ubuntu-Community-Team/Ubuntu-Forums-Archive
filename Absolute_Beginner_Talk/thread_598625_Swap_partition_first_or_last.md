---
title: "Swap partition first or last?"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by mivo on 2007-10-31
I have read contradicting answers to this question: Should the swap partition go first or last for quickest access?

swap, /, /home
or
/, /home, swap

---

### Post by nest on 2007-10-31
it makes any difference?

if yes (and if you are sure)

why?

---

### Post by Banacek on 2007-10-31
/boot, /, /usr, /var, swap, /home, /tmp

---

### Post by dacap06 on 2007-10-31
Like most things in life, I have to answer "It depends."

If you have plenty of memory in the target machine, I recommend /, home, swap.  If your machine is  memory starved then it will swap a lot, so I recommend swap, /, home in that case.

At idle with no applications running, the kernel,  libraries, X-windows, and KDE occupy around 300 Mbytes of memory in Ubuntu on my Dell laptop, both in Gutsy and Feisty.  As I run a lighter version of KDE without all the resources, mine may be a little less than yours.  I define "plenty of memory" in Ubuntu as 512 Mbytes or greater.  I often run a couple of heavyweights - Openoffice and Firefox - as well as numerous small cats and dogs like TunaPie and a few different applets such as Klaptop, the KDE power manager, and the KDE wireless manager.  Still, I don't go over 512 Mbytes.  

To determine the memory use in your specific application, use the "top" command in a terminal window to look at your memory use.  Remember to subtract the "buffers" amount to find out what you are really using.  Linux will use whatever memory it can grab for disk a disk cache, but wiill yield it up when you load another application.  Also remember that swap space use is (almost) never 0, even when it is not in use if you get a transient use at Startup, you'll create overhead structure in it to keep track of what is used and where.

My one word of advice that differs from convention is to set up a swap space that is 3 times your memory (most say 1.5-2).   The reason I say that is because it is a pain (and dangerous to your data) to move partitions around after you install.  Later when you add memory, you will still have enough swap space to suspend to disk if you follow my advice.  Remember, the suspend-to-disk feature requires that you have more swap space than memory.  Of course, if your machine is already maxed out with memory, you can ignore my recommended ratio. :).

---

### Post by ant2ne on 2007-10-31
> **nest said:**
> it makes any difference?

if yes (and if you are sure)

why?

I'd still like to hear an answer to "why?". Is it easier/quicker for the hard drive to access the first partition, so it would be a speed boost to put the swap first?

---

### Post by leileicats on 2007-10-31
Hi, **dacap06**, just as you said, the swap space use is never 0, but why mine is 0 after I use the "top" command.

lei@maverick:~$ top

top - 15:25:25 up  1:12,  2 users,  load average: 0.37, 0.24, 0.26
Tasks: 123 total,   1 running, 122 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.2%us,  0.0%sy,  0.0%ni, 99.7%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   1027476k total,   837400k used,   190076k free,    18920k buffers
Swap:  1020116k total,        [COLOR="Red"]0k used[/COLOR],  1020116k free,   480412k cach

---

### Post by dacap06 on 2007-10-31
> **leileicats said:**
> Hi, **dacap06**, just as you said, the swap space use is never 0, but why mine is 0 after I use the "top" command.

lei@maverick:~$ top

top - 15:25:25 up  1:12,  2 users,  load average: 0.37, 0.24, 0.26
Tasks: 123 total,   1 running, 122 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.2%us,  0.0%sy,  0.0%ni, 99.7%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   1027476k total,   837400k used,   190076k free,    18920k buffers
Swap:  1020116k total,        [COLOR="Red"]0k used[/COLOR],  1020116k free,   480412k cach

Wow.  How'd you manage that?  Looks like I am wrong.  Swap space can be 0.

---

### Post by Bliepo32 on 2007-10-31
I know there is a bug in Ubuntu which can cause the swap to be reported as 0, whilst it is not.

---

### Post by Jaco Du Toit on 2007-10-31
It is actually possible for it to be 0k used. In my case the output for top is:

Mem:   2074432k total,   601280k used,  1473152k free,     20584k buffers
Swap:  4803392k total,            0k used,  4803392k free,   334612k cached

and the output for free is:

                   total         used          free     shared     buffers     cached
Mem:      2074432     601032    1473400             0      20624     334620
-/+ buffers/cache:     245788    1828644
Swap:     4803392             0     4803392

If I then proceed to start up a virtual pc with 1,7gig of RAM configured for it the output for free becomes:
             total       used       free     shared    buffers     cached
Mem:       2074432    2020236      54196          0       1536    1784216
-/+ buffers/cache:     234484    1839948
Swap:      4803392      71684    4731708

So quite clearly swapping only happens when it really has to.

Incidentally there is a kernel parameter that controls this to an extent. You set it by editing /etc/sysctl.conf. 

You add the line 

vm.swappiness = 0 

to the end of that file and reboot, to basically tell ubuntu to only swap when it really has to, thus keeping as much as possible in ram, leading to generally more responsive system in my opinion.

---

### Post by macogw on 2007-10-31
> **ant2ne said:**
> I'd still like to hear an answer to "why?". Is it easier/quicker for the hard drive to access the first partition, so it would be a speed boost to put the swap first?

Yep.  The first partition is closest to the center of the hard drive.  Think of a record player.  You start in the middle and work your way out.  Hard drives look just like record players, and their arms start in the middle and go out.  The shortest distance for them to travel is to the first partition.

---

