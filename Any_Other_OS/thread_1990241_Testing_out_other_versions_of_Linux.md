---
title: "Testing out other versions of Linux"
date: 2012-05-29
forum: Any Other OS
---

### Post by Lateralus138 on 2012-05-29
Hi all, I am running a dual os with Ubuntu 12.04 and Window 7 Ultimate 64 bit on a laptop and I was interested in trying out other Linux OS's (are they called Distros?) and I was wondering the best way to go about it without having to install it. I have tried virtual machines (both Linux and Windows)before on this machine, but had problems running most OS's saying stuff about it not running on 64 even though I know the versions were 64 bit and I know for a fact what my architecture is. I got one Linux OS to work a few years ago (can't remember which one) though I could not get the internet running on it. My question really is what is a good linux version to try with my system in a virtual machine AND/OR do other Linux versions have cds like Ubuntu that allow you to view the OS from the disc?

---

### Post by Cheesemill on 2012-05-29
You can run any Linux distro in a VM, including 64-bit versions. However, to run a 64-bit VM your processor needs to support virtualization extensions (VT-x for Intel or AMD-V for AMD processors) and they need to be enabled in your BIOS. You can run a 32-bit VM on any machine.

I use VirtualBox for all of my VM's and currently have Ubuntu Server, Arch Linux, Fedora, Mint, Windows 7 and Windows Server 2008 R2 VM's all running in a variety of 32 and 64 bit versions.

---

### Post by Lateralus138 on 2012-05-29
Ok thank you very much, maybe it was some other unseen problem that caused me problems before so I'll try again, but how about my second question? Are there other distros that can be ran live from disc?

---

### Post by Cheesemill on 2012-05-29
As far as I know all modern Linux distros have a Live CD you can run without installing.

---

### Post by Lateralus138 on 2012-05-29
Awesome, thanx again. I am somewhat new to Linux and want to wee what the Linux world is all about.

---

### Post by Slim Odds on 2012-05-29
> **Lateralus138 said:**
> Awesome, thanx again. I am somewhat new to Linux and want to wee what the Linux world is all about.

Looking at multiple distributions is likely to be more confusing than helpful is you just want to get familiar with Linux. I'd recommend spending some time playing in the Ubuntu install that you already have.

---

### Post by Lateralus138 on 2012-05-29
I know Ubuntu pretty well. I understand the terminal pretty much, I just want to see what others look like.

---

### Post by chocklet on 2012-05-30
Slim has you on the right track.  The most efficient way to find out "what the Linux world is all about" is to find a distro that works well on your hardware and get to know it well.  Install lots of FOSS applications.  Become part of a community.

If you are into Music, perhaps you are a musician... I've found Audacity and Hydrogen to be excellent tools.  Art?... check out Inkscape and Blender.  If you are into thought-provoking games or online RPGs... just explain your preferences and somebody here will not hesitate to give their opinion of how you should burn all of your time.  For most any activity, you will find multiple tools in the repository, and community help to maximize your fun.

I can't specifically help you with web/graphic design.  But if design tools are what you are looking for, then you probably should find out what FOSS tools other designers are using and run whatever distro offers that software.  I'm skeptical that other distros offer more/better design tools than Ubuntu, but it is possible.  Surely you already know more about code and such than I ever will.

For now, let's assume that you just want to learn about Linux desktops.  Here are some thoughts to consider...

In Ubuntu there are two desktops options in one install.  Be sure to spend some quality time with both Unity and Classic (gnome-panel).  Even if you find painful or missing features at first, with a little effort you might find tricks and tweaks that fix things up to suit your fancy.

If looking at live CDs will show you what you want to know about the Linux world, then how about this?...

Since Ubuntu works on your laptop, it would make sense to look at Ubuntu flavors and Ubuntu derivatives.  But as of today, May 29 where I am, Mint is the only derivative "final release" with a 3.2 kernel (based upon Ubuntu 12.04) that I've looked at.  So as of today, I'd suggest
- Ubuntu flavors
- Mint Cinnamon and maybe Mate
  (my only experience with Mate was older version)

If your lappy has been around for over a year, then I'd suggest
- PCLOS
- Knoppix (DVD version)

If PCLOS doesn't work, then try
- Mageia (more recent kernel)

Again, there are flavors with various DEs that you can look at if the main PCLOS or Mageia version works for you.  

At this point you should have tried all the major DEs: Unity, Classic, KDE, Gnome, XFCE, LXDE, Cinnamon, and maybe Mate.  32 bit and 64 bit.  Still curious?...
- Fuduntu
Just for fun...
- Bodhi (Enlightenment)

Lateralus, I think that most people are here in the Ubuntu forum because they feel that other distros are less satisfactory than Ubuntu.  These are honorable people who are reluctant to recommend to you something that doesn't work as well for them.  The people you are seeking - the people who try out all the latest distros - are now, at this very moment, spending all of their time trying to make those distros work.  Few are around here to respond to your question.

I, on the other hand, having less honor and more time, and am willing to lead you astray... Follow me!  Check out those live distros listed above.

One more thought, about self-improvement ("evolving").  Communication is a difficult art.  One of the best things that we can do for ourselves - to better prepare ourselves to address our future - is work with others on a project of some kind.  That just happens to be "what Linux is all about".

---

### Post by Megaptera on 2012-05-30
Hi Lateralus138,
I keep an eye on Distrowatch for new and updated distros [http://distrowatch.com/](http://distrowatch.com/)

---

### Post by codemaniac on 2012-05-30
> **Lateralus138 said:**
> I know Ubuntu pretty well. I understand the terminal pretty much, I just want to see what others look like.

Then you should have your hands on distros like gentoo and slackware that are considered more geekier .Or you can build your system from scratch, LFS .

---

### Post by howefield on 2012-05-30
Thread moved to "*Other OS/Distro Talk*"

---

### Post by Lateralus138 on 2012-05-30
> **codemaniac said:**
> Then you should have your hands on distros like gentoo and slackware that are considered more geekier .Or you can build your system from scratch, LFS .
Thanx codemaniac... the advice I was looking for.

---

