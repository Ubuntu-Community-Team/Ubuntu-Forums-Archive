---
title: "Ubuntu Solo"
date: 2008-07-22
forum: Apple Hardware Users
---

### Post by TedPacyga on 2008-07-22
Hey I have looked around but didn't get the answer I was looking for.  I just got a new 15" Macbook Pro and was wondering if it is possible to install Ubuntu as the only operating system.  That means no Mac OS X.  As to whether or not I will do this in the end, I don't know, but I want to know if it is possible.  

Is it also possible to boot Ubuntu as default and not OS X if you have a dual boot?

Also, I saw rEFI, but how do I make that work?  I want to be able to see BIOS like settings, this is what it does right?

Sorry if there is any typos or something I am at work and typing fast.  Thanks.

---

### Post by kdb424 on 2008-07-22
[http://ubuntuforums.org/showpost.php?p=5166788&postcount=21](http://ubuntuforums.org/showpost.php?p=5166788&postcount=21)

That's what you are looking for, but why have apple and not OSX. Might as well sell that and get something better hardware wise, make ubuntu installing slightly easyer, and not have to worry about any issues. I have seen laptops that come with Ubuntu installed and they go cheep, but are still great!

---

### Post by TedPacyga on 2008-07-22
That is exactly what I was looking for, thank you.  Is that method reverseable though?  If I ever would want to put back to factory settings I believe I'd be able to, but just making sure.  Also, that answered my question on rEFI.

The reason I would get rid of Mac OS X and just use Ubuntu is that I love Ubuntu and I thought it be cool if I could virtual machine xp vista and osx, would it be possible to do that, would I be able to get os x to run as normal through a virtual machine

---

### Post by kdb424 on 2008-07-22
Ubuntu is great I agree. Yes, you could go back with the install disk. Mac OS X will never run in a virtual machine well. Someone will come in this topic and tell you MOL (Mac on linux), but I have found little success running that well even on apple hardware. You can however run Mac OS X server in VMware fusion on the Mac though. lol. Anything else that I can help you with?

---

### Post by TedPacyga on 2008-07-22
I was actually planning on using vmware fusion to run os x, is that bad?  Besides that I think you pretty much cleared it up for me thanks.  Oh yeah one more thing, when I tried the Ubuntu live cd on the macbook pro, the touchpad feels very different than on os x, it isn't as smooth as in os x, if you know what I am talking about will installing the multi touch touchpad driver thing for linux make the touchpad smoother.  I am looking for the smoothness not neccessarily the multi touchness.  Hopefully this happened to other people and you know what I mean.

---

### Post by cyberdork33 on 2008-07-22
> **TedPacyga said:**
> Hey I have looked around but didn't get the answer I was looking for.  I just got a new 15" Macbook Pro and was wondering if it is possible to install Ubuntu as the only operating system.  That means no Mac OS X.  As to whether or not I will do this in the end, I don't know, but I want to know if it is possible.Yes, you can, there are a few people here that have done that.  

> **TedPacyga said:**
> Is it also possible to boot Ubuntu as default and not OS X if you have a dual boot?Yes, rEFIt will allow this.

> **TedPacyga said:**
> Also, I saw rEFI, but how do I make that work?  I want to be able to see BIOS like settings, this is what it does right?Not really. rEFIt is just a "boot menu" You get nearly the same effect by holding option on startup. rEFIt does include some nifty tools though such as an EFI shell, and a Partition Sync utility. Theoretically you could access EFI settings through the EFI shell, but I would not recommend messing with that too much.

> **TedPacyga said:**
> That is exactly what I was looking for, thank you.  Is that method reverseable though?  If I ever would want to put back to factory settings I believe I'd be able to, but just making sure.  Also, that answered my question on rEFI.If you mean uninstall rEFIt, then yes. [http://refit.sourceforge.net/doc/c1s3_remove.html](http://refit.sourceforge.net/doc/c1s3_remove.html)

> **TedPacyga said:**
> The reason I would get rid of Mac OS X and just use Ubuntu is that I love Ubuntu and I thought it be cool if I could virtual machine xp vista and osx, would it be possible to do that, would I be able to get os x to run as normal through a virtual machineNo. If you want to use OS X, just dual boot. Some progress has been made in getting OSX to run in a VM, but it is buggy, and due to legal reasons (and forum rules) I won't go into much detail. Personally, I use OSX most of the time, but I dual boot with Ubuntu and also have an Ubuntu install in VirtualBox on my OSX side just in case I need to get to something quickly.

> **TedPacyga said:**
> Oh yeah one more thing, when I tried the Ubuntu live cd on the macbook pro, the touchpad feels very different than on os x, it isn't as smooth as in os x, if you know what I am talking about will installing the multi touch touchpad driver thing for linux make the touchpad smoother. I am looking for the smoothness not neccessarily the multi touchness. Hopefully this happened to other people and you know what I mean.That will likely be more reliant on how you tweak the synaptic settings.

---

### Post by TedPacyga on 2008-07-22
Thanks, I kind of like OS X, so I think I will either dual boot Ubuntu or use parallels, I havn't looked into parallels much, it is like a virtual machine but better right?  Becuase you can switch which operating system to use instead of using two at once?  But I will remain functinality of all the os x features when I parallel into ubuntu such as multitouch on touchpad and dashboard buttong, am I right?

---

### Post by cyberdork33 on 2008-07-22
> **TedPacyga said:**
> Thanks, I kind of like OS X, so I think I will either dual boot Ubuntu or use parallels, I havn't looked into parallels much, it is like a virtual machine but better right?  Becuase you can switch which operating system to use instead of using two at once?  But I will remain functinality of all the os x features when I parallel into ubuntu such as multitouch on touchpad and dashboard buttong, am I right?
parallels is just another VM. I don't quite know what you are asking about switching between, etc. The VM runs within your host OS. Some VMs have nice features that allow fullscreen, and window integration, but it is still a VM.

No VM currently supports 3D acceleration outside of Windows as a guest. This means no Compiz :(

I would consider VirtualBox (Free) and VMWare Fusion before parallels. They tend to play nicer with Linux.

---

### Post by TedPacyga on 2008-07-22
Oh I see, I must be mistaken about something.  I saw some videos on youtube of people saying they are running Ubuntu on parallels and they would press a button and the screen would flip over to the other operating system, so I am guessing that is just a visual effect of a virtual machine.  I will check out those two vms thanks.

---

### Post by cyberdork33 on 2008-07-22
> **TedPacyga said:**
> I saw some videos on youtube of people saying they are running Ubuntu on parallels and they would press a button and the screen would flip over to the other operating system, so I am guessing that is just a visual effect of a virtual machine.
Yes. I have also seen someone link into the sudden motion sensor so that you could "slap" the side of the screen, and it would change to the other OS.

---

### Post by kdb424 on 2008-07-22
> **cyberdork33 said:**
> Yes. I have also seen someone link into the sudden motion sensor so that you could "slap" the side of the screen, and it would change to the other OS.

That's called slapbook and that is a virtual machine that runs full screen in (usually in vmware fusion) and just changes spaces.

---

