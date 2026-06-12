---
title: "Various questions about dual boot with Ubuntu and OS X"
date: 2005-06-09
forum: Apple PPC Users
---

### Post by ItinitI on 2005-06-09
Hi
I am contemplating installing Ubuntu GNU/Linux on my iBook. I want to retain Mac OS X and have a dual boot setup. So I have a few questions regarding specifics of such a scenario...

First, when repartitioning my HD will I be able to do an archive [the option where one's home directory and files are preserved in a directory whilst the rest of the system is replaced] re-install? It's not a substitute for making backups, but still it'd be more convenient than re-loading all data so just wondered if it would work...not that a clean system install couldn't be a good thing.

Second, will I be able to access my OS X partition from my Ubuntu partition or vice-versa? I read that HFS+ and Linux file system don't play so well when it comes to reading and writing [ [http://www.sowerbutts.com/linux-mac-mini/](http://www.sowerbutts.com/linux-mac-mini/) ], but I read how to access one's OS X partition from Yellow Dog Linux [ [http://www.yellowdoglinux.com/support/solutions/ydl_4.0/hfsplus.shtml](http://www.yellowdoglinux.com/support/solutions/ydl_4.0/hfsplus.shtml) ] as well. So maybe that's a Yellow Dog specific ability or file system support has improved..?

I have a '40GB' HD, equalling about 37.3GB real space, so I'm thinking about how to divide it up. I'm leaning towards something like...
16MB for Bootstrap
24GB for Mac OS X
12GB for Ubuntu Linux
1.2-ishGB for ??? Swap, Shared, maybe more Linux space?
I have 768MB memory, so how much swap space would be appropriate? [I'm thinking 512MB – 1GB perhaps..?] Any particular order they should be in? I'd think Partition 1 should be Bootstrap perhaps followed by Partition 2 with OS X...

Finally, regarding Ubuntu packages... is there a listing of all the packages in Ubuntu anywhere? I assume Ubuntu's binary packages work for PPC..?
Are Debian .deb fully compatible with Ubuntu or are their changes between a Ubuntu .deb and a Debian .deb?

Okee sorry for sooo many questions, but much thanks. =)

---

### Post by chascon on 2005-06-10
[QUOTE=][/QUOTE]
 you can resize the HFS+ partition using parted and by disabling OS X's journalling prior.  You might be able to do this from the d-i too now, not sure.  Other than that install like the ydl recommends.

---

### Post by michaelic on 2005-08-12
I hope this is the right place to ask this question:

I am a total linux newbie, but wanted to poke around a bit, and see how well it would work on my powerbook G4 (1.5 GHZ, 512 MB RAM, etc)...  i made the partitions using the manager in linux.  at this point, ubuntu is working fine, but i can't get the computer to boot from my osx cd so i can install tiger...  i can't seem to figure out what's wrong - any help would be appreciated.

thanks.

---

### Post by ru55 on 2005-08-12
for the second matter just 

write in fstab /dev/hdaX       /mnt/yourdirectory       hfsplus  defaults,(noauto)   0   0 

and mount 

till now i haven't got an problems  \\:D/

---

### Post by autocrosser on 2005-08-14
As far as Dual-boot & reading one OS from the other--

In Mac OSX--there is a control panel you can find on VersionTracker--search for ext3 and download/install it--handy when you (as root user) can edit your Ubuntu partitions from the outside--you can look, not edit as your normal user in OSX----

As for Ubuntu, you need to edit your fstab in /etc to reflect you OSX partition(s)--next, sudo mkdir /mnt/whatever your OSX partition is--then--
sudo mnt /dev/hd(a-b-etc)  /mnt/the name you just used--

To edit files in your OSX, you will need a directory (use Shared in the User directory) & change the permissions on it--make it "no ownership"--Other than that, the same as OSX holds true in Ubuntu--if you are logged in as root, you can edit any file that is in a mounted partition (CAUTION!!! you can NUKE your OSX this way--also follows if you are as root in OSX--you can nuke your Ubuntu!!!)

My fstab looks like this---

---

### Post by slux on 2005-08-15
[QUOTE=autocrosser]As far as Dual-boot & reading one OS from the other--
To edit files in your OSX, you will need a directory (use Shared in the User directory) & change the permissions on it--make it "no ownership"--Other than that, the same as OSX holds true in Ubuntu--if you are logged in as root, you can edit any file that is in a mounted partition (CAUTION!!! you can NUKE your OSX this way--also follows if you are as root in OSX--you can nuke your Ubuntu!!!)
[/QUOTE]

Another option is to make your ubuntu and OS X user the same UID and GID after which you'll be able to edit everything you would be when logged in to OS X. You can do with the users and groups administration utility or from the command line by editing /etc/passwd and /etc/group. Only adding a new user seems to be possible thru the graphical one since it won't let you change an existing user's UID though. If you decide to change an existing user, be sure to assign the ownership of your home directory to the new UID/GID. I don't know if this can be easily done graphically (recursively changing ownership) but a simple chown uid.gid -R directoryname/ will suffice from the shell.

I have one problem with an OS X mount though. Moving files to the trash doesn't seem to work, the files just won't go to the trash or sometimes go there but aren't shown in the trash (so I'm left with the files moved in .Trash-USERNAME on the mount but can't empty the trash). Anyone else experiencing this? Anyone have a solution? There's something about the trash and mounts in the Ubuntu FAQ but that didn't seem to apply here.

---

