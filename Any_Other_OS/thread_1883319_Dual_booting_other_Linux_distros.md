---
title: "Dual booting other Linux distros"
date: 2011-11-18
forum: Any Other OS
---

### Post by OakRaider4Life on 2011-11-18
I have Ubuntu paritioned so that I have a separate root partition and home partition... and I've been toying with the idea of dabbling in some other linux distros (mainly I want to fool with one that has well refined KDE integration... decidedly not Kubuntu). My question is, does anyone know if I can mount the same partition as /home for both ubuntu and another linux distribution such as SUSE or Arch?

---

### Post by donato roque on 2011-11-18
Currently dual booting Arch linux and Ubuntu but I learned from experience that there will be some 'collisions' no matter what.

So I now set it up to have separate /home partitions for each distros. I just synchronize several folders to the cloud so I have access to them wherever desktop /distro I'm in.

---

### Post by wolfen69 on 2011-11-19
It's pretty easy. Just buy a couple extra hard drives, unplug your current "stable" install(s) and go nuts.

---

### Post by ShodanjoDM on 2011-11-19
> **OakRaider4Life said:**
> I have Ubuntu paritioned so that I have a separate root partition and home partition... and I've been toying with the idea of dabbling in some other linux distros (mainly I want to fool with one that has well refined KDE integration... decidedly not Kubuntu). My question is, does anyone know if I can mount the same partition as /home for both ubuntu and another linux distribution such as SUSE or Arch?

I did just that.

Same partition for /home for both Arch and OpenSUSE, and on another disk, another common /home partition for Ubuntu 11.04 and 11.10.

But I created different username for each distro though. And then symlinked the configuration folders that I need such as .mozilla and .purple so I still have the same web bookmarks and chatlog no matter what distro I logged into.

---

### Post by OakRaider4Life on 2011-11-21
> **ShodanjoDM said:**
> I did just that.

Same partition for /home for both Arch and OpenSUSE, and on another disk, another common /home partition for Ubuntu 11.04 and 11.10.

But I created different username for each distro though. And then symlinked the configuration folders that I need such as .mozilla and .purple so I still have the same web bookmarks and chatlog no matter what distro I logged into.

I didn't even know what a symlink was until you just mentioned that and I went to do a little reading on it. This may be the perfect solution! Thank you for your response!

---

### Post by majedaly on 2011-11-21
I actually managed to dual boot in a different way. My issue was that I needed windows for some work applications, and as we all know, windows crash. when windows crash after installing GRUB on the master boot record, things get messy, and you can not easily restore windows, reinstall without having to refix grub. so, I came up with another approach. I have 2 hard disks, one, I installed windows on, and is formatted as NTFS. The other one I installed UBUNTU and formated EXT4. This one has GRUB. From UBUNTU, I load the NTFS partition easily, and have full access. When I need to boot for windows, I just change the boot options from the BIOS :)
Easy, straight forward.

---

### Post by ShodanjoDM on 2011-11-22
> **OakRaider4Life said:**
> I didn't even know what a symlink was until you just mentioned that and I went to do a little reading on it. This may be the perfect solution! Thank you for your response!

You're welcome. Glad I can help :)

Be careful to decide what configuration/hidden folders and files to link under other username directories though. In my experience, folders such as ~/.cache, ~/.config, ~/.gconf, ~/.gnome2*, ~/.local etc are better leave unlinked to minimize the possibilities of conflicting configurations.

And one more, do check the user ID and group ID for each user folders. In most of the distros that I've tried, the default UID and GID of first user created is 1000:1000 while other, such as OpenSUSE is 1000:500. This might caused some permission problems to access shared folders and files although it's not hard to rectify.

---

