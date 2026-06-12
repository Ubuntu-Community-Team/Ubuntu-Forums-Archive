---
title: "low memory for virtual machine"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Bubs on 2007-07-10
using vmware server and trying to install windows 64bit (which I own a legal copy of) I had installed it once and deleted it but now I actually need to use it.  The problem occours when I boot the machine with the windows disk in about 10 min into the install a vmware message pops up saying the host machine doesn't have enought available memory to switch to 64 bit mode.  I click ok and the vm shuts down.

vmware, azureus, and wicd are the only things I have open and running.  I have 1gig of ram.  this really shouldn't be a problem.  right?

any suggestions.  similar problems...  hints, tips...

---

### Post by wormser on 2007-07-10
That error message sounds like you do not have enough memory on the host machine.  It is probably just because it is 64 bit.  Try a 32 bit install or add ram.

---

### Post by Eggnog on 2007-07-10
Don't quote me on this, but I think vmware has a default RAM of 192M when you create your VM.  Try raising that up a bit, maybe to 256 to start.  You have one gig so you could go to 512 I would think.

Edit:  Nevermind.  I just saw that your problem was on the host end.  Move along.  Nothing to see here.

---

### Post by Bubs on 2007-07-10
I don't have the 32bit cd I lost it...  and I don't want to add ram because this worked litterally 2 weeks ago.  I just wanted to make the vm bigger and I didn't know how to do that in an existing vm so I deleted and am now trying to make a new one.  i'll just mess with it until it's fixed or unusable...

---

### Post by wormser on 2007-07-12
Just a thought.  If you have another machine you could try creating the VM there then transfer the files over.  That might work if the problem is in just creating the VM.  Another thought is try lowering the amount of ram in the VM.  It would make sense to see an error like that if the VM was taking up too much ram.  Good luck.

---

### Post by Bubs on 2007-07-12
I would try that but no other machine.  but my luck is awsome this day because a buddy of mine returned my 32bit windows disk.  I forgot he even had it!

---

### Post by s[_]spect on 2007-07-12
If your happy to go with 32-bit then go for it. However if you need the 64-bit for whatever reason.. I would ask..
How much memory is allocated to the VM and if memory page trimming is enabled? As this allows the VM's memory to be swapped by the host.. It gets disabled for better performance but relies on the host having enough physical memory.
also check the vmx file for  sched.mem.pshare.enable=TRUE as this is not there by default.

---

### Post by Bubs on 2007-07-13
I have 256 mem for the vm.  where would I find the page trimming?  I'm new to vm's and  don't know much about it.  

and I don't really need the 64bit at the time it was the only windows disk I had.  all I need from windows is photoshop, dvddecrypter, and clonedvd.  thats all I was ever going to open it up for...

but I would like to know more...  I may try out some other distros of linux in vm so I don't have to mess with duel booting just to see if I like the flavor

thanks

---

### Post by s[_]spect on 2007-07-17
If you are using vmware server rather than player like i am then it is in the settings on the virtual machine.
Go to settings > options > advanced > should be under settings on the right. (note: depends on version of vmware as was not there in older versions) 
If using player, you need to edit the vmx file. Unfortunately I cant remember the way it is written in the vmx file.. will check some of my existing vms if any have it set.. will let you know.

---

### Post by s[_]spect on 2007-07-17
Further, If you go to preferences on the console itself, and go to memory.
See the additional memory section
Select the option that most suits your situation.. I disable swapping for performance, however if limited on ram, you can enable swapping.
Again, this will depend on software version

---

