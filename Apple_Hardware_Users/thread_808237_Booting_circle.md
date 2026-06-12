---
title: "Booting circle ?"
date: 2008-05-26
forum: Apple Hardware Users
---

### Post by gtppc on 2008-05-26
I have installed ubuntu ppc 8.04 to my G5 desktop (1.6).

I power up and hold 'alt' - I then have the onscreen icons for which os to boot. I have 3 icons: my Mac OS X partiton. my firewire external clone partition - and the linux os with the penguin(?) on the drive icon.

I choose the linux with the mouse then press the arrow to proceed. Computer then goes to the text screen. It tells me press 'L' or 'X' or 'C. I press L then it goes back to the icons - and so on.

Any ideas anyone?

Thanks

gtppc

---

### Post by frog_pilot on 2008-05-26
recently there was a [discussion]("http://ubuntuforums.org/showthread.php?t=800041") of a similar problem. Try these suggestions and report your success...

---

### Post by stream303 on 2008-05-26
Sounds like something got weird in openfirmware.

I'd boot into a rescue shell from an install disk, and at the second yaboot boot: prompt, hit -tab- to stop the countdown, and type:

```
rescue-powerpc
```

(or whatever rescue option is shown, ie rescue-powerpc64 for G5's) and then get to a shell on your root partition.  For default installs where guided partitioning did it all automatically for you, it will probably end up being /dev/sda3 or /dev/hda3 etc.

Then as long as your /etc/yaboot.conf file is ok, redo ybin

```
ybin -v -C /etc/yaboot.conf
```

In the rescue mode, you are already operating as root, so no need for sudo.  Exit the shell (just type *exit* and reboot.

Ideally it should no longer go into a loop..

---

### Post by stueng on 2008-05-27
Have you considered using rEFIt?

[http://refit.sourceforge.net/]("http://refit.sourceforge.net/")

I have created some instructions on how to get it working an Apple Mac's

[http://www.lostpeg.co.uk/content/view/29/71/]("http://www.lostpeg.co.uk/content/view/29/71/")

---

### Post by stream303 on 2008-05-27
For the ppc machines, rEFIt might not work - as much as we'd like it to. :)

---

### Post by gtppc on 2008-05-27
I'm still not getting anywhere.

I don't have the ability to know how to do things with command lines. It would have to be very clear procedure for me to follow.

Thanks for the information about rEFIt - but it seems this is only for intel macs.

I'm stuck :(

How have others managed to get Ububtu running on power pcs?

gtppc

---

### Post by cyberdork33 on 2008-05-27
> **stream303 said:**
> For the ppc machines, rEFIt might not work - as much as we'd like it to. :)
I can't decide if you guys are better off with OF instead of EFI or not :)

Ok Off-topic...

---

### Post by stream303 on 2008-05-27
> **gtppc said:**
> I don't have the ability to know how to do things with command lines. It would have to be very clear procedure for me to follow.

If you can boot OSX, can you go into disk-utility and specify the Ubuntu drive to boot from?  (It's been awhile so I'll have to check that myself...)

As frustrating as OF or rEFIt can be at times, I'm still amazed that Apple didn't do a total lock-in. :)

---

### Post by gtppc on 2008-06-01
**SUCCESS** - I have installed onto my laptop ppc.

I made the 2nd partition free space and then installed into largest free space.

The laptop now dual boots without any problems. I have downloaded updates and things seem to be going well.

Dont know what the issue is with the desktop. Maybe I need to re-partition and reinstall. I may do this at some future date. For now I am into the Ubuntu community.

Thanks everyone for suggestions.

gtppc

---

### Post by stream303 on 2008-06-02
Allright!  Thanks for reporting back the success story - always good to hear.  Take a breather, and let us know what's up with the G5 problems...

---

### Post by Scientia on 2008-06-02
> **gtppc said:**
> **SUCCESS** - I have installed onto my laptop ppc.

I made the 2nd partition free space and then installed into largest free space.

The laptop now dual boots without any problems. I have downloaded updates and things seem to be going well.

Dont know what the issue is with the desktop. Maybe I need to re-partition and reinstall. I may do this at some future date. For now I am into the Ubuntu community.

Thanks everyone for suggestions.

gtppc

Gee, you got that far? I couldn't even get the dual-boot partition installing part right for nuts...:) Now running perfectly on the entire disk, laptop ppc like yours btw.  Sheesh, if someone could help me on partitioning then being able to dual boot...but that would mean having to wipe my drive again wouldn't it?

---

