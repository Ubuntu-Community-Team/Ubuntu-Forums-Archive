---
title: "GRUB - 2 Ubuntu Dappers ?"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by EGE-FB on 2006-11-12
Hi,

On my GRUB bootloader, there are two Ubuntu OS's with 2 Recovery's (along with 1 Windows OS)

Is there anything wrong with this? If there is, how can I fix it?

---

### Post by David_T on 2006-11-12
I just looked, and I have three different kernels on my grub menu each with their respective recovery mode boot option.  Take a look at your /boot/grub/menu.lst file -- editing that will change your grub menu options.

---

### Post by fasoulas on 2006-11-12
> **EGE-FB said:**
> Hi,

On my GRUB bootloader, there are two Ubuntu OS's with 2 Recovery's (along with 1 Windows OS)

Is there anything wrong with this? If there is, how can I fix it?

I have the same thing but i don't think it is a problem

---

### Post by bigken on 2006-11-12
they are different kernels theres nothing wrong with having them what has happend is you have updated you machine ;)


its a good thing to have 2 different kernels to boot from just incase one goes bad you can fall back to the previous one too remove the old one go to synaptic find the old kernel and remove it your grub menu will update its self

---

