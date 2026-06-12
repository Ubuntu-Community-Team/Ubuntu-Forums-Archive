---
title: "Installatn/Grub Problem."
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by hayz on 2007-04-22
Hello Ubutuans,
       I was installing a Ubuntu Dvd nd d installatn was goin' fine but stopd at 94% @ first i taught mayb it was a normal thing during installatn bt till about 3-5 mins later i still got stuck.
@ dis time i now got an error message 'Installer Crashed' but i think it failed to instal d Grub.
So ppl is there a way i can make d installatn complete/Or install ubuntu Grub -dat can b found as an entity on it self.
  Tanx.

---

### Post by ajmorris on 2007-04-22
> **hayz said:**
> Hello Ubutuans,
       I was installing a Ubuntu Dvd nd d installatn was goin' fine but stopd at 94% @ first i taught mayb it was a normal thing during installatn bt till about 3-5 mins later i still got stuck.
@ dis time i now got an error message 'Installer Crashed' but i think it failed to instal d Grub.
So ppl is there a way i can make d installatn complete/Or install ubuntu Grub -dat can b found as an entity on it self.
  Tanx.

did u install from a dvd you burnt yourself?

---

### Post by freebird54 on 2007-04-22
Any chance that your BIOS is set not to allow changes to your MBR (Master Boot Record) - that would stop grub from installing pretty effectively!

---

### Post by Pobega on 2007-04-22
What device is your drive showing up as?

If it's showing up as hda, try running this from the LiveCD:

grub_install --root-directory (Your root partition) hda

---

### Post by hayz on 2007-04-22
> **ajmorris said:**
> did u install from a dvd you burnt yourself?
I got d ubuntu dvd frm a frnd it comes wit d full apps.

---

### Post by hayz on 2007-04-22
> **freebird54 said:**
> Any chance that your BIOS is set not to allow changes to your MBR (Master Boot Record) - that would stop grub from installing pretty effectively!

how culd i correct dat?
Or is there like a place i can download d ubuntu grub frm? So i can install it on its own wen d installatn stops @ 94% again?

---

### Post by hayz on 2007-04-22
> **Pobega said:**
> What device is your drive showing up as?

If it's showing up as hda, try running this from the LiveCD:

grub_install --root-directory (Your root partition) hda

yes, it shows as hda,
wot will dat command do?
guys help me out..

---

