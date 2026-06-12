---
title: "Hawaii Desktop Environment"
date: 2012-11-09
forum: Any Other OS
---

### Post by DisappearingOak on 2012-11-09
I came across a new project based on Wayland and a new QT Compositor called "Green Island" on phoronix, which is called Maui OS/Hawaii DEsktop Environment. It says packages for the new desktop environment are available for Arch Linux. Has anyone tried it?

[http://www.maui-project.org/](http://www.maui-project.org/)

---

### Post by lykwydchykyn on 2012-11-09
Looks pretty cool!  I'll have to keep an eye on that.

---

### Post by mips on 2012-11-10
> **DisappearingOak said:**
> I came across a new project based on Wayland and a new QT Compositor called "Green Island" on phoronix, which is called Maui OS/Hawaii DEsktop Environment. It says packages for the new desktop environment are available for Arch Linux. Has anyone tried it?

[http://www.maui-project.org/](http://www.maui-project.org/)

I've got a fresh manjaro(arch) install so I'm a bit hesitant to add their repo and install it seeing it's still early days. Probably best tried in a VM which I might do a bit later.

---

### Post by Dlambert on 2012-11-10
> **mips said:**
> I've got a fresh manjaro(arch) install so I'm a bit hesitant to add their repo and install it seeing it's still early days. Probably best tried in a VM which I might do a bit later.

I use Manjaro too! :)

---

### Post by mips on 2012-11-10
> **Dlambert said:**
> I use Manjaro too! :)

Nice distro ;)

---

### Post by MG&amp;TL on 2012-11-11
Grr....doesn't have 32-bit builds. (Attempting to)  Building from source now, will let you guys know how it works out. Looks promising though.

---

### Post by Dlambert on 2012-11-11
> **mips said:**
> Nice distro ;)

With steam support! :)

---

### Post by Sableyes on 2012-11-11
Like the look of that ^^ Will eagerly look out for an Ubuntu based distro with that in ^^

---

### Post by MG&amp;TL on 2012-11-12
Well, I tried it out in a virtual machine, and I have to say I'm impressed. It was jerky on the VM (and then probably jerkier because it was running under an X session), but really, not too bad.

There's a screenshot attached (to see what you've got to look forward to), plus some instructions, hints and tips. :)

So, to get this running:

1) Install some virtualisation software. Virtualbox, Qemu, VMware...

2) Get Manjaro Linux installed on it, giving the /home directory at least 500MB space. Some of the source we're gong to compile has some serious data in it. You could use arch instead, but I was going for speed here.

3) Download the AUR package (download tarball, then decompress) from here: [https://aur.archlinux.org/packages/hawaii-greenisland-git/](https://aur.archlinux.org/packages/hawaii-greenisland-git/). Try and build it using *makepkg*. It will complain about dependencies, and fail to build.

4) Once you're all started up, look for, download and install the missing dependencies from AUR (they're all there), which may take a while. I think I installed 14 packages manually.

5) Once you get the original package to build properly and install, download the attached script, make it executable and run it in your X session.

With quite a hefty chunk of luck, you should get something similiar to the screenshot. Have fun!

EDIT: See Mips' post below for a substantial shortcut. :)

---

### Post by mips on 2012-11-13
> **MG&TL said:**
> 
3) Download the AUR package (download tarball, then decompress) from here: [https://aur.archlinux.org/packages/hawaii-greenisland-git/](https://aur.archlinux.org/packages/hawaii-greenisland-git/). Try and build it using *makepkg*. It will complain about dependencies, and fail to build.

4) Once you're all started up, look for, download and install the missing dependencies from AUR (they're all there), which may take a while. I think I installed 14 packages manually.

Manjaro has packer & yaourt installed by default so you don't have to download anything and run makepkg.

Just do a,
sudo packer -S <packagename> 
 or
yaourt -S <packagename>

---

### Post by MG&amp;TL on 2012-11-13
And this is why I stick to these forums. Thanks, mips! :lol:

---

### Post by cecilpierce on 2012-11-13
> **MG&TL said:**
> And this is why I stick to these forums. Thanks, mips! :lol:

Hi Mike, looks real nice, I'll have to try it when I find my brain!

I have an old ver of Manjaro and Bridge which has a ton of junk in it.
Seems like fun...:)

---

### Post by plfiorini on 2012-12-28
Hi folks,

I'm sending this to let you know that I'm working on the virtual machines.

The latest Maui development snapshot works on both VirtualBox and qemu-kvm using the framebuffer. Of course the compositor doesn't have very good performance ontop of the framebuffer but it's decent.

Latest build of the mesa-full-wayland patch also has fixes for llvmpipe which is now working with Wayland compositors.
This might be useful for VMware which has the vmwgfx driver although I havent tested it yet.

Stay tuned! :D

---

### Post by screaminj3sus on 2012-12-28
this project looks very interesting.

---

### Post by cecilpierce on 2013-04-01
Any body get Hawaii, Maui to work ?

---

### Post by DisappearingOak on 2013-04-04
> **cecilpierce said:**
> Any body get Hawaii, Maui to work ?

I had Hawaii working on Archbang few months ago, there wasn't much to see back then. but I messed up that installation, so I don't know what Hawaii is like recently. The last pre-alpha image of Maui gave me a segfault at line 10 when trying to run, but I think they will release a new alpha build soon as Phoronix had an article that Hawaii has been successfully ported to Weston compositor. They have some pics and a couple videos (though they are a bit dated) at the Maui G+ community. 

[https://plus.google.com/communities/114894812299360329015](https://plus.google.com/communities/114894812299360329015)

The eventual desktop will be something like the mockups shown here, I think.

[http://wiki.maui-project.org/Hawaii/Design/DesktopShell](http://wiki.maui-project.org/Hawaii/Design/DesktopShell)

---

### Post by MadmanRB on 2013-04-05
Seems Gnome 2 ish in its double panel design.

---

### Post by cecilpierce on 2013-07-31
Any news on Maui-project ? I have it working good in Bridge64 linux, still waiting for the installable iso !

---

### Post by Linuxgamer94 on 2013-07-31
Looks Ugly like Gnome 2 and no suport for Ubuntu. I will have to pass on this.

---

### Post by cecilpierce on 2013-08-01
Looks great to me...):P

---

### Post by Beren Camlost on 2013-08-02
Looks nice. I might just have to try the Maui project when a stable release is available.

---

### Post by cecilpierce on 2013-08-02
Working nice in Bridge Linux, should be an installable ISO out soon I hope.

---

### Post by su:bhatta on 2014-01-20
If anyones interested, they have an ISO out now, only 287Mb. 

[http://www.maui-project.org/download/](http://www.maui-project.org/download/)

Getting it now, gonna try it on VBox and see how it works out.

EDIT: It is not supported on VBox currently, due to lack of Drivers. 

Ha, will have to wait to give it a try.

---

