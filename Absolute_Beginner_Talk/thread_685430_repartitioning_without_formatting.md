---
title: "repartitioning without formatting"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Liet_Kynes on 2008-02-02
Hey everyone.

I've been using ubuntu feisty fawn for about a month now. I installed it onto an old 6gig hd but now I think its time to install onto my main hd.

The one question I have is if its possible to do this without having to format and repartition my HD. I'd like to keep the windows partition functional as well. Or if possible partition without reformatting.

Thank you in advance.

PS. I have been loving the Linux experience and was surprised that everything just  worked. :) I've also been messing around with Beryl and that's ubercool.

---

### Post by obscur156 on 2008-02-02
Yes you can by following this very simple tutorial.
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty]("http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty")

You will be running UBUNTU in 25 minutes.That very easy even if your a total noob just like me.

Just read and print the "how to" if you dont have another pc to follow the steps.

I have done my triple boot with that tuto,XP/GUTSY/HARDY.

Good luck and have fun budy.Regards.

---

### Post by mysticrider92 on 2008-02-02
I think it is *possible* to move Ubuntu to a new partition, but it is a very complicated process and not worth the extra work. The drive can can be repartitioned without formatting your Windows partition however.

You will need to use the Ubuntu live cd and select the manual partitioner in the Ubuntu installer. Shrink down your Windows partition to whatever size you want (I would leave about 15-20gb for Ubuntu). Now create a new ext3 partition in the space left. Make this fill all but around 512mb, to be made into swap. Create an extended partition in the 512mb, then create a linux-swap partition inside the extended one. 

Now just finish up the installation, but be absolutely sure (in the summary page) that your NTFS partition is not going to be formatted! It is also helpful to defrag your Windows drive before starting this process.

[edit] Actually, the guide linked to above my post would simplify this process. You don't need to install Windows though, so just skip that part.

---

### Post by Liet_Kynes on 2008-02-02
Thanks guys.

Another question. I need to enter a password everytime I connected to wireless access point. Is there a way to not have to enter it everytime?

---

### Post by tad1073 on 2008-02-02
> **mysticrider92 said:**
> Create an extended partition in the 512mb, then create a linux-swap partition inside the extended one.

All you have to do there is create the swap w/o creating the extended, it makes things easier when working with grub.

---

### Post by tad1073 on 2008-02-02
> **Liet_Kynes said:**
> Thanks guys.

Another question. I need to enter a password everytime I connected to wireless access point. Is there a way to not have to enter it everytime?

you might be able to sudo chown it but i am not sure of the rest of the command.

```
sudo chown<your user name>:<your user name> path file name
```

Like I said i don't know the full command for I am a noob myself.

---

### Post by Liet_Kynes on 2008-02-02
I get this msg everytime I log in.

nm-applet needs access to keyring or something similar. Is there a way to store the password so I don't need to enter it everytime the wireless connects?

---

### Post by tad1073 on 2008-02-02
> **Liet_Kynes said:**
> I get this msg everytime I log in.

nm-applet needs access to keyring or something similar. Is there a way to store the password so I don't need to enter it everytime the wireless connects?

There is an option to always allow or something to that effect in the dialog.

---

