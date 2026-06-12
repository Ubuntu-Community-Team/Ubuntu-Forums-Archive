---
title: "Virtualization question"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by ramzai on 2007-02-18
I have read a bit about different kinds of virtualizations, about vmware and xen, but one (and, probably, main) question remains:

Can I run EXISTING Windows XP install "in a window" under Ubuntu?
Feisty Fawn (2.6.20-8), CPU supports Intel VT.

---

### Post by shof2k on 2007-02-18
> **ramzai said:**
> I have read a bit about different kinds of virtualizations, about vmware and xen, but one (and, probably, main) question remains:

Can I run EXISTING Windows XP install "in a window" under Ubuntu?
Feisty Fawn (2.6.20-8), CPU supports Intel VT.

I think the sort answer is NO.

The way virtualisation works is that the cpu and pc guts are created in software (the VT stuff helps the modelling be done quicker).  The virtual pc would be different to the way your existing install works so it wouldn't work.

Saying that tho, it may be possible if you tweak the way vmware works.  I'm not saying this is easy, but it probably goes way beyond what the average user could do with virtualisation.

Hope that helps

---

### Post by G Morgan on 2007-02-18
It's possible but it is much easier to perform trivial tasks like walking on water.

You're better off just setting up a new one. If it is just file access you want then first mount the appropriate partition in Ubuntu (look up NTFS-3G if needed). Then mount it as a Samba share. It should then appear in 'My Network Places' in the VM.

---

### Post by ramzai on 2007-02-18
**shof2k**, **G Morgan**: thanks for your answers, I'll stay on a dual boot for a while((

---

### Post by kaihoko on 2007-02-20
You cannot run your existing install as is in vmware.  However, you can do a Physical to Virtual creation of the existing XP machine and then run that virtualized machine in vmware.

You can use the Vmware Convertor [http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/) to do this.  It is a free download.  

You don't loose anything either as it just clones the machine.

---

### Post by veloce on 2007-02-21
> **kaihoko said:**
> You cannot run your existing install as is in vmware.  

This is incorrect.  You CAN run your existing install in a vm under Ubuntu. 

As noted above, it's not easy to get it working.  Then, after you finally manage it, you find that it  is equivalent to using a hard drive from one machine in another - windows copy protection doesn't like it.

---

### Post by ramzai on 2007-02-21
**Veloce**
Any good howto?

---

### Post by veloce on 2007-02-21
> **ramzai said:**
> **Veloce**
Any good howto?

Unfortunately not, i haven't done it myself.  I would start here:

[http://pubs.vmware.com/server1/wwhelp/wwhimpl/js/html/wwhelp.htm](http://pubs.vmware.com/server1/wwhelp/wwhimpl/js/html/wwhelp.htm)

It's not quite what you need to do as you are hoping to use what is installed on the physical  partition rahter than installing another. 

but it covers the same issues you will need to consider: permissions being the big one.

---

### Post by gabng on 2007-02-22
According to RikoW in this thread: [http://www.ubuntuforums.org/showthread.php?t=365057&highlight=vmware+converter](http://www.ubuntuforums.org/showthread.php?t=365057&highlight=vmware+converter)

VMware workstation do support running a VM with the guest OS in the existing physical partition.

I went to the link he provided: [http://www.vmware.com/support/ws55/doc/disks_dualmult_ws.html#wp1046601](http://www.vmware.com/support/ws55/doc/disks_dualmult_ws.html#wp1046601)
and it does state VMware workstation have the option to to run a VM from a physical parition (under Configuring a Linux Host, step 6 and onwards).

Now I don't have any experience with that myself, but do intend to try this out, since it seems like a good way to migrate existing window users to linux.

---

### Post by xpod on 2007-02-22
Ok i`m certainly no expert of this stuff...or much of anything else PC when it come to it but surely the easiest way to do this virtual machine thing right now is  Virtualbox???...aint it?????

[http://www.virtualbox.org/](http://www.virtualbox.org/)

I have all kinds setup and although i only mess about it`s actually really easy to install and setup VB as well as  the subsequent VM`s themselves
The other methods  looked a bit complex for my own meager abilities or so i thought but VB made easy work of it for sure and it it`s just another great thing i`ve learned a liitle about this past year with a computer(besides just setting fire to  XP with beryl that is):twisted: 

Of course you need to have an XP cd or iso of some sort(i think) but as long as you have that much then setting up a Virtual XP,Vista or even a decent  VM like feisty with VB is a piece of cake:wink: 
It took me long enough to make a bootable XP cd from my dusty old files so the least i could do was test the thing eh:oops:...... thats my excuse:) 

Good luck either way

---

### Post by veloce on 2007-02-22
> **gabng said:**
> 
Now I don't have any experience with that myself, but do intend to try this out, since it seems like a good way to migrate existing window users to linux.

Exactly the reason I had a look at it.  However, I don't think it's going to work in that context for a number of reasons:
i[LIST=1]
[*]t is quite difficult to achieve - particularly for novice linux users
[*]Windows copy protection. The windows installation want to be re-authenticated because the "hardware" has changed significantly.
[/LIST]

At some stage I hope to try the following method:
[LIST=1]
[*]Make a virtual machine copy of the physical windows installation
[*]Change the vm so that the hard disk points to the physical
[/LIST]

My hope would be that the copy of the physical machine would have "hardware" as similar to the physical as possible.

---

### Post by gabng on 2007-02-22
> **veloce said:**
> Exactly the reason I had a look at it.  However, I don't think it's going to work in that context for a number of reasons:
i[LIST=1]
[*]t is quite difficult to achieve - particularly for novice linux users
[*]Windows copy protection. The windows installation want to be re-authenticated because the "hardware" has changed significantly.
[/LIST]


I just had a look at it now, installed the VMware server and got to the point of the window (on the existing partition) booting screen, and then BSOD.  I think it's because the underneath hardware is totally different between the physical machine and the VM that windows couldn't handle it even with it's plug and play.  If only there's a way to get pass this...

I got to this point simply by following the instructions to install the VMware server and then following the instructions [here]("http://www.vmware.com/support/ws55/doc/disks_dualmult_ws.html#wp1046601").

---

### Post by butter on 2007-02-22
This page has the best description I have found for utilizing a physical installation of windows in a virtual machine: [http://www.motin.eu/www/mirror/physvmware/]("http://www.motin.eu/www/mirror/physvmware/").
After a significant amount of trouble I was successful.  The performance is quite good.  The major caveats are that you can't take a snapshot, and, as mentioned previously, you will run into the "windows protection activation".  Still after a call to Microsoft, I was able to activate.  But here's the rub: you will again need to reactivate if you boot into Windows natively.  I understand why this is, but I believe it is within my rights to do this under the EULA, which solely requires that I only make one install and only run the os on one processor.  I have not reinstalled ( still running original installation) and the device manager inside Windows (inside vmware) still correctly identifies my processor.  I am going to take this to Microsoft tech support.  Any advice?

oh yeah, link to microsoft community discussion: [http://forums.microsoft.com/Genuine/ShowPost.aspx?PostID=732200&SiteID=25]("http://forums.microsoft.com/Genuine/ShowPost.aspx?PostID=732200&SiteID=25")

---

### Post by veloce on 2007-02-23
> **butter said:**
> I am going to take this to Microsoft tech support.  Any advice?


Yeah, organise nice padded walls to bang your head against!  

The very best response I'd expect from them would be along the lines of "Okay, maybe it doesn't break your EULA, but we have no intention of changing WPA for you."

---

### Post by butter on 2007-02-23
I know, I know... Don't expect too much.  But hey they've reauthorized me a few times.  If they were to give me two wpa codes could windows handle this or would I have to enter them each time I did either native or vm boot.  I love the ease of the vm boot, but I'd like to have 3d acceleration from native when I need it.

---

