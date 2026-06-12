---
title: "Kubuntu/Bodhi dual boot"
date: 2014-11-29
forum: Any Other OS
---

### Post by punchdrunkgrunt2 on 2014-11-29
So I've decided to have a play around with Bodhi Linux for a bit, alongside Kubuntu 12.04 (my main OS). I've freed up a partition on my HD but the installer is giving me cause for concern. Two questions:

1   How can I specify that I want it to go on the free partition? I don't want it to overwrite my Kubuntu root partition, but the installer isn't making it clear where the data is going to be written to.

2   Do I need to create a new swap partition or can it use my existing one?

Thanks

---

### Post by papibe on 2014-11-29
Hi punchdrunkgrunt2. Welcome to the forum ):P

> **punchdrunkgrunt2 said:**
> How can I specify that I want it to go on the free partition? I don't want it to overwrite my Kubuntu root partition, but the installer isn't making it clear where the data is going to be written to.
Bodhi Linux is based on Ubuntu, and so is its installer. There should be an option to select the partition very similar to the Ubuntu installer.
> **punchdrunkgrunt2 said:**
> Do I need to create a new swap partition or can it use my existing one?
General answer: yes, you can use the same one as Kununtu.

If you want to do hibernation (not suspend), you would need another swap partition. Another special case would be if you want to have an encrypted swap partition. I'm not sure in this case.

Hope it helps. Let us know if you have more questions.

Come here often and have fun.
Regards.

---

### Post by deadflowr on 2014-11-30
To add, do nothing about the swap.
Leave it as is, do not mark the swap to be formatted.
Formatting will change the uuid of the swap's partition and the kubuntu install won't have the new uuid number, so kubuntu wouldn't have swap, that is until you re-write the uuid in /etc/fstab. I speak from experience;)

As Papibe stated, hibernate and encryption would be the exceptions. 
Otherwise all your installs can share the same swap.

And yes, like Papibe stated, the installer should have an option for "Something Else", or it might be called something like Advanced,or Manual.
It should be the bottom option of installation choices in the install page.
Typically, if you are only going to have the new install in a single partition, and not broken up, set / as the mountpoint.

---

### Post by punchdrunkgrunt2 on 2014-12-13
Thanks for that.
Now some other stuff has gone wrong, but that's a story for another thread...

---

