---
title: "My 2 cents"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by tuyer on 2006-04-28
I gave it numerous tries.The partioning part is just to non-intuitive for me.I've installed Xandros,Redhat7 and on up to FC3(not 4 yet) with no problem.   There is just something about the partitioning that confuses me.From the searching I did I sure can see I'm not alone in this.

  1)I've used a 3rd party partition manager to create a partion of unallocated space but it doesn't get seen during the install.
  2)I've let it resize my C drive twice
  3)I created a partion formatted as ext3, no  go
  4)I created a partiotn formatted as ext2 no go
   5)I created a partition as reiserfs no go


    I've followed the steps in several tutorials but something always goes of course.I haven't tried the qpart thing or whatever it was called .I'm not going to post a lot of repetitive details,I'm clearly not the first one to have trouble.There is one more possibility-that I have a flaky install CD due to a corrupt download or burn.In that spirit I'm downloading the  Live/Install DVD.If I try that later tonight or tomorrow and it works I will post back about it  just because I saw that mentioned fewer times than all the other possibilities.
   Anything's possible but the fact that a lot of obviously intelligent people are having problems with something as simple as partitioning/installing suggests there might be an intermittant problem somewhere  that hasn't been chased down.

        Anyway the point of this post was not to bitch but to point out to the developer (as have many others)  that while this may be the greatest thing since steamed lobster-but if you can't get past the shell it isn't much help.
    I'm a fairly smart guy and I've had enough.

---

### Post by zerhacke on 2006-04-28
The developers don't read this forum.  Your message will go unnoticed by them.  Try submitting a bug report instead.

---

### Post by Sef on 2006-04-28
Next time you partition, write down exactly what you do: every step.  Perhaps someone could see the problem then.  

Just use the partitioner that comes on the install disk, and yes, learning to partition is a bit of a pain.

---

### Post by tuyer on 2006-04-28
[QUOTE=zerhacke]The developers don't read this forum.  Your message will go unnoticed by them.  Try submitting a bug report instead.[/QUOTE]

     That explains a lot.I doubt if they get a lot of bug reports from people having problems with the partitioning.The chicken or the egg?

   Anyway I am not one to give up so I kept at it while waiting for my download to complete.I did find one definite problem.The partition you are installing to will not be recognized by ubuntu if there is no drive letter assigned.I'm not sure why that is.Maybe it's a bug,maybe theres a reason.I like to assign my drive letters after the fact when possible.At any rate I got it installed.Hopefully things will go smoother from this point on.From what I've heard it's pretty sweet once (if) you get past the secret installation process.Does my modem need to know a secret handshake?

---

### Post by zerhacke on 2006-04-29
[QUOTE=tuyer]That explains a lot.I doubt if they get a lot of bug reports from people having problems with the partitioning.The chicken or the egg?
[/QUOTE]
You're on the net, are you not?  Two seconds with google turned up [http://www.ubuntuforums.org/showthread.php?t=100738](http://www.ubuntuforums.org/showthread.php?t=100738)

---

### Post by Randomskk on 2006-04-29
Did the automatic partitioner not work?
The option "automatically partition free space" is there for a reason you know.

I can't see why that wouldn't have worked.

---

### Post by tuyer on 2006-04-29
The automatic partitoner did not work.It did not recognize the partion as explained already.
 I used Google trying to resolve my problem,thats how I got here.I wasn't worried about filing a bug report at that time.Actually I'm still not.I'm sure the developers are already more than aware of this problem.What they choose to do about it is up to them.
   I've got it installed now.

---

### Post by tuyer on 2006-04-30
I finally got a chance to play with it for awhile.It wiped out my MBR though.Grub just flies on by without any options,this is just an unfriendly install.
  Every other distro I have tried co-existed with Windows instead of taking over.I'm going back to Fedora,maybe I'll try this again at some point.Have fun with what I'm sure is a fine distro,I just don't feel like fighting with it right now.](*,)

---

### Post by jpfreely on 2006-04-30
I never have problems with the install CD - maybe that's just me. But I'd hold off with the Live/Desktop install for now - though it might be nice to try out the live!
I've had a few problems installing from that, but give it a shot in June when it's out of beta - I'm confident it will have been smoothed out. Ubuntu's worth another shot you know!

---

### Post by Sef on 2006-04-30
I have never had a problem with the partitioner.  I find it fairly intuitive. If you would tell step-by-step how you partition, perhaps we could help you.

---

