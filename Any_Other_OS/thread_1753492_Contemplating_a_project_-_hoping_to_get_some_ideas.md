---
title: "Contemplating a project - hoping to get some ideas"
date: 2011-05-09
forum: Any Other OS
---

### Post by ClientAlive on 2011-05-09
Hi,

Lately I've been contemplating a certain project for my computer. I was wondering how you would approach something like this if you were doing it. So I thought maybe I could present my ideas and get some takes on it.

In a nutshell I was thinking it would be nice to run everything (even my daily, bread and butter o/s) in a virtual machine. So first off I guess a guy would be faced with two options: (a) Run a vm that runs as a layer on top of another o/s; or (b) run a bare metal vm.

Personally, I think that a bare metal vm would be better but I think there is a harder learning curve with that and I'm not sure how 'up for it' I am. Also, I'm not sure if running a bare metal vm removes the advantage of safety if you break Linux in there.

On the other hand, running a vm that sits on top of another o/s may require more work to set up; and, to be honest, probably a lot of learning to do with that too (just in a different area) - you'll see what I mean in a minute.

So I'll do my best to share what I'm thinking with regard to the vm that runs on top of a host o/s. That's about as far as I think I'll get since I don't really know anything about the bare metal ones.

So If I were to go with something like Virtual Box I would want to run a host o/s that was extremely extremely stripped down. I mean, like, what . . . a kernel, bash, whatever utils the vm needs to run and that the host o/s needs to maintain, maybe a couple reliable text editors like nano and vim and thats about it.

No gui, maybe not even any desktop environment (since no gui anyway); so no gnome, no kde no xfce, none of that. Certainly nothing like compiz. No special graphics. no apps, no nuthin' - not on the host o/s. Just absolute bare bones minimal - using hardly any system resources at all.

So that, then Virtual Box on top, then whatever o/s or o/ses I want to run in the vm. Problem is I'm not sure I know what to look for. I would consider compiling the kernel, patches, and whatever else needs to go into it but I would still need some starting point before I could even approach that. I can find material on how to carry it out just not sure what parts and pieces I'd need to acquire to put into it.

Then there's the whole micro kernel thing. What about that?

As far as a bare metal vm. I find that more attractive from an ignorant (read: simple lack of knowledge) sort of standpoint. Just that it's another thing I'd at least need a jumping off point to get started learning about it. I hear VM Ware is a bare metal vm. Seems like I've heard the name Itanium but not sure if it is a commercial, paid, or even server type vm.

Any ideas folks? Assuming you had determined to do something like this with your computer - how would you do it?

---

### Post by SecretCode on 2011-05-09
I'm pretty sure you will need a full GUI on the host, because your VM guest will use it - unless you run the VMs via VRDP from another physical host.

That said, "full GUI" is far simpler than "full desktop environment". You could start with an "ubuntu minimal" install, then attempt a virtualbox install from the repositories and see what dependencies it drags along.

But just one question ... **why** do you think it will be nice to run everything in a vm? :)

---

### Post by ClientAlive on 2011-05-09
> **SecretCode said:**
> I'm pretty sure you will need a full GUI on the host, because your VM guest will use it - unless you run the VMs via VRDP from another physical host.

That said, "full GUI" is far simpler than "full desktop environment". You could start with an "ubuntu minimal" install, then attempt a virtualbox install from the repositories and see what dependencies it drags along.

But just one question ... **why** do you think it will be nice to run everything in a vm? :)


Oh, well, for one thing I would like to get a few o/ses going in the list. With virtual machines/ vb I can do that and they're all right there in the list. Second, it's easy to take a snapshot so I can take one right after start up or just before shut down every time I boot and save them in case I break something in Linux. The way Virtual Box does this is by using some kind of differencing tool that just records the difference between the current time and the last time. This is convenient if something comes up where you need it and it is compact in size (rather than a copy of the whole thing bit by bit). Of course I would still keep regular backups too though. Finally, if it really came down to it and I had totally fubared the whole thing up I would still have the underlying host o/s; and, with my backed up personal data, could limp along with it until I fixed the other stuff. I also use this computer for work so that would be important.

There is a micro kernel called sel4 that I've been taking a serious look at. Perhaps this could be something to build on?

Here's a couple links to information for it:

[http://ertos.nicta.com.au/research/sel4/](http://ertos.nicta.com.au/research/sel4/)

[http://www.sigops.org/sosp/sosp09/papers/klein-sosp09.pdf](http://www.sigops.org/sosp/sosp09/papers/klein-sosp09.pdf)

Here's the thing. When I switched over to Linux one of my primary reasons was to learn. Learn, learn, learn. This same motivation is also what leads me to the "project" ideas. Doing these projects is a great way to learn and a lot of fun too. Thing is it needs to have some practical purpose also. Just doing practice exercises in bash gets a little boring after a while and it only goes so far. A guy needs a real challenge and a hands on deal to make some good leaps and bounds with this stuff. That's what I think anyhow.

---

### Post by SecretCode on 2011-05-10
Those are good enough reasons (pretty much what I expected).

One catch to be aware of is that the 3D capabilities of guests may be limited, especially until you install Vbox Guest Additions or the equivalent. In general the day-to-day experience in a VM is not quite the same as native - but it's worth trying.

---

### Post by ClientAlive on 2011-05-10
> **SecretCode said:**
> Those are good enough reasons (pretty much what I expected).

One catch to be aware of is that the 3D capabilities of guests may be limited, especially until you install Vbox Guest Additions or the equivalent. In general the day-to-day experience in a VM is not quite the same as native - but it's worth trying.


Right on. Well, I'm still contemplating making a little project out of this. Guess I'll look around and see what's out there.

Thanks man.

---

