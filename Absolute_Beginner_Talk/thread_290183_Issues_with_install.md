---
title: "Issues with install"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by glocksout on 2006-10-31
A while back I rebuilt my computer from the ground up and installed Ubuntu 5.10 64bit on the blank HDD and it wouldn't come up. I looked for help and was told to download the Alt CD and try again. I did this, and it would get to the load screen of Ubuntu and stop.

I installed Windows on a separate partition and GRUB uses Ubuntu as the default.

I am determined to get Ubuntu working on my system. At first I figured it was just the system I have since it was so new the support must not have been available. I bought the new AM2 socket the week it was released.

This weekend I downloaded the 6.06.1 Alt AMD64 iso, the 6.10 Alt AMD64 iso and the 6.1 Desktop iso and burned them to CD. When I boot my computer it boots from the CD and Ubuntu asks what to do. I select "install" and it says "loading kernel" and then freezes. It did this with both Alt CDs. So I tried the Desktop CD and it actually brings up the Ubuntu graphic with the loading bar underneath, but it freezes right here.

I want to get this working. Help please?

---

### Post by John.Michael.Kane on 2006-10-31
Have you tried passing any of these commands at boot noacpi noapic acpi=off nolapic?

Also fullspecs of your machine may help garner a more complete responce.

---

