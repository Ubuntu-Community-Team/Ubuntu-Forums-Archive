---
title: "Advice for new PC: compatibility and software choices."
date: 2009-01-22
forum: BSD
---

### Post by Kladaradatsj on 2009-01-22
Hi!

I've been using several Linux distro's for some years now, but I've become more
interested in the BSD's the last few years. I have finally bought a new PC, and
I intend to install a BSD on it (I'm leaning heavily towards FreeBSD, although
I wouldn't preclude NetBSD yet). The overall philosophy, unity and maturity
really look interesting to me.

I still have a few questions though, and I hope you might be willing to answer
some of them. :) Any help would be greatly appreciated.

The PC is a new Dell Studio XPS Desktop model, with an Intel i7 processor and
6GB of RAM. It sports an ATI Radeon 4850 graphics card.
It comes with Vista preinstalled, but I'll reinstall that on a small slice. I
want Vista just for games, which is also why I have ordered the Radeon. I don't
really care about my graphics for serious work (in fact, I quite prefer wmii).

The screen is a 23inch 1920x1080 S2309 (by Dell too, I believe).
Would that be compatible in its native resolution, you think? I sure hope so,
because now I still have to switch windows far too often, and I'm really longing
for a nice, wide resolution. 8)

I actually do want the 64bit OS-version, since my specs can handle it,
and also because I have a bit of a weakness for new stuff, and because
I intend to update and install userland from ports. And I would like to use the
64bit potential for calculation speed (I'm a student of Engineering).
I know of some of the drawbacks to 64bit, and how that conflicts with my
statement supra about maturity, but I'll take the challenge. :)

Since Dell preconfigures the system, I suppose all components will pretty much
be compatible with one another on the actual hardware level.
I can't find any real information about the motherboard though.

Wireless is not necessary: I use Ethernet. USB-support is only necessary for big
external hard drives (which all work perfectly well with Linux) and, of course,
for keyboard and mouse. I suppose it all depends on the specific devices, but as
a rule of thumb, would you say the BSD's can handle those things?

I need to connect to my university over VPN with a Citrix Client. It works (but
just barely) in Linux. Do the BSD's have options for this situation? Are they
stable (i.e. stable enough for overnight calculations)?

Are there any specific points I need to bear in mind? (Flash, audio and video
codecs, Maple and Matlab compatibility [although I'd be perfectly happy to use
Octave and Sage instead], VPN connection, Citrix Client,...)

Phew... Quite a post. :) Anyway, I'd be really happy if some of these points
could be clarified. Feel free to nudge me either way in the FreeBSD -- NetBSD
choice, by the way. I'm still holding out on torrenting the iso's. :)

PS: I just found out about Pedro Giffuni's EuroBSDCon 2008 talk about
working with Engineering applications in FreeBSD. I haven't yet had the time to
listen it through, but I will do so soon.

My best regards,
Ruben

---

### Post by Sorivenul on 2009-01-22
If your external drives work fine with Linux, they should work with FreeBSD. 

I haven't come across a system yet that hasn't had an out-of-the-box ethernet connection, so you should be okay there too.

As far as ATI support goes, you should be okay, as I've read reports with folks getting your desired resolution using similar cards. It may take some tweaking with your X configuration. As far as acceleration goes, I don't believe it is support with the current FreeBSD driver. I don't use an ATI card myself, but from what I've read this is the case. Others will probably have more information.

I know that FreeBSD supports Octave, and I believe that MATLAB is supported through its Linux compatibility layer.

As far as your Citrix Client is concerned, it should be able to be installed from ports, but requires the Linux compatibility layer, and the linux-openmotif port, I believe.

Flash in any BSD is usually a bit more problematic than in Linux. The Linux Flash 9 plugin should work, or the alternatives of swfdec or Gnash. Mulitmedia is also a bit more difficult. The gstreamer plugins are available, and there are always win32-codecs. These should cover most of your basic needs.

The NetBSD crew should be along shortly to give their two cents. ;)

Hope this helps! Good luck!

---

### Post by Kladaradatsj on 2009-01-22
Helps a lot! Especially the engineering and connectivity software part. Thanks!

I'll probably install [Free|Net]BSD tomorrow or the day after. There's probably not that much of a difference between the two for me to appreciate, I guess. Perhaps the only thing I really notice that might have an impact for me, is the difference in the number of applications in ports versus in pkgsrc. Has anyone ever found that NetBSD's pkgsrc offers too little applications, or is that a false fear I have?

---

### Post by Sorivenul on 2009-01-22
> **Kladaradatsj said:**
> Perhaps the only thing I really notice that might have an impact for me, is the difference in the number of applications in ports versus in pkgsrc. Has anyone ever found that NetBSD's pkgsrc offers too little applications, or is that a false fear I have?
I've used NetBSD (and OpenBSD) in addition to FreeBSD, though I currently run FreeBSD exclusively for production work. That said, I've never felt that pkgsrc offers too few applications. I personally prefer the ports system and FreeBSD in general, but that, again, is personal preference.

---

### Post by JMJ_coder on 2009-01-22
> **Kladaradatsj said:**
> Helps a lot! Especially the engineering and connectivity software part. Thanks!

I'll probably install [Free|Net]BSD tomorrow or the day after. There's probably not that much of a difference between the two for me to appreciate, I guess. Perhaps the only thing I really notice that might have an impact for me, is the difference in the number of applications in ports versus in pkgsrc. Has anyone ever found that NetBSD's pkgsrc offers too little applications, or is that a false fear I have?

NetBSD's pkgsrc offers over 7300 packages. I don't find it lacking in the least! 

One of the biggest differences in NetBSD and FreeBSD is that NetBSD is installed as a very small base (~250 MB total) and it's up to you to add what you want. For example, it doesn't come with either bash or tcsh -- you can install them from pkgsrc. 

I like this (for a number of reasons), but some prefer a more "complete" system right out of the box. FreeBSD will give a more desktop-centric environment from a base installation.

---

### Post by kk0sse54 on 2009-01-22
hey JMJ_coder, never knew you were over here on the ubuntuforums :)

---

### Post by JMJ_coder on 2009-01-22
> **C!oud said:**
> hey JMJ_coder, never knew you were over here on the ubuntuforums :)

I just signed up after reading a post by windependence on the other forum! ;)

---

### Post by cardinals_fan on 2009-01-22
NetBSD is my favorite BSD.  FreeBSD is also nice, but Net just feels simpler and cleaner to me.  Flash is deeply screwed up on all of the BSDs, but you can likely get Flash 9 quasi-working.  It's not very stable, in my experience.

---

### Post by kk0sse54 on 2009-01-22
> **JMJ_coder said:**
> I just signed up after reading a post by windependence on the other forum! ;)

Nice and welcome to the NetBSD population on ubuntuforums, currently numbering = 2. So it's great to have another BSD user :D

> NetBSD is my favorite BSD. FreeBSD is also nice, but Net just feels simpler and cleaner to me. Flash is deeply screwed up on all of the BSDs, but you can likely get Flash 9 quasi-working. It's not very stable, in my experience.

Have you read this [http://mail-index.netbsd.org/pkgsrc-changes/2008/12/18/msg015588.html?](http://mail-index.netbsd.org/pkgsrc-changes/2008/12/18/msg015588.html?) Haven't had much time lately so I was only able to try it briefly and it didn't work for me.

---

### Post by cardinals_fan on 2009-01-22
> **C!oud said:**
> 
Have you read this [http://mail-index.netbsd.org/pkgsrc-changes/2008/12/18/msg015588.html?](http://mail-index.netbsd.org/pkgsrc-changes/2008/12/18/msg015588.html?) Haven't had much time lately so I was only able to try it briefly and it didn't work for me.
That's very interesting.  I've played with 5.0 some but have stuck with 4 on my desktop.  I might have to dig out the virtual machine again to look at this...

---

### Post by JMJ_coder on 2009-01-22
> **C!oud said:**
> Nice and welcome to the NetBSD population on ubuntuforums, currently numbering = 2. So it's great to have another BSD user :D

I like that. My new label here -> **UbuntuForums Registered NetBSD User #2**

---

### Post by cardinals_fan on 2009-01-22
> **JMJ_coder said:**
> I like that. My new label here -> **UbuntuForums Registered NetBSD User #2**
I think you need to bump that down to #3, since there already were two ;)

*feels manly for asserting self and defending territory*

---

### Post by kk0sse54 on 2009-01-22
> **JMJ_coder said:**
> I like that. My new label here -> **UbuntuForums Registered NetBSD User #2**

haha nice, although it *was* 2, now 3 ;)

> That's very interesting. I've played with 5.0 some but have stuck with 4 on my desktop. I might have to dig out the virtual machine again to look at this...

If you get it working I'd love to hear what you did. 

Other than that I think we've hijacked this thread for too long :). Might be time to create a separate NetBSD talk thread.

---

### Post by JMJ_coder on 2009-01-22
> **Kladaradatsj said:**
> Are they
stable (i.e. stable enough for overnight calculations)?

*BSD UNIX is among the most stable OS's available. Uptimes are measured in **years**, even back when Windows uptime had only improved from hours to days.

---

### Post by rliegh on 2009-01-22
What's the saying? --if you haven't rebooted your server in years, then it's probably no longer yours. :p

Don't mind me, I'm just miffed because NetBSD won't work with either of the two computers I bought in the last couple of years (issues with Nvidia disk controllers keeps it from working on my desktop, and no network drivers for my laptop's Marvell card :()

If it did, it would be my OS of choice.

---

### Post by Kladaradatsj on 2009-01-23
> **JMJ_coder said:**
> *BSD UNIX is among the most stable OS's available. Uptimes are measured in **years**, even back when Windows uptime had only improved from hours to days.

Which is indeed a major part of the appeal they hold for me. :)

But I was referring to the question if the connection over VPN is stable (my Ubuntu's vpnc and Citrix Client aren't really what I'd call stable).
I need to have overnight-calculations running on a remote server, through the VPN-Citrix combo (Matlab and Maple) to ensure compliance to the university's versions. Ubuntu's implementations have failed me a few times last year (which might of course be due to other problems, but still, it's quite pesky).

---

### Post by kk0sse54 on 2009-01-23
> **Kladaradatsj said:**
> Which is indeed a major part of the appeal they hold for me. :)

But I was referring to the question if the connection over VPN is stable (my Ubuntu's vpnc and Citrix Client aren't really what I'd call stable).
I need to have overnight-calculations running on a remote server, through the VPN-Citrix combo (Matlab and Maple) to ensure compliance to the university's versions. Ubuntu's implementations have failed me a few times last year (which might of course be due to other problems, but still, it's quite pesky).

You can check out [http://pkgsrc.se/](http://pkgsrc.se/) to browse through all the packages available through pkgsrc although I don't think Matlab or Maple are available. There are some tutorials from wiki.netbsd.se on how to get them to work through linux emulation. However I don't how applicable they are anymore since they were written for NetBSD 3.1 but you might want to check it out.

_[**Matlab Guide**]("http://wiki.netbsd.se/How_to_run_Matlab_R14.3_on_NetBSD/i386")_
[B][URL="http://wiki.netbsd.se/How_to_run_Maple_on_NetBSD/i386"]
_Maple Guide_[/URL][/B]

As for the other two, vpnc is available through pkgsrc _**[here]("http://pkgsrc.se/net/vpnc")**_
and there's a **[_Citrix ICA client_]("http://pkgsrc.se/net/citrix_ica")**  also available through linux emulation. Haven't used either one so other than point them out to you afraid not much of a help. I'd suggest trying NetBSD in Vm first to see if you can get everything to work (Vmware server, Qemu, KVM, but *not* virtualbox).

---

### Post by Kladaradatsj on 2009-01-26
Thanks, C!oud, I'll check those out.

---

