---
title: "Debian Edition: How To Get  A PURE CINNAMON desktop?"
date: 2012-05-18
forum: Any Other OS
---

### Post by Uncle Spellbinder on 2012-05-18
I ran accros this (regarding Mint 12): [Remove MATE from Linux Mint 12](http://www.itworld.com/software/235061/remove-mate-linux-mint-12)

Does anyone know exactly what the process would be to completely eliminate MATE and retain a pure *LMDE Cinnamon desktop*?

---

### Post by TransitMan on 2012-05-20
> **Uncle Spellbinder said:**
> I ran accros this (regarding Mint 12): [Remove MATE from Linux Mint 12](http://www.itworld.com/software/235061/remove-mate-linux-mint-12)

Does anyone know exactly what the process would be to completely eliminate MATE and retain a pure *LMDE Cinnamon desktop*?

Why not download and install LinuxMint 13 Cinnamon Edition in either 32-bit or 64-bit.

---

### Post by Uncle Spellbinder on 2012-05-20
> **TransitMan said:**
> Why not download and install LinuxMint 13 Cinnamon Edition in either 32-bit or 64-bit.

Linux Mint Debian Edition only comes in a Cinnamon/Mate DVD (both environments installed by default). Hence my question on how to make my install pure Cinnamon.

---

### Post by TransitMan on 2012-05-20
> **Uncle Spellbinder said:**
> Linux Mint Debian Edition only comes in a Cinnamon/Mate DVD (both environments installed by default). Hence my question on how to make my install pure Cinnamon.

Go to synaptic, and slowly scroll through what packages are installed.

For every occurrence of Mate you find, mark it for Complete Removal. This will remove all traces of Mate when you are done, but you still have to deal with the leftover Gnome 2 dependencies for Mate.

For that, go to the section button, scroll down to Gnome Desktop Environment and go through the packages again, checking those that you want to completely uninstall. Look at the package warning as you check Completely Remove for the other dependencies it might take with it. Synaptic may place an indicator in the Status section of those packages that can be Auto-Removed without affecting the stability of the system. I recommend this over scrolling for individual Gnome 2 packages.
However, be forewarned, that by manually uninstalling some Gnome 2 packages may render your system unaccessible on the next reboot. 

My suggestion for Mate will not render the computer inaccessible, but my suggestions on Gnome 2 packages might, with the exception of those recommendations from Synaptic under Auto Remove.

**I am not and will not be responsible for those who follow this advice and render their computer inaccessible causing the user to reinstall the operating system.**

---

