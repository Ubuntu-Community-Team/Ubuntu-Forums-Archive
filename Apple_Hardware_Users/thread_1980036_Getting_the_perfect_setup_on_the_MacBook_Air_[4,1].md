---
title: "Getting the perfect setup on the MacBook Air [4,1]"
date: 2012-05-14
forum: Apple Hardware Users
---

### Post by Kallun on 2012-05-14
**Greetings!**

I'm posting this thread as I plan to do a re-install of an Ubuntu based distro upon it's release. In doing so, I want to create a nice clean setup with EFI booting, suitable partition schemes and filesystems.

As the title states, I'm using a MacBook Air 4,1 (with an i5 and 64GB SSD).

I currently have 12.04 running on my system (however converted into a dev build of elementary Luna using their ppa's and scripts). But this is a standard install using an MBR and BIOS emulation.

So... that's my current situation, I'll explain in more detail below, just wanted to break my thread here to say; any help is greatly appreciated on this, I will be documenting the process and experience and would really appreciate any contributions. In doing so this thread may even become a good point of reference for others looking for answers.

Right! Onward and upward!

So there are some key factors that I'm taking into consideration:

[LIST]
[*]A clean partition layout
[*]An 'SSD friendly' filesystem
[*]Booting in EFI mode
[/LIST]
**Partition layout**

So as it stands, I have completely removed OS X from my system (I've installed it to an external drive just in case I need it).
I have the Apple EFI 200MB partition, a dedicated HFS+ partition for rEFIt and then a single ext4 partition with my Ubuntu install packed neatly inside.

I'll make a point about swap here; I don't have a swap partition or swap file as I don't need it. My system is using zram, plus I don't tend to do any memory intensive work.

I'm looking to drop rEFIt and just have it boot straight to Grub2/Ubuntu.

As for Apple's EFI partition, I'm on the fence with whether to keep it or not. As stated on the [Wiki page](http://http://en.wikipedia.org/wiki/EFI_System_partition#Apple.E2.80.93Intel) for EFI System Partitions, this is used as a sort of container for firmware updates from Apple, so really it's just an empty partition. These firmware updates are seldom released, I realise it's only 200MB of space, however it's more about being a bit of a perfectionist and having the partition identifiers nicely ordered :P

So, essentially, I'd like to have as few partitions as possible.

My question here (which may tie in with the 'Booting in EFI mode' section) is would grub2 need it's own partition?

Would it be possible to literally have the one partition?

**'SSD Friendly' filesystem**

I'd just like some advice on which filesystem would be best to use really. This is for a 64GB SSD. I've read a few pages about BTRFS and ReiserFS, however there's been many mixed opinions on what should be used!


**Booting in EFI mode**

I've read a fair few personal blog posts on booting Linux in EFI mode and all seem fairly straight forward I suppose. I'd like some clear advice on getting a bootable Linux kernel in EFI mode.

Will I need a gpt partition table for it?

**Essay over!**

I really hope some of you lovely people can help me get the setup I desire. I've been planning this for quite a while!

Thanks very much in advance for any contributions!

---

### Post by Kallun on 2012-05-18
Anybody have any advice, at all?

I'd really appreciate some answers

---

### Post by graabein on 2012-05-18
Now I don't have a Mac but when I got new hardware for my old box I split the SSD in / and /home. Just in case I want to do a clean install without losing the user data. Have you given that any thought?

---

### Post by tumutanzi.com on 2012-05-18
I hate using my iPad, it not convenience. The first time I heard Ubuntu can be installed on Mac, funny.

---

### Post by Kallun on 2012-05-19
> **graabein said:**
> Now I don't have a Mac but when I got new hardware for my old box I split the SSD in / and /home. Just in case I want to do a clean install without losing the user data. Have you given that any thought?

Yup! I have a backup of my /home ready for this new install. I probably would put /home on a separate partition thinking about it.

---

### Post by graabein on 2012-05-22
How's the progress here?

---

