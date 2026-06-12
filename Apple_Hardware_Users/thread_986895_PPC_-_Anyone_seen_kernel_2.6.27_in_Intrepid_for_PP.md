---
title: "PPC - Anyone seen kernel 2.6.27 in Intrepid for PPC yet?"
date: 2008-11-19
forum: Apple Hardware Users
---

### Post by stream303 on 2008-11-19
I've seen the docs, headers, and other files related to 2.6.27 on my ppc box repos running Intrepid, but no binary kernel.

Am I too impatient, or are we supposed to build it ourselves?

Still running the released 2.6.25...

---

### Post by pxwpxw on 2008-11-19
Nope.
2.6.25-2-powerpc64-SMP here on the g5. 2.6.27-7-server on the MacBook.

I think we have been marginalised.

---

### Post by Leslie Viljoen on 2008-11-19
> **pxwpxw said:**
> Nope.
2.6.25-2-powerpc64-SMP here on the g5. 2.6.27-7-server on the MacBook.

I think we have been marginalised.

I'll say ;-)

But what would be great is if we can help ourselves in the most efficient way possible. I'd like to know where Canonical ends and the community begins, so the gaps can be filled. 

[LIST]
[*]How do we get terribly broken ISO's rebuilt and redistributed? 
[*]Do we need to try and buy our own bandwidth to host such things?
[*]Do we need to do anything special to get SRU's done for PowerPC bugs, or do we just report them in Launchpad and wait?
[/LIST]

I ask the last one because I rebuilt packages that solve what I regard as a critical problem: Thunar and Xfdesktop are broken on the Intrepid CD. The [bug]("https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/297842") was triaged in two days, but must I do something else to get an update done? 

I'd like to do what I can so that people don't have to install a broken Intrepid (using the modprobe ide-scsi work-around) and then have to download my silly little packages off Mediafire and perform "apt-get -f install" magic just so that the basic desktop works. I'm sure they have all used OSX, to say that this is a shock to the system would be putting it mildly!

---

### Post by stream303 on 2008-11-19
> **pxwpxw said:**
> Nope.
2.6.25-2-powerpc64-SMP here on the g5. 2.6.27-7-server on the MacBook.

Same here on ppc.  I guess it is time to dust off stmiller's cool docs on kernel compiling for ppc:

[https://wiki.ubuntu.com/PowerPCFAQ#How%20can%20I%20configure%20and%20compile%20my%20own%20kernel%20under%20PowerPC%20Linux?](https://wiki.ubuntu.com/PowerPCFAQ#How%20can%20I%20configure%20and%20compile%20my%20own%20kernel%20under%20PowerPC%20Linux?)

I've built a few in years past for the G5 this way, although I could never get the firewall support right for some reason. (Not too big a worry since I'm behind a simple hardware router firewall), but I'd like to know how to do it right, with ppc in mind...

Onwards future ppc kernel compilers!

---

### Post by stream303 on 2008-11-19
> **Leslie Viljoen said:**
> But what would be great is if we can help ourselves in the most efficient way possible.

I think cyberdork and crew are putting together some great stuff for Mac-Tel outside of the forums - might be worth a look to see how we can improve.

I'm not a distro-jumper, but fortunately the one thing we can rest upon is our shared knowledge between Debian and Ubuntu ppc.  Most of the install issues are nearly the same.  What Ubuntu really has in it's favor is this huge web-forum, (even as crowded as it is with multi-architecture sharing) vs the standard mailing-lists for Debian.  I have tried in vain to find anyone hospitable to the idea of a dedicated Debian PPC port web-forum - most don't understand the difficulties we face, or have other agendas or biases against Apple that have nothing to do with a user simply wanting to run Linux on his ppc box and dealing with the unique problems without annoying users of other architectures who couldn't care less.

(The above just got the award for the run-on sentence award!) :)

I'm very grateful for the releases we have, and the ports repos that are maintained - but we must face the reality that since PPC is so "high maintenance", (for some: read no-profit) there comes a point where even from a community standpoint, support becomes a nightmare to do casually, especially if you mix forum cpu architectures together - it hurts both parties by not being efficient.

I guess I got off track, but perhaps Debian is the way to go, although I'd probably contribute more with a supportive web-forum that understands our needs.  We have a Debian forum here, but I'm not sure that we'd be welcome with a barrage of ppc messages.  Or would we?

Anyway, getting off track here - time to think a bit about the whole thing...

---

### Post by stream303 on 2008-11-19
Ok, here's the radical solution that should make everyone happy:

1) Create a Debian-PPC forum here.  This keeps it from just becoming a mirror image of what we have now.

2) This unclogs the Apple forum and they can concentrate on Mac-Tel issues.

3) Because of low-resources, Ubuntu can drop all current community-based ppc support, mirrors and repos.

4) Refer ppc users to the newly created Debian-PPC, which also maintains good relations with Debian, seeing as they have more resources than Canonical does as far as porting goes.

Sound reasonable?  Or have I finally lost it? :)

---

### Post by Leslie Viljoen on 2008-11-19
> **stream303 said:**
> Ok, here's the radical solution that should make everyone happy:

1) Create a Debian-PPC forum here.  This keeps it from just becoming a mirror image of what we have now.

2) This unclogs the Apple forum and they can concentrate on Mac-Tel issues.

3) Because of low-resources, Ubuntu can drop all current community-based ppc support, mirrors and repos.

4) Refer ppc users to the newly created Debian-PPC, which also maintains good relations with Debian, seeing as they have more resources than Canonical does as far as porting goes.

Sound reasonable?  Or have I finally lost it? :)

Who would host the files? Hosting large files for many people is expensive business. Wouldn't Ubuntu users be surprised to see "Debian-PPC" as a forum name and then not post there?

---

### Post by cyberdork33 on 2008-11-19
Well, a forum has been requested over and over again for PPC, but has not made a difference. I really think that it the best solution would be to create a generic PPC arch forum so that efforts of Apple and non-Apple hardware alike can work together.

As far as our activities outside the forum, they are not really my idea, but I ran with it. Having a "team" creates a sense of unity and shows that there really are people out there that want to do the same thing you do. I don't know how you guys handle bugs since you have no official support, but our launchpad team makes it easy to track bugs, and everything is relayed on our mailing list as well so that those interested can keep track of changes and outstanding issues.

If nothing else, you should look into a PPC social group.

---

### Post by stream303 on 2008-11-19
> **Leslie Viljoen said:**
> Who would host the files? Hosting large files for many people is expensive business. Wouldn't Ubuntu users be surprised to see "Debian-PPC" as a forum name and then not post there?

With Debian, your custom files may not even be necessary to host.  Debian's stable Etch-n-half, 4.0r5, works very well, even on G5's now, and utilizes much of the info from our own faqs to get up and running.  It is however more "polished", and presents less problems up front.

Debian Testing, aka "Lenny" is getting better all the time, and may be a better fit for those facing all these XFCE4 problems.

So basically all the infrastructure is already in place except for a dedicated web-forum.  Since many of us have more than just a ppc box, we could still stay within the excellent Ubuntu forum framework if a Debian-ppc forum existed here.  Intrepid absolutely rocks on my AMD/64 desktop, but of course that is officially supported.  The nice thing is that I can come to one place to get both PPC and AMD/64 support.

Time and again both here and on IRC monitoring, it has been seen that Canonical is just out of resources when it comes to PPC.  I don't think there would be any shame in stopping their PPC port and handing off the existing community to Debian.

There are already forums for other OS', and by creating one for Debian-PPC, we could still stay within the same support framework already established.  In this way, the concern about division is solved.  Once people understand that PPC hardware is from a different planet, :) they see that a dedicated forum makes sense, as much as giving Sun users a dedicated forum.  (which in the past 6 months or so has only garnered a wopping 3-pages of forum messages.  (No slight on Sun users, I'd run Ubuntu on it if I owned one!)

When you get down to it, it just appears that due to lack of resources, Debian PPC and an attending forum here, might be a better solution for Canonical, existing PPC users, and even for Ubuntu Mac-Intel by not diluting the Apple forum with ppc concerns.

So give Debian Lenny a shot, and see if your needs for customized files and setup for XFCE4 goes away.

---

### Post by stream303 on 2008-11-19
> **cyberdork33 said:**
> I really think that it the best solution would be to create a generic PPC arch forum so that efforts of Apple and non-Apple hardware alike can work together.

Not a bad idea.  It just has to be done.  Apple PPC, PS3, and IBM Z-series...

> Having a "team" creates a sense of unity and shows that there really are people out there that want to do the same thing you do.

That's the beauty of the spirit of Ubuntu, which was the side-benefit of the original forums.  They fostered not only technical excellence but a rich community experience not available elsewhere.  I'm not so sure that today's version is that rich. :)

> If nothing else, you should look into a PPC social group.

A great idea!  However it should be a supplement to a web-based forum, rather than a sole replacement.

I guess in the end I'm just trying to look out for everyone - from resource-poor ppc devs and maintainers, existing ppc users, and even Apple-Intel users.

I guess we'll see...

---

### Post by Leslie Viljoen on 2008-11-20
> **stream303 said:**
> With Debian, your custom files may not even be necessary to host.  Debian's stable Etch-n-half, 4.0r5, works very well, even on G5's now, and utilizes much of the info from our own faqs to get up and running.  It is however more "polished", and presents less problems up front.

Debian Testing, aka "Lenny" is getting better all the time, and may be a better fit for those facing all these XFCE4 problems.

So basically all the infrastructure is already in place except for a dedicated web-forum.  Since many of us have more than just a ppc box, we could still stay within the excellent Ubuntu forum framework if a Debian-ppc forum existed here.  Intrepid absolutely rocks on my AMD/64 desktop, but of course that is officially supported.  The nice thing is that I can come to one place to get both PPC and AMD/64 support.

Infrastructure-wise, are you proposing making use of Launchpad, or is there a Debian bug tracking tool? 

> Time and again both here and on IRC monitoring, it has been seen that Canonical is just out of resources when it comes to PPC.  I don't think there would be any shame in stopping their PPC port and handing off the existing community to Debian.

I agree: no shame, and Canonical has a history of abandoning projects in order to concentrate on the core. Since PPC support is so minimal among all the distros it would be great to see all the resources pooled. 

After I struggled for so long and then failed to get Hardy to even boot on my machine I searched for a while for the best distro. Eventually I installed Fedora and that was a disaster. So I installed Intrepid and that was less of a disaster because at least Apt doesn't suck like Yum.

> So give Debian Lenny a shot, and see if your needs for customized files and setup for XFCE4 goes away.

I'll give it a try.

---

### Post by pxwpxw on 2008-11-20
I am struggling with the issues raised above. 
I can't see any workable ideas much, except the idea of a team spirit, yes. But a team to do what?

Most support forums I know of are distriubution based and supported firstly, then machine, or cpu or vendor or other sub group.  
e.g. Ubuntu-> Apple-> (ppc,mactel)

So I cant see a generic powerpc, multi distro, multi machine group as a reality.

Ubuntu ppc numbers are very low, that is a major problem (critical mass), for a separate group.

I think it is also unrealistic to expect ppc releases  to continue indefinitely when apple powerpc hardware is now frozen, and I will probably stay with hardy or intrepid. I can accept the idea that my powerpc will not    handle later releases, but it would be good to have a known cut off release that worked well for powerpc, with some tidy and well organised support.

I have to live with the idea that I need to upgrade hardware in order to use the latest software, and I have equal interest in apple intel, and whatever its successor might be.

I suspect that Debian Lenny is running better on powerpc just because it is  not so leading edge as ubuntu, must try it again sometime.

---

### Post by stream303 on 2008-11-20
> **Leslie Viljoen said:**
> Infrastructure-wise, are you proposing making use of Launchpad, or is there a Debian bug tracking tool?

There is both, however I'm exploring the whole upstream-downstream situation that might be beneficial to all parties.  There's no law that says you can't be a member of more than one ppc community. :)  Dual-booting Ubuntu and Debian is a win-win since we are tied to one another.  I'll have a bit more later.

> I'll give it a try.

If you do, be sure to turn on the "popularity contest" - the Debian devs actually use this data.  Ubuntu has it as well, but it is not really clear if this data has any real importance or not.  I think the name is unfortunate, since it implies a sense of distro-cheerleading, and that's definitely not what I'm about - both Ubuntu and Debian have their pros and cons - put the pros together and you've really got something.

More to come - I've got some partitioning to do....

---

### Post by stream303 on 2008-11-20
> **pxwpxw said:**
> So I cant see a generic powerpc, multi distro, multi machine group as a reality.

You are right.  I'll pull back in to just a dedicated Debian-PPC, otherwise we'd end up in the very much the same congested situation.

> Ubuntu ppc numbers are very low, that is a major problem (critical mass), for a separate group.

True, but statistics on the whole don't reveal the whole desktop story.  Linux as a whole is what - single digits or less?  Split this up by distro, and then break it down to running either Ubuntu on PPC *or* Intel, and it spirals down even further. :)

> I think it is also unrealistic to expect ppc releases  to continue indefinitely when apple powerpc hardware is now frozen, and I will probably stay with hardy or intrepid.

Which is ok, but the reason for continuing on to the end with support goes beyond hardware and software concerns - it has to do with personal enlightenment and community.

Fortunately, most ppc boxes are built pretty well, and although they may not fit into the current metric of what a computer should be - (a networked television / game console), as long as they still work they can serve to educate those who are interested in Linux for it's own sake.

I agree that it is unrealistic to expect the hardware to live forever, but the point is that one can get quite a few more years of quality service out of them that provide ample training grounds for newer hardware and other architectures.

Case in point:  Joe Newcomer spends a lot of time banging away on our yaboot bootloader, configuring xorg.conf files, modprobing things that aren't included by default, fixing audio etc.  Now when his friend asks him if he can help him fix his problem with his new 2008 Intel X86 box running Jackalope, he can jump right in, rather than say "I don't know dude, maybe load Vista back on it?"  :)

The one thing I don't get is that Canonical still uses their admittedly scarce resources to put out PPC releases, even if they are unofficial.  Ok, so they don't market or advertise it, but skimp resources are still being used to put them on cdimage.ubuntu.com and the repo servers.  Somebody at Canonical must still like us.  I figure that if they go to the trouble at all to use any of their resources to do that, then a dedicated forum is deserved, to give respect for those devs that take the time (most likely spare time) to do it.  Downplaying or marginilizing support is really a jab against the devs and maintainers, and not the users. :)

At any rate, if it were all to come to an end with the next release, we still have options, and the years of great service and community from everyone here will always be treasured.

---

### Post by Leslie Viljoen on 2008-11-20
> **stream303 said:**
> Fortunately, most ppc boxes are built pretty well, and although they may not fit into the current metric of what a computer should be - (a networked television / game console), as long as they still work they can serve to educate those who are interested in Linux for it's own sake.

My little Mac Mini is far from a historical curiosity yet! It comes bundled with two great games on OSX, which my daughter and I still play, and many more on Linux. She loves Tuxpaint (on OSX, ironically), we run the GIMP, and since its quiet as a laptop it works great as a router, web cache and home webserver. It can stay on all day drawing minimal power, so it's ideal as a low powered server of any kind. I wouldn't swap a twice as powerful (loud, large, hot, power hungry) x86 for it. 

And one more thing: for some bizarre reason, it runs funguloids quite well straight from the repos. Which you just can't install on any other architecture as far as I am aware.

---

### Post by stream303 on 2008-11-20
That's great to hear.  It is wise to keep OSX around if for nothing else to be sure you can apply any firmware updates.

This discussion gets revived every once in awhile, doomsday is predicted, yet current releases and repos for ppc still seem to survive.  I guess you pushed my hot button with the "efficiency" word. :)

A lot of arguments against continuing ppc support sound logical, but when you analyze it, nearly all have to do with marketing, cost, political, or resource issues, and have little to do with the fact that there is enough forum traffic to warrant continued support for the little guy who just wants to run Linux on his ppc box without all those distractions.

I may have a solution that can ease that pain. :)

---

