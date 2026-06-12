---
title: "GRUB Problem"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by neo_weapon on 2007-05-31
So I have a big problem.

  I can't get back into my Windows Vista OS after installing Ubuntu Server in a separate hard drive. I also have Windows XP on this hard drive. Now when I boot into my Windows Vista hard drive, GRUB loads up and when I try to load Windows Vista/Longhorn, it takes me into Windows XP!!!! 

  Should I just remove GRUB to solve this problem. And can somebody point me to a good resource on how to properly partition hard drives? THanks.

---

### Post by Inxsible on 2007-05-31
> **neo_weapon said:**
> So I have a big problem.

  I can't get back into my Windows Vista OS after installing Ubuntu Server in a separate hard drive. I also have Windows XP on this hard drive. Now when I boot into my Windows Vista hard drive, GRUB loads up and when I try to load Windows Vista/Longhorn, it takes me into Windows XP!!!! 

  Should I just remove GRUB to solve this problem. And can somebody point me to a good resource on how to properly partition hard drives? THanks.

Read this for more info on partitioning :

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Could you post the output for```
 sudo fdisk -l
```

-l is a lowercase L

---

### Post by neo_weapon on 2007-05-31
So I sorta fixed my problem. I just inserted the vista cd and booted that to repair my vista partition. GRUB still loads up and I'm kinda scared of it. Should I get rid of it?

---

### Post by alienexplorers on 2007-05-31
If grub is working keep it.

---

### Post by neo_weapon on 2007-05-31
Uhh crap, so i deleted the ubuntu partition and now GRUB gives me an error. Is there a way to get rid of GRUB and boot windows normally?

---

### Post by neo_weapon on 2007-05-31
so i was reading in the forums and found out i needed to use fixmbr. Does anyone know where i have to input this command? thanks.

---

### Post by freebird54 on 2007-05-31
Yes there is.  You need to run one of the following:  FDISK /MBR  (from any windows up to XP) or FIXMBR (from XP CD, R for Recovery console) or Vista equivalent.  Where you go from there is up to you - Vista can install the equivalent of a Grub entry for dual booting, or you can swap drives in the BIOS or.....

Hope this helps.

---

### Post by neo_weapon on 2007-05-31
I loaded the vista cd and i went to system recovery options but I do not know where to input fixmbr. I tried fixmbr at the command prompt located under system recovery options but they said it did not recognize the command.

---

### Post by freebird54 on 2007-05-31
In Vista they changed the name (for whatever reason.  I don't have Vista (thank heavens) but I am pretty sure that the new version is MBRFIX.  If it is to boot Vista from, then I think you need to enter MBRFIX /VISTA.  You must be in the revcovery console, and I think logged into the drive that needs 'fixing'.  If you don't use /Vista - it puts an XO compat boot loader on instead...

Hope this helps.  (there's lots of Google on this too - because Vista is confusing people!)

---

### Post by neo_weapon on 2007-05-31
Sorry, i dont know how to navigate my way through the command prompt. This is where i am suppose to be right? Yea, so do you know how to navigate so i can use mbrfix correctly? Thanks

---

### Post by freebird54 on 2007-05-31
Sorry - not having a Vista system around can't specify too much!  If you can figure out where the MBRFIX command is, you should there.  If it was in:

```
C:\USERS\Username\commands
```

you would enter (at the C:\> prompt)

```
cd c:\users\Username\commands
```

changing the prompt to 

```
C:\USERS\Username\Commands>
```

Then you would type in the command.  Sorry I can't be more specific, as I haven't had to do this yet (for one thing I couldn't function on this triple boot without Grub!)  If you enter  MBRFIX VISTA in a Google search - you might well find a complete walkthrough.  Perhaps going to Linuxquestions.org might also give you that answer in a more detaiied way.  

BTW - the problem is on the VISTA drive, NOT the XP drive?  Which one gives you the GRUB prompt??

---

### Post by neo_weapon on 2007-05-31
the problem is on the vista drive. GRUB is loaded on this hard drive but the linux partition i deleted earlier was on the other hard drive.

So i was looking on google and found a person who had a similar problem and said he loaded an .exe called MBRFIX.exe that fixed his vista boot loader. 
[http://www.linuxquestions.org/questions/showthread.php?t=550172](http://www.linuxquestions.org/questions/showthread.php?t=550172)

My problem is I can't even get access into my hard drive to put this exe in there and also I tried to navigate around the command prompt typing

"cd C:"

but it keeps on giving me the "X:\Sources" prompt.

Thank you so much for you help, I will continue trying to get this fix. Thanks.

---

### Post by neo_weapon on 2007-05-31
Thank GOD!!!! After frantic search on google, I found this site

[http://www.thaivisa.com/forum/index.php?showtopic=122528](http://www.thaivisa.com/forum/index.php?showtopic=122528)

So you just run these commands here in the command prompt after getting into recovery console:

Bootrec /fixboot
Bootrec /fixmbr
Bootrec /fixboot

Thank you all for your time and help and hopefully this post will help idiots like me in the future!! HA

---

### Post by freebird54 on 2007-05-31
Darn!  I knew it had a different name, but I couldn't find it fast enogh for you!  GFlad you found it - it HAD to be there somewhere :)

Now to figure out where to log this info so I'll know next time... there are bound to be more and more Vista people trying this out!

---

