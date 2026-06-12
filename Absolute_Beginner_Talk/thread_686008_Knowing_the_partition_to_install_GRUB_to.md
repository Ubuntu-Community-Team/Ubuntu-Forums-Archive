---
title: "Knowing the partition to install GRUB to"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by ElDudorino on 2008-02-02
Okay, so I'm trying to get a setup where I can dual boot Vista and Ubuntu.  Like everybody.  I have Vista installed already.

Here's the short version of my question:
The tutorial I followed told me that I don't want to install GRUB to the system bootloader, and that I should install it to my Ubuntu partition instead.  I'm using EasyBCD to boot Linux instead of the built-in MBR-edit feature that I guess a normal Ubuntu install uses.  But I can't figure out what to replace (hd0) with at this screen: [http://img519.imageshack.us/img519/9278/feistydual18cv5.png](http://img519.imageshack.us/img519/9278/feistydual18cv5.png) .  Partition #6 is my Ext3 partition for Ubuntu, so I've tried putting (hd6), (sda6), just (sda) I think, (hd0,6) and who knows what else - each time I wasted 15 minutes as Ubuntu installed up until 96% and then freaked out because I'd put in the wrong entry.  What do they expect me to type?

And the long version of my question:
I checked some tutorials to make sure I wouldn't wipe anything out (the language Ubuntu uses when it says "even partitions which you have removed will be erased!" scared me) and ended up following the directions on this one: [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu) .  Since the tutorial says to put GRUB on the Linux partition only because Vista gets nazi with its boot record or some such, I decided to do that.  Unfortunately, every time I tell the installer where to put GRUB I end up putting the wrong thing, and I don't find out until AFTER the install has already gotten to 96% 15 minutes later!

Now, according to the tutorial at [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first) , I don't have to worry about it and I can just install normally.  And I'm tempted to do that, but I think I read somewhere that your mbr can get screwed up and you won't be able to load Vista anymore without messing with it.  So I've just been trying to stick with what the first tutorial told me.  So here's the question: Let's say I'm at this screen [http://img519.imageshack.us/img519/9278/feistydual18cv5.png](http://img519.imageshack.us/img519/9278/feistydual18cv5.png) .  My ext3 partition is partition # 6, and it's sda.  What do I replace (hd0) with?  Or is any of this even necessary?

Final note: I've spent a bit looking at similar posts on this, but haven't found the answer yet.  I just need to know how I figure out what linux considers to be the name of my Ubuntu partition... wouldn't think it would be so hard...

---

### Post by logos34 on 2008-02-02
> **ElDudorino said:**
> I don't want to install GRUB to the system bootloader, and that I should install it to my Ubuntu partition instead.  I'm using EasyBCD... Partition #6 is my Ext3 partition for Ubuntu, so I've tried putting (hd6), (sda6), just (sda) I think, (hd0,6) and who knows what else - each time I wasted 15 minutes as Ubuntu installed up until 96% and then freaked out because I'd put in the wrong entry.  What do they expect me to type?

**(hd0,5)**

or 

**/dev/sda6**

---

