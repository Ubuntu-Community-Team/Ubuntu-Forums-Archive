---
title: "[SOLVED] GParted Help Please"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by rtr86 on 2007-09-24
Hi guys,

I want to format/Partition a 160G IDE hard drive ready for XUbuntu. I already have the latest gparted ISO and can get into the interface but I don't know how I partition it, can anyone please help? 

Ive done a form search but most posts are people talking about using a windows partition as well or more then 1 hard drive. I have just 1 hard drive I want devoted to xubuntu.

Also, i was hoping there would of been a derag app included on the .iso - I cant find 1 though?

Thanks

---

### Post by mikewhatever on 2007-09-24
First, if there will only be Xubuntu on that drive, choose the automatic option on the live CD. In case you must go manual, [http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning).
There is no defrag option in linux, what do you want to defrag anyway?
Here is a good source on how to use Gparted [http://www.google.co.il/search?q=gparted+documentation&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.il/search?q=gparted+documentation&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by Dr Small on 2007-09-24
Linux doesn't need defragging, so there is no need for that.

Dr Small

---

### Post by laidback on 2007-09-24
Remember that once you have you Ubuntu installed you will still need to boot from your Live Gparted CD to adjust your single hdd partition(s) as you cannot modify mounted (active) partitions.

---

### Post by rtr86 on 2007-09-24
Thanks for replys guys but i am still very lost :(

I have been looking at the documentation (for gparted) and although its very detailed about how to use the application I can't find anything about how partions work on linux, or the ones required (e.g root,user swap, boot) or the size they should be set at.

I'll keep leanring but any help you can offer is appricated.

Thanks

---

### Post by psusi on 2007-09-24
Actually there is a defrag package that works on ext2/3, but yes, it is of little to no practical value.

---

### Post by bigken on 2007-09-24
this a typical partition 

/ 10 gig (system)

swap twice your ram ie 512mb = 1gig 


/home the rest

---

### Post by rtr86 on 2007-09-24
> **bigken said:**
> this a typical partition 

/ 10 gig (system)

swap twice your ram ie 512mb = 1gig 


/home the rest


Thanks for that. I don't know if its a problem with me (probably) but i can find a set swap fine, but i can see how to set any other file types?

Thanks

---

### Post by bigken on 2007-09-24
> **rtr86 said:**
> Thanks for that. I don't know if its a problem with me (probably) but i can find a set swap fine, but i can see how to set any other file types?

Thanks


you can do this from the live cd

---

### Post by rtr86 on 2007-09-24
> **bigken said:**
> you can do this from the live cd

Thanks for reply,

I just went back into gparted and selected system as exc2 - 10gig
and linux swap as 1gig.

Do i need to set any kind of flags i.e root, user?

Should I now load the xubuntu cd and select auto at partiton stage (as partitions sohould already be created?)

Thanks

---

### Post by oldos2er on 2007-09-24
If you're going to use the entire disk for Xubuntu, you really don't need to run the gparted cd. Just boot from the Xubuntu live cd, and when you get to the appropriate point in the installation, choose 'Guided--use entire disk.' A swap partition should be created automatically. The installer defaults to ext3 file system.
 Creating separate partitions for /home and/or /boot are really matters of personal preference. There's some info about it here: [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

---

### Post by rtr86 on 2007-09-24
> **oldos2er said:**
> If you're going to use the entire disk for Xubuntu, you really don't need to run the gparted cd. Just boot from the Xubuntu live cd, and when you get to the appropriate point in the installation, choose 'Guided--use entire disk.' A swap partition should be created automatically. The installer defaults to ext3 file system.
 Creating separate partitions for /home and/or /boot are really matters of personal preference. There's some info about it here: [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

Thanks for reply, that is what i initially did but I kept geeting this error:

'The ext3 filesystem creation in partition 1 of IDE1 (HDA) Failed.'

I thought using gparted to create the partitions could be a workaround.

Regards

---

### Post by rtr86 on 2007-09-24
Any help appriciated :)

---

### Post by rtr86 on 2007-09-25
Still really stuck so would appreciate ANY help. I keep getting that same error message every time even though I have formatted the drive.

---

### Post by [Alsharifi] on 2007-09-25
im not exactly sure what your question is but.

this is how i set up my partion

i made one 15 gb extended partition

then set 1.5 gb linux swap logical partion

and the rest of (bout 13.5 gb) for my ext3 ubuntu partion

does that help at all ?

it would look like this [http://hevnikov.com/img/061113-gparted-apply.png](http://hevnikov.com/img/061113-gparted-apply.png)

---

### Post by rtr86 on 2007-09-25
Thanks for all replies :)

I'm now posting this to you on my xubuntu setup! Someone posted earlier saying to try the the xubuntu alternative disk rather then the 'destop' one which worked. I installed the OS via text mode which went without problems.

Again, Huge thanks!

---

### Post by laidback on 2007-09-25
I suspect that AUTO will override what you have already created, although I have happily installed several Ubuntus and have always used the Auto option at the installation stage.

---

### Post by bigken on 2007-09-25
please your up and running now enjoy ride :)

---

