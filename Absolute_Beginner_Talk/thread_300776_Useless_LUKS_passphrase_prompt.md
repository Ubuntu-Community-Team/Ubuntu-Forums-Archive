---
title: "Useless LUKS passphrase prompt"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by hannobal on 2006-11-16
I'm running Kubuntu 6.10. I'm getting "Enter LUKS passphrase for multiload" prompt at boot even that none of my partitions are encrypted at the moment. How to get rid of this? 

I've removed entries about encrypted partitions in /etc/fstab and /etc/crypttab, removed removed any initramfs crypto scripts, done "sudo update-rc.d -f remove cryptdisks" "sudo update-rc.d -f remove cryptdisks-early" and "sudo update-initramfs -u ALL", but still getting the prompt.

---

