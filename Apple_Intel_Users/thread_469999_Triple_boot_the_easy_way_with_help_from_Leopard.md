---
title: "Triple boot the easy way with help from Leopard"
date: 2007-06-10
forum: Apple Intel Users
---

### Post by PaaC on 2007-06-10
Hi, this is a guide for you who is lucky enough to have the Leopard preview DVD.

The reason I am writing this guide is because I didn't have much luck with setting up my MacBook Pro C2D as a triple booter (Mac OS X, Ubuntu and Windows XP/Vista) with the guides I have seen. It was always some trouble, either with partition tables or that I couldn't install Windows/Ubuntu properly. I might have done something wrong, but I discovered another way of re-sizing, partitioning and setting up your Mac for triple booting.

**Step 1**

Please make sure that the hard drive you want to triple boot from is a single volume, else restore your partition with Boot Camp.
Now install rEFIt to your root. [Download here]("http://refit.sourceforge.net/#download")

**Step 2**

Now put in your Leopard DVD and boot from it.
Optional: If you have an external/2nd HDD you can make a temporary partition and restore your Leopard image to that partition and boot from it. (good if you don't want to waste DVD-r's).
[B]
Step 3[/B]

When you have booted onto Leopard's installation guide, please select what language you prefer and then open Disk Utility from the Utilities menu.
Select your internal HDD and repair it (just to make sure it is.. repaired! :p ). Then go into partitions. Here you'll see a new button called "split". Press split twice to create two extra partitions. You can re-size them as you please and it will sense how much is already on the disk so you will not loose any data. When you are happy with the sizes and file systems press partition (you will not loose any data). Please remember that you have to install Windows on the last partition. Reboot and eject the DVD.

**Step 4**

Now you can install Ubuntu on the 2nd partition and Windows on the last.

Enjoy.

---

