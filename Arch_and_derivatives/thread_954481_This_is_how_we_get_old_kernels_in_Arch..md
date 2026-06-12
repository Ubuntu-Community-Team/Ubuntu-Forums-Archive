---
title: "This is how we get old kernels in Arch."
date: 2008-10-21
forum: Arch and derivatives
---

### Post by handy on 2008-10-21
******** Please if you notice the following needs editing due to changes upstream, please PM/email me with the details so I can keep the information current?  Thankyou. ********
_______________


Here is some very valuable information that I have lifted from a reply to my questions in the [***_Arch forum_***]("http://bbs.archlinux.org/"), asking why recent kernels aren't in AUR & I stated that we need easy access to superseded kernels:
_______________

[I]It is clearly stated in the AUR guidelines:

**Check [core], [extra], [unstable], and [community] for the package. If it is inside any of those repositories in ANY form, DO NOT submit the package (if the current package is broken or is lacking an included feature then please file a bug report in FlySpray).**

However, since all official packages are maintained in a SVN repository, accessing previous kernel versions is as simple as:


[B]. /etc/makepkg.conf
svn export -r[REV] svn://svn.archlinux.org/srv/svn-packages/kernel26/repos/core-$CARCH kernel26[/B]

Where **[REV]** is the revision you want to export. To find out which revision corresponds to which kernel, have a look at: [***_i686_***]("http://repos.archlinux.org/viewvc.cgi/kernel26/repos/core-i686/PKGBUILD?view=log") or [***_x86_64_***]("http://repos.archlinux.org/viewvc.cgi/kernel26/repos/core-x86_64/PKGBUILD?view=log").

For example, if I were to get the 2.6.26.x kernel (latest was 2.6.26.5) for the i686 architecture, I'd proceed like this:


[B]. /etc/makepkg.conf
svn export -r12086 svn://svn.archlinux.org/srv/svn-packages/kernel26/repos/core-$CARCH kernel26[/B][/I]

---

### Post by will1911a1 on 2008-10-21
Very informative, thanks!

---

### Post by handy on 2008-10-21
> **will1911a1 said:**
> Very informative, thanks!

I'm so happy to have finally got that knowledge.  

The problem is that there is just so much to know, & I keep on forgetting stuff too! :lolflag:

It's like filling a leaky bucket.

---

### Post by will1911a1 on 2008-10-21
> **handy said:**
> I'm so happy to have finally got that knowledge.  

The problem is that there is just so much to know, & I keep on forgetting stuff too! :lolflag:

It's like filling a leaky bucket.

I have that same problem.  I keep meaning to write things like this down and keeping them on file but I never do.

---

### Post by handy on 2008-10-21
> **will1911a1 said:**
> I have that same problem.  I keep meaning to write things like this down and keeping them on file but I never do.

I've currently got about 800 well organised Bookmarks. They really help me to be able to access information.  But it is a far from comprehensive method & I forget what I have Bookmarked as well. :lolflag:

---

### Post by Majorix on 2008-10-21
I haven't come across any problems due to a kernel upgrade (maybe because I never turn on Testing), but if I ever do I will make sure to check those instructions. Thanks.

---

### Post by handy on 2008-10-21
> **Majorix said:**
> I haven't come across any problems due to a kernel upgrade (maybe because I never turn on Testing), but if I ever do I will make sure to check those instructions. Thanks.

I never turn on testing either.  

There is a current problem that has affected quite a few Arch & anyone else who updates there kernel quickly.  It has caused the less skilled to be jumping about a bit trying to understand what is wrong, & how to fix it.  It has settled down now, though anyone who is prone to it who does an -Syu will still get into trouble, they will find solutions quickly here & on the Arch forum, though I don't think there has been anything mentioned on the Arch main page yet.

---

### Post by crimesaucer on 2008-10-21
Good info on the back up kernels, thanks.


I had no problem with the testing repository on my i686 celeron m.... but I've had bad luck with testing packages and the x86_64 (AMD Turion 64x2), and my nvidia driver (GeForce 7150M / nForce 630M)..... 


Now that I build my system completely from source, I don't want to ruin it with any testing breakages.

---

### Post by handy on 2008-10-21
> **crimesaucer said:**
> Good info on the back up kernels, thanks.


I had no problem with the testing repository on my i686 celeron m.... but I've had bad luck with testing packages and the x86_64 (AMD Turion 64x2), and my nvidia driver (GeForce 7150M / nForce 630M)..... 


Now that I build my system completely from source, I don't want to ruin it with any testing breakages.

:lolflag: I can certainly understand that!

---

### Post by K.Mandla on 2008-10-22
Stickied. This is great information, and something every Archer should at least be aware of ... and pray they never need to use. ;)

---

### Post by mrunion on 2009-01-23
Just a note, the "home" in the path above should now be "srv".

---

### Post by wolfvorkian1 on 2009-01-27
> **mrunion said:**
> Just a note, the "home" in the path above should now be "srv".

Thanks very much for your post. I was pulling my hair trying to get Handy's commands to work being some were having the new kernel do nasty things to their system and the terminal kept telling me to get bent when I copied and pasted even his example into it. 

Now it works like a charm. But so does the new kernel .

---

### Post by handy on 2009-01-28
I just spotted this, sorry I haven't kept it up to date, I'll edit it now, let me know if I got it wrong please? :-)

A PM/email is ideal as it will get me moving quicker.

---

