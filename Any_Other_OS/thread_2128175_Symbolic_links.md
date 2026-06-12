---
title: "Symbolic links"
date: 2013-03-22
forum: Any Other OS
---

### Post by Kols on 2013-03-22
Hi!

I've just started using CrunchBang, and I want to install it alongside my Lubuntu partition. I'd like to have CB use its own /home-partition for config-files and such, but I'd also like the /home folder to share contents with the Lubuntu's /home. This is where I keep all my personal files.

I've read a bit about creating symbolic links, and that they can be applied across file-systems. I'd like to for example link the CB pictures-folder to the Lubuntu pictures-folder, but a problem arises, as far as I can see. Partitions are mounted with a random number in /media, so I don't seem to be able to create a link between the two pictures-folders because of it (I haven't tried, this is just my theory).

My questions is therefore, how to go about doing this?
(I guess I could always access any folder I want through the partitions mounted in filemanager, but it seems a bit awkward, and not very streamlined)

cheers!

---

### Post by Elfy on 2013-03-22
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by coffeecat on 2013-03-22
This shouldn't be difficult, but with one proviso. If the UID for your account is the same in both distros then it won't be difficult. If they are different, there will be permissions issues that will need dealing with. Your UID in Lubuntu should be 1000, but I don't know about Crunchbang, so let's see. Post the output of this terminal command from both distros:

```
id
```

For the rest - the random numbers are partition UUIDs and are used as mountpoints for partitions that do not have partition labels when auto-mounting from the file manager. What you need is to set up custom lines in /etc/fstab in Crunchbang to mount your Lubuntu partition on each boot and then you'll be able to create symlinks. Post the output of these commands from Lubuntu, and we can go from there:

```
sudo blkid
sudo fdisk -lu
```

Also - let us know which partition is which for which distro.

---

### Post by Kols on 2013-03-22
> **coffeecat said:**
> This shouldn't be difficult, but with one proviso. If the UID for your account is the same in both distros then it won't be difficult. If they are different, there will be permissions issues that will need dealing with. Your UID in Lubuntu should be 1000, but I don't know about Crunchbang, so let's see. Post the output of this terminal command from both distros:

```
id
```

For the rest - the random numbers are partition UUIDs and are used as mountpoints for partitions that do not have partition labels when auto-mounting from the file manager. What you need is to set up custom lines in /etc/fstab in Crunchbang to mount your Lubuntu partition on each boot and then you'll be able to create symlinks. Post the output of these commands from Lubuntu, and we can go from there:

```
sudo blkid
sudo fdisk -lu
```

Also - let us know which partition is which for which distro.

Copy that!

Tell what I'll do; I need to install Cruncbang on the computer I'll be using, and I'll use the same username. I'll come back to you once I've done this! Thanks for taking an interest in my issue. Truly, Linux and opensource is the future. I need to take a minute here and thank you, and everyone else with such immense knowledge and willingness to help out other people!

---

### Post by Paddy Landau on 2013-03-22
> **Kols said:**
> … I'll use the same username.
From the point of view of permissions, the user name is irrelevant (although it would probably make it easier for you to remember). It's the user ID — the unique number that each user gets — that is important.

It is possible to explicitly specify the user ID when creating a new user. So, if Crunchbang doesn't use the same default ID as Ubuntu for the first user created (1000), you can create a new user with ID 1000 in Crunchbang, and throw away the old user.

There are other ways around the issue, but this would be the easiest.

---

### Post by coffeecat on 2013-03-22
> **Kols said:**
> 
Tell what I'll do; I need to install Cruncbang on the computer I'll be using, and I'll use the same username. I'll come back to you once I've done this! 

That's fine! :)

Just a point of information: the username is immaterial. What matters for permissions purposes is the UID (and the GID of the default group). In Ubuntu, the first created account is given the UID 1000, the next 1001 and so on. It used to be that some distros such as Fedora started with a UID of 500, although they've used 1000 in more recent releases. I see that Crunchbang is based on Debian, so they may very well start from 1000 too, but it's easy enough to check.

The point about the username is that say I set up a dual-boot of Ubuntu and Lubuntu and name the accounts "bill" and "fred" in the two installations respectively. So long as they are both the first-created accounts, they would have the same UID and permissions won't be a problem if one account accesses files belonging to the other account in the other installation.

Anyway, we'll see whether this is going to be an issue when you next post.

**EDIT**: ninja'd by Paddy Landau. Thanks, Paddy. Nice explanation.

---

### Post by Kols on 2013-03-22
Well, it's now installed, but I just came to remember that I've encrypted the /home-partition in Lubuntu... What's the easiest way to remove the encryption? 

I'll post the outputs from Crunchbang for now, as I'm currently running a post-install script.

```

$id
uid=1000(ojkolsrud) gid=1000(ojkolsrud) groups=1000(ojkolsrud),24(cdrom),25(floppy),27(sudo),29(audio),30(dip),44(video),46(plugdev),103(fuse),104(scanner),107(bluetooth),108(netdev),1001(cbnetwork)

```

```

$sudo blkid

/dev/sda1: LABEL="Reservert av systemet" UUID="A0506D02506CE090" TYPE="ntfs" 
/dev/sda2: UUID="7A00EE3200EDF553" TYPE="ntfs" 
/dev/sda6: UUID="d23e9ab3-6e71-48b0-9630-4a0ceb9fbe85" TYPE="ext4" 
/dev/sda7: UUID="659fdd48-3ed0-4f8d-bd6a-e1a859ad281e" TYPE="ext4" 
/dev/sda5: UUID="77765047-d4a5-4556-bd6d-c5914e5fc677" TYPE="swap" 
/dev/sda8: UUID="6542abe8-4eb3-4cee-8048-026fa8c2189f" TYPE="ext4" 
/dev/sda9: UUID="706bab48-6bd7-445c-b75c-318d4e791bdc" TYPE="ext4"

```

```


$sudo fdisk -lu

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdabedabe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    40962047    20377600    7  HPFS/NTFS/exFAT
/dev/sda3        40964094   195371007    77203457    5  Extended
/dev/sda5        40964096    50726911     4881408   82  Linux swap / Solaris
/dev/sda6        50728960   128853959    39062500   83  Linux
/dev/sda7       158150656   195371007    18610176   83  Linux
/dev/sda8       128854016   148385791     9765888   83  Linux
/dev/sda9       148387840   158144511     4878336   83  Linux

Partition table entries are not in disk order

```

Partitions used by each distro:

sda6: /home of Lubuntu
sda7: / of Lubuntu
sda8: / of Crunchbang
sda9: /home of Crunchbang

thanks again, guys!

---

### Post by coffeecat on 2013-03-22
> **Kols said:**
> Well, it's now installed, but I just came to remember that I've encrypted the /home-partition in Lubuntu... What's the easiest way to remove the encryption? 

Absolutely no guarantees as I've never done this myself, but I found this on askubuntu and it seems credible:

[http://askubuntu.com/questions/4950/how-to-stop-using-built-in-home-directory-encryption](http://askubuntu.com/questions/4950/how-to-stop-using-built-in-home-directory-encryption)

As someone says there: backup your home first. And did I say to make sure you have backups? :wink:

---

### Post by Kols on 2013-03-22
> **coffeecat said:**
> Absolutely no guarantees as I've never done this myself, but I found this on askubuntu and it seems credible:

[http://askubuntu.com/questions/4950/how-to-stop-using-built-in-home-directory-encryption](http://askubuntu.com/questions/4950/how-to-stop-using-built-in-home-directory-encryption)

As someone says there: backup your home first. And did I say to make sure you have backups? :wink:

Hehehe... will backup and try to remove encryption, then get back here.

I read somewhere that one should use encryption - how dangerous is it to stop using it?

---

### Post by Paddy Landau on 2013-03-22
> **Kols said:**
> I read somewhere that one should use encryption - how dangerous is it to stop using it?
"Should" is a judgemental word. It depends entirely on your situation.

If you are holding confidential client data, you had best use encryption to help prevent data theft; you also need a strong password, and you must also encrypt your backups. (Imagine the problems if a thief steals your computer, your confidential data is exposed, and you are sued…)

If you are holding confidential personal data, it depends on how much you value your data. Again, if a thief steals your computer and you have banking details or other information that could lead to identity theft, it could cost you dearly.

If you hold no confidential data, there's no point to encryption.

---

