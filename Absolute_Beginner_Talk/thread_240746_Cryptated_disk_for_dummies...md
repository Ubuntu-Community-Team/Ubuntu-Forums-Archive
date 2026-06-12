---
title: "Cryptated disk for dummies..?"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by grenness on 2006-08-21
I need to have at least my Home partition cryptated.
As far as i remember from a SUSE installation I did a year ago, the option of cryptating a disk/partition/directory was available in the GUI installation process.
Now I'm running Ubuntu 6.06.1 on a Thinkpad X60S which mostly rocks, but I need cryptation.
After browsing through the forums, all I can find are pretty long How-To's demanding lot's of shell inputs from me. I am a bit scared of the shell/terminal window, and strongly prefer point-and-click in the GUI.
Is it possible for a newbie like myself to add cryptation of my Home dir/partition without having to type lots of commands like "sudo cryptsetup --verify-passphrase --verbose --hash=sha256 --cipher=aes-cbc-essiv:sha256 --key-size=256 luksFormat /dev/hda3" ?

Thanks,
Christopher

---

### Post by huygens on 2006-08-21
Hi Christopher,

Never did encryption of a FS myself. But here are some resources that might help you.[LIST]
[*]encfs (not point-&-click but seems to be easier than the method you found ;) ): [https://wiki.ubuntu.com/encryption_with_encfs_and_pam-encfs](https://wiki.ubuntu.com/encryption_with_encfs_and_pam-encfs)
[*]You have a few howtos here: [https://help.ubuntu.com/community/Security#head-067b52f485b8a37bf67b9df8c1c9d6fd167dea6a](https://help.ubuntu.com/community/Security#head-067b52f485b8a37bf67b9df8c1c9d6fd167dea6a)[/LIST]However, none are GUI-driven howtos, I'm afraid. Perhaps, one of them is easier to implement than the other... Anyway, you should now that using the command line is rather safe. You should only take special care of its syntax when using the 'rm' command or a 'sudo' command.

Sorry for not having found what you were looking for :( but you could try one of this, and you will see that the command line has nothing that can bite :)

Huygens

---

