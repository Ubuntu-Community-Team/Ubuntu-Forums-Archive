---
title: "[SOLVED] Pesky green defrag stripes!"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Jon Law on 2007-10-19
I'm trying to stick ubuntu on my laptop (dual boot). I have about 20 gb i want to dedicate to ubuntu. The problem is, when i de fragment my hard-drive, i have green stripes on the right of my hard drive and some on the left. Am I right in saying that this means I won't have 20 gb at my disposal because it has to be continuous space? Is there any way I can move those green stripes?

---

### Post by skymera on 2007-10-19
get partition magic for windows and move windows o free upthe space

---

### Post by JBAlaska on 2007-10-19
O&O Defrag and Diskeeper both do boottime defrags, You can have them do a defraf cycle on boot before any files get locked.

Windoze defrag is ..erm..less than optimal..

---

### Post by Jon Law on 2007-10-19
Thanks, are these available free or do i need to buy them?

---

### Post by Paqman on 2007-10-19
> **JBAlaska said:**
> 
Windoze defrag is ..erm..less than optimal..

Absolutely, it does a really bad job at about the speed of an asthmatic snail.

---

### Post by JBAlaska on 2007-10-19
I beleive both O&O and diskeeper have 30day trials, plenty enough time to defrag and resize your partitions. with ext3 you do not need to defrag near as often.

Good thing to, as the only way I know is to move everything off the HD and then copy it all back.

---

### Post by Herman on 2007-10-19
That immovable green  block in Windows is your page file.
It's an area on the hard disk where some of the slower moving items from your computers memory can be shunted out of the way temporarily from time to time when your RAM gets mostly used. That leaves your RAM free for the fast lane stuff. (Kind of like a highway with a slow lane, or a railway with a siding).
In Linux we have a special partition for that, called a swap area.

In Windows XP you can easily turn it off in 'Control Panel' -->'System' --> 'System Properties'-->'Advanced' tab -->'Performance, Settings button' --> 'Advanced' tab, 'Virtual Memory',-->'Change', [COLOR=#ff0000]take note of your settings[/COLOR] (on a piece of paper), and click the radio button for 'no paging file' -->'Set', 'Apply', 'Okay'.
Then restart your computer and now you can run defrag as many times as you need to, without the big green block in the way.
   (*If you do this, don't forget to go back and turn it on again later, after the resizing is over, and Ubuntu is installed*).

If you are using the Ubuntu Live CD to install Ubuntu with as most people would be, you  will  probably find it is smart enough to be able to resize Windows without needing to defrag first.
A good defragging shouldn't hurt and might do some good anyway though. 
The 'Alternate CD' for installing Ubuntu (needed sometimes for special installations), used to refuse to resize Windows sometimes if Windows was too messy.

I never need to defrag any of my Linux file systems. Linux file systems never need defragging unless we make them too full. They like a little bit of spare room in the partition for shuffling files. about 5 or 10% is all you need but 20% of spare room is a lot better.
There are no defragmenters for Linux even if they did need defragging. If the file system is nearly full it's best to make the partition bigger or remove some files and store them somewhere else.
Here are a couple of cool links about that, 
[CENTER][OneAndOneIs2 - Why doesn't Linux need defragmenting?]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting")
                        
                        [ITworld.com - Fragmentation and Unix file systems]("http://www.itworld.com/Comp/3380/nls_unixfrag040929/index.html")[/CENTER]
                                               
               Linux file systems do like to have a  'file system check' once in a while, but those are not the same thing as defragging and are a lot quicker than the defragging you are used to in Windows, and you don't have to pay for the software for doing it. 
Happy Ubunuing!

Regards, Herman :)

---

### Post by Jon Law on 2007-10-19
Thanks everyone especially Herman for taking the time to go through all that. Much appreciated.

---

