---
title: "linux modules &amp; images"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by aeto on 2006-07-30
i never got this cleared - when installing linux-restricted-modules & linux-image do i just install just the latest one that matches my pc architecture? I have a pentium 3, so should i remove 386 & just install 686? I now have only the latest 2.6.15-26, i uninstalled 2.6.15-25 & 2.6.15-23. Previously i had all of em in. Am i doing it wrong?

---

### Post by 5-HT on 2006-07-30
Yup you only need one kernel -- so long as it works.
For a PIII, you may notice a speed increase with the 686 kernel. However, some people have reported much higher resting processor use with the 686 kernel. Though I believe that was mostly for the Pentium M.

I would highly suggest booting into a new kernel before deleting all others just to make sure everything's working alright. After that it's safe to delete the others, but you may want to keep an extra one around just in case.

About the restricted modules, you'll need one for each kernel you have so long as you need to use them.

---

### Post by moma on 2006-07-30
You have done it right.

Your machine is Pentium III, so you can run a 686kernel.
$[COLOR="Green"] sudo aptitude install linux-image-2.6.15-26-686 linux-restricted-modules-2.6.15-26-686 linux-headers-2.6.15-26-686[/COLOR]

Your new kernel will appear in GRUB boot menu.
Keep the 2.6.15-26-386 as reserve.

Read: [http://ubuntuforums.org/showthread.php?p=1301606#post1301606]("http://ubuntuforums.org/showthread.php?p=1301606#post1301606")

---

### Post by aeto on 2006-07-30
hey thanks..figured it all out.

---

