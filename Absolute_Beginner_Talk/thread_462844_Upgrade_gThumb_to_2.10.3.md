---
title: "Upgrade gThumb to 2.10.3?"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by chattanoga on 2007-06-03
1. How do I upgrade gThumb from the Synaptic version 2.10.2 to the latest stable version 2.10.3?

2. Is it unwise to use a version different from Synaptic?

3. Why isn't the latest version in Synaptic?

---

### Post by AtrejuT on 2007-06-03
is it really that important to you to have 2.10.3? if there is no major advantage I'd just stick with the one in synaptic.

If you really want to upgrade there is two possibilities:
- There is a deb-package of the program available on the net. Just download, doubleclick and it will get installed.
- There is no .deb available. You'll have to download and compile the source code. If you do want to go through this post here again.

The latest version will either appear in the backports repository at some point, but I doubt it, or it will be available in the next release of Ubuntu, due in October.

---

### Post by chattanoga on 2007-06-04
> **AtrejuT said:**
> is it really that important to you to have 2.10.3? if there is no major advantage I'd just stick with the one in synaptic.

If you really want to upgrade there is two possibilities:
- There is a deb-package of the program available on the net. Just download, doubleclick and it will get installed.
- There is no .deb available. You'll have to download and compile the source code. If you do want to go through this post here again.

The latest version will either appear in the backports repository at some point, but I doubt it, or it will be available in the next release of Ubuntu, due in October.

Yes.
In the latest version it is possible to use the EXIF info when batch-renaming files. This is not possible now due to a bug.  I seem to recall that this was possible in some earlier version as well.

Compiling is not my cup of tea, ;)
I guess I will have to look for a similar program having this feature.


/Thanks

---

### Post by kringle on 2007-07-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/gthumb/+bug/109164](https://bugs.launchpad.net/gthumb/+bug/109164) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hey everyone,

I have the same problem now in Gthumb (Feisty version) with the renaming too.  With Edgy, I always batch renamed my photos with the EXIF date information in the title.  Now, the date comes up as today--not when I actually took the photo (the image date is correct though if I look at the EXIF information).  They fixed this with 2.10.3, but I cannot find a .deb for this.  However, I did find a .deb for 2.10.2-4 here [http://packages.debian.org/testing/gnome/gthumb]("http://packages.debian.org/testing/gnome/gthumb").  I'm not sure if bug 109164 was fixed or not with this release.  Yet, when I tried to install the .deb file it states "libart-2.0-2" dependency not satisfiable.  I'm sure I could upgrade that package, but I don't want to hose my system.  According to [https://bugs.launchpad.net/gthumb/+bug/109164]("https://bugs.launchpad.net/gthumb/+bug/109164") the fix is easy, but as a newbie still (though getting better), I don't understand what file to edit with the lines provided.

Any help would be greatly appreciated!

Thanks.

---

### Post by javierfh on 2007-09-03
> **kringle said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/gthumb/+bug/109164](https://bugs.launchpad.net/gthumb/+bug/109164) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hey everyone,

I have the same problem now in Gthumb (Feisty version) with the renaming too.  With Edgy, I always batch renamed my photos with the EXIF date information in the title.  Now, the date comes up as today--not when I actually took the photo (the image date is correct though if I look at the EXIF information).  They fixed this with 2.10.3, but I cannot find a .deb for this.  However, I did find a .deb for 2.10.2-4 here [http://packages.debian.org/testing/gnome/gthumb]("http://packages.debian.org/testing/gnome/gthumb").  I'm not sure if bug 109164 was fixed or not with this release.  Yet, when I tried to install the .deb file it states "libart-2.0-2" dependency not satisfiable.  I'm sure I could upgrade that package, but I don't want to hose my system.  According to [https://bugs.launchpad.net/gthumb/+bug/109164]("https://bugs.launchpad.net/gthumb/+bug/109164") the fix is easy, but as a newbie still (though getting better), I don't understand what file to edit with the lines provided.

Any help would be greatly appreciated!

Thanks.

Does anyone know how can i install the latest version of Gthumb?
or if you have any link to a .deb from it.

Thanks in advance.

Javi

---

