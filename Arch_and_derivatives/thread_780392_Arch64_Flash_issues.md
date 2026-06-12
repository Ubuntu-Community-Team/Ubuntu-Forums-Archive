---
title: "Arch64 Flash issues?"
date: 2008-05-03
forum: Arch and derivatives
---

### Post by mips on 2008-05-03
I have a fresh Arch x86_64 + KDEmod install on my desktop, only use Konqueror as my browser.

I followed [http://wiki.archlinux.org/index.php/Install_Flash_on_Arch64](http://wiki.archlinux.org/index.php/Install_Flash_on_Arch64) on how to install Flash but it does not seem to work. Youtube gives me "Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player." JavaScript is enabled.

Any ideas?

---

### Post by morgan141 on 2008-05-04
Hmm, I'm afraid I can't help you too much using that method. How I got java working though was to set up a 32bit chroot. It doesn't take much effort to set it up and I always felt it was a bit 'cleaner' than setting up nspluginwrapper. Still, I'm sure someone else will help you out.

Here's the link to the guide on setting up the chroot if you're interested: [http://wiki.archlinux.org/index.php/Arch64_Install_bundled_32bit_system](http://wiki.archlinux.org/index.php/Arch64_Install_bundled_32bit_system)

---

### Post by mips on 2008-05-05
> **morgan141 said:**
> How I got java working though was to set up a 32bit chroot]

I'm not keen on chroots.

For java I simply did a pacman -S jre and my java seems to work fine.

---

### Post by morgan141 on 2008-05-05
Oh sorry I meant flash not java.

That's fair enough I suppose. Still if someone can't help it's an option.

---

