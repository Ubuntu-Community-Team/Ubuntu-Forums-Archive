---
title: "Now I Have 4GB of RAM and my Comp is Really Slow"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by videocheez on 2008-02-17
I have a dual boot with XP Pro and Gutsy that originally had 2GB of RAM.  Memory finally went on sale and I bought another 2GB last week.  XP had no  problems seeing the additional memory although instead of seeing 2GB, I only see 3.25GB.  
In Ubuntu however, booting up and its response became really slow and basically unusable.  Does anyone have a suggestion to help my computer act normal with the extra memory.  I also upgraded my motherboards BIOS last week so perhaps this could be part of the problem too.  Any help will be appreciated

Thanks in advance ,

VC

---

### Post by randomnote1 on 2008-02-17
it sounds as if one of the memory sticks you have is bad.  You should try reseating the memory.  If that fails then swap the two new dimms out with the two old dimms and see if it works that way.  basically process of elimination.  Also for good measure check your /var/adm/messages for memory errors.

---

### Post by JoshuaRL on 2008-02-17
Shouldn't be the BIOS, Linux doesn't care much about that.  Have you changed anything else recently?

With the RAM, that's the most that XP will ever see, even if you installed 40GB.  32bit systems can only see a total of 4gb of memory.  So with the processor cache and the windows pagefile, the most you'll see recognised is 3.2GB.  Sorry.  Theoritically, 64bit machines can see **exabytes** of RAM.  Imagine the programs you could run on a machine like that!

---

### Post by randomnote1 on 2008-02-17
That's not completely true.  Microsoft limits the amount of memory XP can see.  I thought the limit was around 2GB, but I know the server versions can see up to 32 GB

---

### Post by kbless7 on 2008-02-17
> **randomnote1 said:**
> That's not completely true.  Microsoft limits the amount of memory XP can see.  I thought the limit was around 2GB, but I know the server versions can see up to 32 GB

And that is completely false. It is a limit of 32 bit systems to only recognize about 3.2 Gb while 64 is unlimited*. Do some research first. Microsoft isn't a complete ****.

---

### Post by dcstar on 2008-02-17
> **videocheez said:**
> I have a dual boot with XP Pro and Gutsy that originally had 2GB of RAM.  Memory finally went on sale and I bought another 2GB last week.  XP had no  problems seeing the additional memory although instead of seeing 2GB, I only see 3.25GB.  
In Ubuntu however, booting up and its response became really slow and basically unusable.  Does anyone have a suggestion to help my computer act normal with the extra memory.  I also upgraded my motherboards BIOS last week so perhaps this could be part of the problem too.  Any help will be appreciated

Thanks in advance ,

VC

Change the memory Ubuntu uses with the Grub boot string, and example of how to do this is here:

[http://ubuntuforums.org/showpost.php?p=3444120&postcount=13](http://ubuntuforums.org/showpost.php?p=3444120&postcount=13)

Then you can see if it is Ubuntu or your hardware.

---

### Post by bumanie on 2008-02-17
you could do a memory+86 test and check that your ram sticks are OK. Problem doing this is that if there are errors you then have to scan each one separately, until you find which one/s are faulty. As stated already double check that they are seated properly.

---

### Post by randomnote1 on 2008-02-17
> **kbless7 said:**
> And that is completely false. It is a limit of 32 bit systems to only recognize about 3.2 Gb while 64 is unlimited*. Do some research first. Microsoft isn't a complete ****.

I stand corrected about the XP memory limit.  However Microsoft is still a complete imbecile.  The limited the Server 2003 Web edition to 2 GB of memory, Standard Edition to 4GB, Enterprise Edition to 32 GB and DataCenter gets the whole way up to 64 GB.  And I am pulling these numbers straight out of my 2003 Server book for 32 bit systems.  Plus M$ limits the number of Processors that Windows will recognize.

But anyway...for the windows side of this problem, try disabling the pagefile and it should be able to see all the memory.  I Googled for this issue and found a bunch of results that stated that worked for them.

---

### Post by maniac_X on 2008-02-17
before you do an extensive testing of the ram, pull out the 2 older sticks and leave the newer ones in and see if XP/Ubuntu act as they did before you installed the extra ram. this will help in further identifying if the newer sticks are a problem or not. then run the memtest on each stick individually. It could also be the motherboard. some mobos can get pickier the more ram you add.

---

### Post by JoshuaRL on 2008-02-17
> **randomnote1 said:**
> I stand corrected about the XP memory limit.  However Microsoft is still a complete imbecile.  The limited the Server 2003 Web edition to 2 GB of memory, Standard Edition to 4GB, Enterprise Edition to 32 GB and DataCenter gets the whole way up to 64 GB.  And I am pulling these numbers straight out of my 2003 Server book for 32 bit systems.  Plus M$ limits the number of Processors that Windows will recognize.

But anyway...for the windows side of this problem, try disabling the pagefile and it should be able to see all the memory.  I Googled for this issue and found a bunch of results that stated that worked for them.

That's not an XP problem, that's a 32bit problem.  The way x86 is written, it needs a definite address for each memory position.  So with a 32bit processor, you can only have 4gb of memory.  And with the way XP is written, you will only see 3.3gb of that is recognised as RAM in the system.  Yes, if you disable the page file you will see more in there.

As far as the Server Edition, I'm not sure what that means.  Are you sure that isn't per array?  Because 32bit shouldn't be physically able to see anywhere near 64gb of RAM.

With x86-64, I believe the limit is in the exabytes.  That's because it's only halfway 64bit, since it was written to be backwards compatable.  True 64bit computing doesn't even understand 32bit, can't be made to without heavy virtualization, and I'm not sure even then.  However, it should be able to recognise near infinite amounts of RAM.

As far as your exact problem goes OP, the suggestions here are sound.  First, swap out the old RAM to see if the problem changes.  Then, run a memtest on the new RAM.  If you're having this serious of issues, I would suggest you leave it overnight and see what it's doing in the morning.  If it's neither of those, then it's probably a software issue.  If that's the case I would suggest you try and remember anything you've changed recently.  That could give us some clues as to where to start.

---

### Post by videocheez on 2008-02-17
> **dcstar said:**
> Change the memory Ubuntu uses with the Grub boot string, and example of how to do this is here:

[http://ubuntuforums.org/showpost.php?p=3444120&postcount=13](http://ubuntuforums.org/showpost.php?p=3444120&postcount=13)

Then you can see if it is Ubuntu or your hardware.

I would like to try what you have suggested but Ubuntu is all screwed up.  I don't even see the top bar that allows me to get into the applications, places and system.  Shall I try what is suggest at the link that you given me by loading Ubuntu from the CD?

Thanks in advance,

VC

---

### Post by randomnote1 on 2008-02-17
when you boot up you will need to select boot into restricted mode.  It should be a command line environment, although I'm not to sure about that having not worked in restricted mode myself.  But when you get into a command line, you'll have to type in grub and use that program to manipulate the bootup line.  I haven't had to do this myself for quite some time, so I'd check around the forums for more specific guidance on how to edit the grub boot line.

---

### Post by videocheez on 2008-02-18
> **JoshuaRL said:**
> Shouldn't be the BIOS, Linux doesn't care much about that.  Have you changed anything else recently?

With the RAM, that's the most that XP will ever see, even if you installed 40GB.  32bit systems can only see a total of 4gb of memory.  So with the processor cache and the windows pagefile, the most you'll see recognised is 3.2GB.  Sorry.  Theoritically, 64bit machines can see **exabytes** of RAM.  Imagine the programs you could run on a machine like that!
I think an exabyte of mem would cost a few bucks.

---

### Post by JoshuaRL on 2008-02-18
Yeah, but by the time you had a motherboard that supported it and programs that needed it, it would be pretty cool.  I guess I'm a pseudo-RAM-theorist.

---

### Post by dcstar on 2008-02-18
> **videocheez said:**
> I would like to try what you have suggested but Ubuntu is all screwed up.  I don't even see the top bar that allows me to get into the applications, places and system.  Shall I try what is suggest at the link that you given me by loading Ubuntu from the CD?

Thanks in advance,

VC

That is changing Grub, you do that at the Grub boot screen, well before Ubuntu loads.

If things are not fully visible on your screen, then use the "Auto" function to sync your monitor so all is visible.

---

### Post by videocheez on 2008-02-18
> **JoshuaRL said:**
> 

As far as your exact problem goes OP, the suggestions here are sound.  First, swap out the old RAM to see if the problem changes.  Then, run a memtest on the new RAM.  If you're having this serious of issues, I would suggest you leave it overnight and see what it's doing in the morning.  If it's neither of those, then it's probably a software issue.  If that's the case I would suggest you try and remember anything you've changed recently.  That could give us some clues as to where to start.

As I mentioned, I have a dual boot computer with windows and Ubuntu.  I don't believe that there is a memory problem.  I already had 2GB of RAM and I just added two more.  I understand about the 32 bit systems not being able to see more than 3.3GB of RAM.  The reason I don't think the memory is defective because when I boot to Windows, I see 3.25GB RAM.  When I boot to Ubuntu, the computer is running incredibly slow. In fact the computer not only runs really slow in Ubuntu, but it also is not really operational.  The menu bar at the top of my desktop doesn't even show up.

The changes I have made to my computer since the last time I booted to Ubuntu were adding an additional 2GB of RAM and updating the BIOS.  Do you think I should reinstall Ubuntu from the CD?  If so, how would I go about this?  How can I get to a command line and what can type there to change the memory requirements.  

In my limiited opinioin, it appears that the Ubuntu software cannot easily handle the change of adding another 2GB of RAM.  I'm sure if I had 4GB of RAM already when I did the Gutsy upgrade a few months back, all would be fine.

Any suggestions would be appreciated.

DS

---

### Post by stchman on 2008-02-18
32bit OSes can directly address 4GB of RAM.  The reason is that 2^32 = 4096MB.

64bit OSes can address 1.76e13 MB of RAM.  That is because it is 2^64.

Now there are bus limitations as you have to make sure the bus it 64 bit as well.

---

### Post by philinux on 2008-02-18
Just for information.

Microsoft solved the memory limit problem some time ago with something called Physical Address Extension (PAE). It bumps the memory address system to 36 bits. Technically the limit for 36 bit being 64Gb. So xp and vista are deliberately crippled by M$ as the server 2003 datacentre edition can see the 64GB.

---

### Post by johnnybirdman on 2008-02-18
> **videocheez said:**
> As I mentioned, I have a dual boot computer with windows and Ubuntu.  I don't believe that there is a memory problem.  I already had 2GB of RAM and I just added two more.  I understand about the 32 bit systems not being able to see more than 3.3GB of RAM.  The reason I don't think the memory is defective because when I boot to Windows, I see 3.25GB RAM.  When I boot to Ubuntu, the computer is running incredibly slow. In fact the computer not only runs really slow in Ubuntu, but it also is not really operational.  The menu bar at the top of my desktop doesn't even show up.

The changes I have made to my computer since the last time I booted to Ubuntu were adding an additional 2GB of RAM and updating the BIOS.  Do you think I should reinstall Ubuntu from the CD?  If so, how would I go about this?  How can I get to a command line and what can type there to change the memory requirements.  

In my limiited opinioin, it appears that the Ubuntu software cannot easily handle the change of adding another 2GB of RAM.  I'm sure if I had 4GB of RAM already when I did the Gutsy upgrade a few months back, all would be fine.

Any suggestions would be appreciated.

DS

Use the live cd and do the mem test as suggested above.  You can re-add the panel at the top if you want by right clicking the other panel and tell it to  'add panel'.   I also recently went from 2 to 4GB of mem with no problems.  I doubt the problem is with Ubuntu.

---

### Post by videocheez on 2008-02-18
> **johnnybirdman said:**
> Use the live cd and do the mem test as suggested above.  You can re-add the panel at the top if you want by right clicking the other panel and tell it to  'add panel'.   I also recently went from 2 to 4GB of mem with no problems.  I doubt the problem is with Ubuntu.
Okay I ran the mem test and everything looked okay.  I decided to reboot ubuntu with 2GB memory and now everything is working perfectly just as it did before.  It seems as the way that I have Ubuntu set up, it does not like the extra memory.  Its kind of pain in the butt to have a dual boot scenario where I have to take out memory to use Ubuntu.  Does any one have an idea how I can set up Ubuntu to work with 4G?  I don't understand how to apply the following suggested code:
 ```

title		Ubuntu, kernel 2.6.20-16-lowlatency 500MB RAM
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-16-lowlatency root=UUID=88e2c353-0fc8-4ebf-a9ff-aad9f073d692 ro quiet splash noapic mem=500M
initrd		/boot/initrd.img-2.6.20-16-lowlatency
quiet
savedefault

```
Is there a simple way to reinstall Ubuntu without losing all of my settings?  

Thx in advance,

VC

---

### Post by dcstar on 2008-02-19
> **videocheez said:**
> Okay I ran the mem test and everything looked okay.  I decided to reboot ubuntu with 2GB memory and now everything is working perfectly just as it did before.  It seems as the way that I have Ubuntu set up, it does not like the extra memory.  Its kind of pain in the butt to have a dual boot scenario where I have to take out memory to use Ubuntu.  Does any one have an idea how I can set up Ubuntu to work with 4G?  I don't understand how to apply the following suggested code:
 ```

title		Ubuntu, kernel 2.6.20-16-lowlatency 500MB RAM
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-16-lowlatency root=UUID=88e2c353-0fc8-4ebf-a9ff-aad9f073d692 ro quiet splash noapic mem=500M
initrd		/boot/initrd.img-2.6.20-16-lowlatency
quiet
savedefault

```
Is there a simple way to reinstall Ubuntu without losing all of my settings?  

Thx in advance,

VC

Install the current generic kernel and see what happens - that kernel you are using is ancient and "low latency" is no longer made.

---

### Post by sailor2001 on 2008-02-19
are you defaulting into gxl, beryl, compiz?  do:' metacity --replace'

---

### Post by videocheez on 2008-02-19
Yes I have compiz as default.  What is the result of?
```

metacity --replace.

```

---

### Post by sailor2001 on 2008-02-19
loss of top bar indicates beryl, compiz is using up your video memory resource. I'm not on ubuntu, but I believe if you go to your home and click ctrl/h and open gnome2 and delete profile and restart session ( ctrl/alt/backspace) it will reset the profile

---

