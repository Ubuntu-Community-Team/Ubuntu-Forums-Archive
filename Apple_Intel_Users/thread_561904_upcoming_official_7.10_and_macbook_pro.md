---
title: "upcoming official 7.10 and macbook pro"
date: 2007-09-28
forum: Apple Intel Users
---

### Post by phonky on 2007-09-28
Hi

I'm running 7.04 on a macbook pro for +- 4 months now.
I've used linux on PCs for years before.

I like it, but there are a few things which prevent me from forgetting about
my OSX installation and only use ubuntu.

- On every kernel update, I need to recompile uvc support for isight, then
  applying a time-consuming patch until it works
- Same for sound
- Mic only works after some fiddling around (I'm studying abroad, need skype)

--> after a kernel update I spend futile time to get my system running again.
I've got other things to do.

- No "official" clean way of maintaining shared home dirs between ubuntu and osx (?)
This is a real drawback. I mostly use ubuntu, but sometimes need to go to osx.

--> Suspend and hibernate don't work
Serious IMHO. I don't want to reboot all the time. I'm studying,
and between study hours it'd be great to just suspend the machine.
I'm thinking ecologically and try to avoid useless energy consumption.

- Battery time seems to be lower compared to osx
When I run my MBP on ubuntu, it seems my battery runs down faster than on osx

- Known fan issues and hardware
(I know I can set min fan speeds, etc. But it seems I need to do this also on every kernel update?). I just get the feeling as when running on ubuntu, my MBP is "sweating" more and I'm lowering the possible life span of this wonderful machine. 


So my question:
Will these issues be fixed in 7.10? To what extent?
Because if not I might think of going back to osx and use only that.
Sorry, I'm a real supporter of linux since 1996, but in this case it's not suing my
purposes.

Any tips on better usage patterns also very welcomed.

btw: is compiz in 7.10 officially replacing beryl? That's my understanding...

---

### Post by cyberdork33 on 2007-09-28
> **phonky said:**
> I like it, but there are a few things which prevent me from forgetting about my OSX installation and only use ubuntu.

- On every kernel update, I need to recompile uvc support for isight, then
  applying a time-consuming patch until it worksThey are working on this module supporting iSight out of the box. The current process is broken on 2.6.22 kernels anyway, so there is no way to get isight in gutsy.... yet.

> - Same for sound
- Mic only works after some fiddling around (I'm studying abroad, need skype)I haven't messed with the Mic before since I don't need it, but as for the sound situation, I can't say whether it will work in gutsy or not (but you can try the live cd). The only way these things will be made more compatible in the future is if bug reports are filed so that the developers know what needs to be fixed.

> - No "official" clean way of maintaining shared home dirs between ubuntu and osx (?)
This is a real drawback. I mostly use ubuntu, but sometimes need to go to osx.Sharing a home directory between OSX and Ubuntu will never be made too easy because it is not really a wise thing to do. You CAN create an extra 'storage' partition with a fat32 format that is easily accessible by both systems and you won't have to deal with permissions.

> --> Suspend and hibernate don't work
Serious IMHO. I don't want to reboot all the time. I'm studying,
and between study hours it'd be great to just suspend the machine.
I'm thinking ecologically and try to avoid useless energy consumption.

- Battery time seems to be lower compared to osx
When I run my MBP on ubuntu, it seems my battery runs down faster than on osxThis is likely a result of the fact that developers / users have to reverse engineer how the Apple hardware works. Apple has all the specifics, and can make their OS work the best it can. Power consumption will get better with time, but it may never measure up to what you get with OSX.

> - Known fan issues and hardware
(I know I can set min fan speeds, etc. But it seems I need to do this also on every kernel update?). I just get the feeling as when running on ubuntu, my MBP is "sweating" more and I'm lowering the possible life span of this wonderful machine.I can't help you here... but keep in mind that you do not HAVE to update your kernel. If what you have is working great, then don't fix what isn't broken! 

> So my question:
Will these issues be fixed in 7.10? To what extent?
Because if not I might think of going back to osx and use only that.
Sorry, I'm a real supporter of linux since 1996, but in this case it's not suing my
purposes.You will have to test the new release to see what changes are there. MANY MANY things change between releases. Some things may break, others may be fixed.

> btw: is compiz in 7.10 officially replacing beryl? That's my understanding...compiz-fusion is installed by default in gutsy, yes.

---

### Post by phonky on 2007-09-28
thank you for your copious answers to my long
question list, cyberdork.

I want to congratulate all of the people for the fantastic job working on making
this happen first, as I'm perfectly clear on the fact that it's not
Apple who is making ubuntu running on a mbp, 

I've worked in biz environments where you normally don't change a running system,
so actually I like this philosophy.

So what do you do then? Do you switch off the update manager?
Some of the updates are labeled "important security updates"...
how do you manage this stuff on your iMac? Don't you have similar issues I have?

thanks again

---

### Post by cyberdork33 on 2007-09-28
> **phonky said:**
> thank you for your copious answers to my long
question list, cyberdork.

I want to congratulate all of the people for the fantastic job working on making
this happen first, as I'm perfectly clear on the fact that it's not
Apple who is making ubuntu running on a mbp, 

I've worked in biz environments where you normally don't change a running system,
so actually I like this philosophy.

So what do you do then? Do you switch off the update manager?
Some of the updates are labeled "important security updates"...
how do you manage this stuff on your iMac? Don't you have similar issues I have?

thanks again
Yes/No. Wifi is not a problem because I do not have to compile my own drivers separate from what is in the repos already and the audio works fine too (although channels get mixed up sometimes).

I did have to update the uvcvideo module everytime I updated the kernel, but that is as easy as: remove current module, make, make install, and you are good to go. I am on gutsy now though, so I have no iSight :( (it does work with ekiga though, just not gstreamer.)

Kernel updates are not often security related. You can tell aptitude to 'hold' packages so they will not be updated. From the man page (which you can read all of by using the command 'man aptitiude':
> remove, purge, hold, unhold, keep, reinstall
These commands are the same as &#8220;install&#8221;, but apply the named action to all packages given on the command line for which it is not overridden. The difference between hold and keep is that hold will cause a package to be ignored by future safe-upgrade or full-upgrade commands, while keep merely cancels any scheduled actions on the package.  unhold will allow a package to be upgraded by future safe-upgrade or full-upgrade commands, without otherwise altering its state.So, you can prevent a kernel update with the following command (I think):
```
sudo aptitude hold linux-image-generic
```Then when you are ready to update, you can unhold it:
```
sudo aptitude unhold linux-image-generic
```

---

### Post by phonky on 2007-09-28
> **cyberdork33 said:**
> 

So, you can prevent a kernel update with the following command (I think):
```
sudo aptitude hold linux-image-generic
```

That's what I just did,
and I'm happy this way.

bye
fabio

---

### Post by ivelasco on 2007-09-30
> **phonky said:**
> That's what I just did,
and I'm happy this way.

bye
fabio

You can do it very easily through synaptics(lock some packages)

---

