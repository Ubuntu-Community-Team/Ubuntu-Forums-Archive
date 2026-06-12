---
title: "Removing lines from Grub"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by jbag on 2006-09-26
Hi Guys

I have been using Ubuntu for about 2 months now & am starting to find my way around. I still have along way to go though. These forums however are a great help.

I was wondering if I can safely remove some lines from grub.

When the system boots to grub the following appears:

Ubuntu, kernel 2.6.15-27-386
Ubuntu, kernel 2.6.15-27-386 (recovery mode)
Ubuntu, kernel 2.6.15-26-386
Ubuntu, kernel 2.6.15-26-386 (recovery mode)
Ubuntu, kernel 2.6.15-23-386
Ubuntu, kernel 2.6.15-23-386 (recovery mode)
Ubuntu, memtest86+
Other operating systems:
Microsoft Windows XP Professional

I would like to remove lines 3 thru lines 6 if possible

Is it safe to remove. I just wanted to clean up the menu before it gets too cluttered.

Can I just do this through the editor in grub or should I go through menu.lst.

Thanks for any help

jbag

---

### Post by bulldog on 2006-09-26
You can remove or comment ## out this lines.

You can however,the 'extra not used anymore' kernels had them removed with synaptic.

Do a search in synaptic  linux-image and remove the ones you no longer use.

Be carefull to not remove the latest one or two you need at least one to boot Ubuntu :D 

After you removed them do 
```
 sudo grub update 
```

And your grub should be up to date.

---

### Post by Rumor on 2006-09-26
Yes, you can safely remove those lines.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bkup
```
```
sudo gedit /boot/grub/menu.lst
```

And you'll be able to edit and save the file . . . and restore the backup if something oges horribly wrong :D

---

### Post by drifternel on 2006-09-26
copy this into terminal

gksudo gedit /boot/grub/menu.lst

input your password then comment out the ones you dont want by instering a # in fron of each line you want to disappear on boot up.

---

### Post by maaronB on 2006-09-26
> **bulldog said:**
> 
You can however,the 'extra not used anymore' kernels had them removed with synaptic.

Do a search in synaptic  linux-image and remove the ones you no longer use.

Be carefull to not remove the latest one or two you need at least one to boot Ubuntu :D 

After you removed them do 
```
 sudo grub update 
```

And your grub should be up to date.

I would say that this is the method you should do first.  You can go to menu.lst and edited out lines (by deleting them or by placing a ## in front of anything you don't want appering on the screen), but they would still be on your system and be basically unreachable.  What would be the point of that?  
If you remove them using synaptic then update grub it will clean them out of your system.  Not that it will save you much space, but it just seems like good housekeeping to me.  Don't hide what you use. Get rid of it.

---

### Post by jbag on 2006-09-26
Thanks to all

I really appreciate the quick responses. This proves once again that these forums are the best. Trust me when I tell you that most of the Windows forums I have tried treat you like you are from another planet.

I used the solution that drifternel suggested only because it looked like the shortest route. It worked fine.

I am sure the others would have too. I have copied & pasted all the solutions into a journal I am keeping for future reference.

You guys are the best

I really appreciate it

jbag

---

### Post by drifternel on 2006-09-26
Glad it worked Jbag
Agree about the forums too.

---

