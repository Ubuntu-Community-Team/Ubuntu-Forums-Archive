---
title: "HFS+ on linux. How good is it?"
date: 2007-05-31
forum: Apple PPC Users
---

### Post by shamael on 2007-05-31
Hallo, I am doing some research because I need to build a file server for the studio I'm working in.
We work with OSX only (doing music and video) so the most natural choice would be the Xserve, except that it is very expensive and overpowered for our needs. So my plan was basically something close to the [RAIDZilla]("http://www.smallnetbuilder.com/content/view/29954/77/") featured on tomshardware.
My concern is obviously about those damn resource forks, and you can easily guess who would get the blame (and rightly so) in case some backup projects doesn't open...
I know that archiving in tars or dmgs preserves all the forks regardless of the filesystem they're archived on, but we would need to access the drives often so it would all get to be very very cumbersome really fast.
So, has any of you any past experience with this sort of problems? Do you think it is a feasible project or do you think it is better to spend on an Xserve and be on the safe side?

Thanks!

---

### Post by stmiller on 2007-05-31
If you are connecting via samba or something like that over the network, then the filesystem is irrelevant. 

Linux can read/write HFS+ just fine.

---

### Post by shamael on 2007-05-31
Well, yes I would be mostly connecting through samba, but the filesystem is not completely irrelevant because some Mac files have important data on their resource fork. Usually, OSX splits the data fork and the resource fork in two different files when sending data to non-mac filesystems, but I am not sure if it is also able to retrieve the file correctly without extra work by the end user (namely, the FixupResourceForks command). What I am trying to achieve is native support for resource forks on a linux server, and that depends on the degree of maturity of the hfs+ kernel module...

---

### Post by stmiller on 2007-05-31
I'd be glad to test for you, if there's any specific thing you want me to try out reading/writing to HFS+. Or perhaps this is a better question for the HFS+ kernel module dev mailing list.

---

### Post by shamael on 2007-05-31
> **stmiller said:**
> Or perhaps this is a better question for the HFS+ kernel module dev mailing list.

You're probably right...I could test it myself but it would only be a short test, and I would like to have a definite answer from someone who knows the inner workings of the module.
I'll post on their forum/mailing list and then I'll report back here...we'll see.

---

### Post by Auria on 2007-05-31
AFAIK resource forks are deprecated on OS X, aren't they? most recent os X apps probably and files dont use it

---

### Post by shamael on 2007-06-01
> **Auria said:**
> AFAIK resource forks are deprecated on OS X, aren't they? most recent os X apps probably and files dont use it

Yes, that's what I thought... I'll also get to do some testing with the kind of files we use here.

---

### Post by 3rdalbum on 2007-06-01
I don't know about Linux's built-in support for HFS+, but the hfsplus command-line utilities give you the option of splitting the forks into seperate files or Binhexing it all to preserve the fork. These two options might not really be convenient for a file server where OS X programs are going to be accessing them directly.

If the files don't have resource forks, you'll be fine. Otherwise... you could just get an ordinary Mac (even second-hand) and run ordinary OS X on them as a server.

---

### Post by ssam on 2007-06-02
you might want to look up [http://netatalk.sourceforge.net/](http://netatalk.sourceforge.net/)

---

### Post by shamael on 2007-06-04
> **ssam said:**
> you might want to look up [http://netatalk.sourceforge.net/](http://netatalk.sourceforge.net/)

Yes, it seems that would work...still, we might go the powermac + external caddy way. We would probably be using the "server" mostly for archiving, so that speed is not that much of an issue, and that way we would also get another workstation...

Thanks for the tip though, I might test it anyway even if just out of curiosity!

---

