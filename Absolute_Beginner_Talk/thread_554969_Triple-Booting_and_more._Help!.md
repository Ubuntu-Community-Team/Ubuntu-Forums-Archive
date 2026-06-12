---
title: "Triple-Booting and more. Help!"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by eshafer on 2007-09-19
Sorry for the redundancy if there is any, but it seemed that most threads were on dual-booting, and I have more a question on triple-booting. 

Okay, so I know my computer will run 7.04 fine, it's pretty new, it only has a 80GB Internal Harddrive in it though, but I have an additional 300GB External from which my music, important files, etc are stored in.  My main question is, if I can triple boot XP/Vista/Ubuntu.  I am getting Vista from a friend who is now migrating to ubuntu, and he said I should try both and see how I like each different OS.  I know already that my wireless lan card is not supported by ubuntu, and therefore, I'll probably at least be dual booting XP or Vista depending on which I like more.  

So I guess my question is how do I triple boot, and can I say, triple boot, decide I no longer like XP or Vista and then add that partition to the other windows/ubuntu partition and just dual-boot it?

Also, I think it's probably a dumb question, but is there any way I could use a cat-6 lan cable to connect to another computer running XP with a wireless card that is connected to my wan?  Or am I just 'screwed' in the problem of using the internet with ubuntu? (Would other distros maybe support my card? [Linksys WMP11 v2.1]  friend said Ubuntu would probably support the most stuff)

Thanks.

---

### Post by rsambuca on 2007-09-19
Yeah, triple booting is basically just as easy.  You just install XP first, then Vista, then Ubuntu in that order.  Grub will then give you an option of Ubuntu or the Vista bootloader.  Vista's bootloader then gives you the option of Vista or XP.  If you decide you don't want one or two of the OS's later, you can just reformat the partitions and restore grub using a linux liveCD.

I have XP, Vista, and 5 linux distros on my rig right now.  If you want my personal opinion, save yourself the hassle and skip Vista.  XP will do everything you need from Windows for now, and you don't have driver issues, DRM issues...

---

### Post by Duck2006 on 2007-09-19
May be this will help.

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

---

### Post by Straylit Me on 2007-09-19
Just because its not supported doesnt necessarily means ndiswrapper or some other driver wont work with your WLAN. Mine isnt supported either but works just fine with ndiswrapper.

As far as triple booting. Its exactly the same and dual booting. Just do the following.
1) Boot into an ubuntu live CD.
2) Using GParted, make 4 different partitions. One being EXT3, one being SWAP, and two NTFS partitions. As far as sizes for each of the partitions go. It up to you depending on how your going to use each of the OS's.
3) Boot using either your XP or Vista disk and it will see the two empty NTFS partitons, install both XP and Vista on the respective partitions.
4) Now boot back into the Ubuntu live CD and choose to manually edit the partitions, install ubuntu on the EXT3 partition, and designate the SWAP partition. Grub will be installed as the MBR and will atuomatically see XP, Vista, and Ubuntu every time it starts.

Hope this helps, if you have any specific questions, feel free to ask.

---

### Post by eshafer on 2007-09-19
Hmm, yeah, I'm just curious about Vista, so I might just try it alone, then if I like XP more, I'll just dual boot the two.

Also, what do you mean by ndiswrapper?  Does that mean, just because it isn't supported, I might still get a signal and be able to connect to the internet?

Thanks.

---

### Post by Straylit Me on 2007-09-19
> **eshafer said:**
> Hmm, yeah, I'm just curious about Vista, so I might just try it alone, then if I like XP more, I'll just dual boot the two.

Also, what do you mean by ndiswrapper?  Does that mean, just because it isn't supported, I might still get a signal and be able to connect to the internet?

Thanks.

ndiswrapper is a WLAN driver that works with a 'ton' of WLAN devices. Run a search for it on these forums, youll get a ton on very simple how-to's.

And if your just curious about vista. May i recommend Microsoft Virtual PC? Its a free download, just google it. But it will allow you to install a Vista virtual machine on XP. So youll be running XP but be able to use Vista aswell without dedicating a partition to it. Virtualbox,a VirtualPC equivalent, is available for Linux if you would like to do it on a linux host rather than XP.

---

### Post by eshafer on 2007-09-19
Ah, very cool, I didn't even know about Virtual PC, I'll have to check that out as well!  Thanks for all your help!

---

