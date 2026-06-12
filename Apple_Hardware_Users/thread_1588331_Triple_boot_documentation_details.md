---
title: "Triple boot documentation details"
date: 2010-10-04
forum: Apple Hardware Users
---

### Post by gustavold on 2010-10-04
I'm planning to install a triple boot (OSX, Win XP, Ubuntu) on my MacBook5,1.
I've found the following great documentation:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Mac%20OSX,%20XP,%20and%20Ubuntu](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Mac%20OSX,%20XP,%20and%20Ubuntu)

The doc has a Partitioning Diagram that says I should partition my disk as follow:

(Ubuntu partition editor)
Resize sda3 down for UBU /,
 XP retains sda4, new partition names start sda5
sda1, sda2-------------,sda3----------,sda5--,sda4------
[EFI][OSX=============][=====(UBU)===][=====][XP========]

But on step 13: On Linux installation, delete the partition you created (Linux) because its HFS, and set it as ext3 and mount /. Don't create swap (I know its going to warn you, but ignore it).

I'm confused about sda5. What is it if it is not Linux swap? Ubuntu will do the swap on a file? Or will it magically find this sda5 and use it as a swap partition? What would happen if I choose sda5 as swap partition during installation?

[]'s
Gustavo

---

