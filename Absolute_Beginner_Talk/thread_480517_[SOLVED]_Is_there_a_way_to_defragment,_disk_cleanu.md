---
title: "[SOLVED] Is there a way to defragment, disk cleanup, end now???"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by JimBuntu on 2007-06-21
On my windows xp computer if something stalls or is not responding I can press ctrl+alt+del and it brings up a window allowing me to close applications and "END NOW". Is there a way to do this in Ubuntu?

Also, what about defragmenting??? How do i do that?

Also, is there a disk clean up?

What about a browsing history clean up??

Just started with Ubuntu Studio about 1.5 weeks ago and I'm trying to learn the ropes.

Thanks.

---

### Post by Paerez on 2007-06-21
1) End now: System->Administration->System Monitor. Then click the processes tab and you can "kill processes".

2) You don't need to defrag anymore.

3) For disk clean up, there are various things that are only neccessary if you run low on HD space.

4) In firefox: Tools -> Clear Private Data

Hope that helps.

---

### Post by JimBuntu on 2007-06-21
Why dont i need to defrag anymore? I thought that was used for instance when i download a big file or rip a bunch of cd's and the files are all over the place on the HD?

Even though you say i dont need to anymore, is there a way to do it?

Same with disk clean up. Why dont i need to do that either? Doesnt all of the stored web pages make my system run a bit slower? Thats the way i was told with windows.

---

### Post by lepz on 2007-06-21
> **JimBuntu said:**
>  Thats the way i was told with windows.

But your not using windows. ;)

---

### Post by lamar_air on 2007-06-21
Disk maintenance is done occasionally in the background so you don't have to worry about it, it will be done when necessary and when resources are free.

---

### Post by meatpan on 2007-06-21
> 
Why dont i need to defrag anymore?


The most common filesytems (ext2, ext3) used in linux are fundamentally different from Microsoft filesystems.  Disk fragmentation is much more of an artifact within the Microsoft file systems.

If you want to know why, here is a site that does a decent job explaining the dirty details 
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by JimBuntu on 2007-06-21
Wow...Ubuntu just keeps getting better and better every time I ask about something...COOL!!!

I love Ubuntu

---

### Post by jputman01 on 2007-06-21
> **JimBuntu said:**
> Why dont i need to defrag anymore? I thought that was used for instance when i download a big file or rip a bunch of cd's and the files are all over the place on the HD?

Even though you say i dont need to anymore, is there a way to do it?

Same with disk clean up. Why dont i need to do that either? Doesnt all of the stored web pages make my system run a bit slower? Thats the way i was told with windows.

the ext3 filesystem is less prone to fragmentation you will not see fragmentation like you did in windows

there are some commands you can run to clean up some unused packages, i believe it is ```
 sudo apt-get autoremove
```

delete your temp files within firefox like stated above

ending a program can be done the way listed above or you can add the "force quit" applet to your panel and use that to force programs to close.

hope that helps

---

### Post by corney91 on 2007-06-21
> **JimBuntu said:**
> On my windows xp computer if something stalls or is not responding I can press ctrl+alt+del and it brings up a window allowing me to close applications and "END NOW". Is there a way to do this in Ubuntu?

If you right-click on a panel and select 'add to panel' there is a button called 'Force Quit' which when clicked you can select a window to end it's process.

---

