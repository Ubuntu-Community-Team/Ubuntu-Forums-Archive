---
title: "Installing Ubuntu and MB drivers"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by Dr. Tom on 2008-03-16
Hi:

New to this site and Ubuntu.

I have a ECS Elitegroup KAGeForce6100sm-m motherboard.  It has on-board audio, video, and LAN.  I will use it with 2GB of RAM and 160 GB hard drive.

I have checked a few posts concerning drivers, but do not believe they fully apply to me.  Here are my questions.

1)  ECS does not have Linux drivers.  Will Ubuntu automatically recognize the North Bridge, South Bridge, Audio, Video, LAN, and USB ports and install the correct drivers?

2)  IF Ubuntu does not have drivers, where can I get Linux drivers for my motherboard?

3)  I have downloaded Ubuntu and copied it to a CD.  During the install process, will Ubuntu support partitioning and formating of the hard drive?

I have been playing with computers since 1965.  I don't believe Linux will be anywhere as difficult as some I used.  It looks a lot like AppleSoft to me and I really enjoyed that.  But I may be in for a surprise.

I am better at following books than verbal type instructions.  I have seen several books for sale about Ubuntu.  I would also appreciate a recommendation for a good Ubuntu book.

Thanks for your time and help,

Tom

---

### Post by MasterJS on 2008-03-16
Well, if you burned the Ubuntu CD correctly, you should be able to boot into the Live CD. You can use that to try ubuntu for yourself and see if all your hardware works. The Live CD functions like the OS itself, the only difference being that you can't save any settings.

---

### Post by bsharp on 2008-03-16
1.Go ahead and boot up a live cd and for anything that doesn't work, look around the web and these forums for linux compatibility, for sound, go to [http://alsa-project.org](http://alsa-project.org)

2.look above

3.Yes, there is partition and formatting support in both the live-cd and the alternate.

for a book look for Ubuntu Unleashed, it is over 800 pages and very helpful, even though it is a little dated (Dapper 6.06).  I believe there is a free online version as well, but I went ahead and dropped the $50 on the paperback because I find them easier to follow than a e-book.

---

### Post by bruce89 on 2008-03-16
> **Dr. Tom said:**
> 
1)  ECS does not have Linux drivers.  Will Ubuntu automatically recognize the North Bridge, South Bridge, Audio, Video, LAN, and USB ports and install the correct drivers?

The Linux kernel would be pretty useless without drivers for common things like these. The only issue may be with older kernels (it's difficult for a kernel to support hardware that didn't exist when it was written).

External drivers are a pain in the ****, and not worth bothering with (they tend to be buggy).

---

### Post by PeterJS on 2008-03-16
> **Dr. Tom said:**
> Hi:

New to this site and Ubuntu.

I have a ECS Elitegroup KAGeForce6100sm-m motherboard.  It has on-board audio, video, and LAN.  I will use it with 2GB of RAM and 160 GB hard drive.

I have checked a few posts concerning drivers, but do not believe they fully apply to me.  Here are my questions.

1)  ECS does not have Linux drivers.  Will Ubuntu automatically recognize the North Bridge, South Bridge, Audio, Video, LAN, and USB ports and install the correct drivers?

2)  IF Ubuntu does not have drivers, where can I get Linux drivers for my motherboard?

Well you stated that there are no closed drivers for your mother board, so the only linux drivers that could possibly exists are open source drivers. All open source device drivers are maintained in the kernel itself and will be automatically installed. The only reason ubuntu wouldn't have them is because they don't exist to be had.

> 
3)  I have downloaded Ubuntu and copied it to a CD.  During the install process, will Ubuntu support partitioning and formating of the hard drive?

The install/liveCD includes the GParted partitioner, and it's run as one of the earlier steps of the install process.

> 
I have been playing with computers since 1965.  I don't believe Linux will be anywhere as difficult as some I used.  It looks a lot like AppleSoft to me and I really enjoyed that.  But I may be in for a surprise.

I am better at following books than verbal type instructions.  I have seen several books for sale about Ubuntu.  I would also appreciate a recommendation for a good Ubuntu book.

I can't recommend any good books as most authors stick to the more commercial red hat branches of the linux family tree. I can however offer a couple of links to good community documentation:

Aysiu's guide to just about everything:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

The guide to installing anything:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

And of course, here, feel free to ask, it gives us volunteers things to do.

---

### Post by Dr. Tom on 2008-03-16
Thank you all for the quick replies.  I will give it a shot tomorrow or Tueday.

Your explanations cleared up things a lot more.  Everything is beginning to make sense and I now can see why Linux is so good.  I expect I will have a lot of fun with it.

Also, I appreciate the advice and references.

Tom

---

