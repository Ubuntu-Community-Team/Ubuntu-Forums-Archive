---
title: "drives gone crazy"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by metzy85 on 2007-04-04
i have dell and it automatically divides drives into like four things i have total of 60gb and like it makes a primary like 38 gb then it makes a back up which i made my linux to i think and then there is a restore then there is the full 60 gb one i want to make it easier and i can not add files to the 38 gb hard drive and i have no idea wut drive it is i have some picks below of the diffedrent screens please help i would like to keep linux on thie computer but if i can not figure the drives out i think i might uninstall  it and not use it at all because i do not know which drives are which.


[http://i149.photobucket.com/albums/s...Screenshot.png](http://i149.photobucket.com/albums/s...Screenshot.png) 


[http://i149.photobucket.com/albums/s...sksManager.png](http://i149.photobucket.com/albums/s...sksManager.png)

[http://i149.photobucket.com/albums/s...ileBrowser.png](http://i149.photobucket.com/albums/s...ileBrowser.png)

---

### Post by Rhubarb on 2007-04-04
metzy85 the 3 links to the screenshots you posted are all broken.

I've taken a (poor) screenshot of a Dell PC that I'd fixed up last year.
I used GParted to managed the partitions on the hard disk.
[http://ubuntuforums.org/attachment.php?attachmentid=17493&d=1160749223](http://ubuntuforums.org/attachment.php?attachmentid=17493&d=1160749223)

While this will look different from your setup, I'll quickly explain what it all means:

*The far left green box (fat16) represents the Dell Diagnostics partition.

*The next box is the black one (unknown), this would've been where windows was sitting (but is corrupted in the example).
Some Dells have a 10GB recovery partition here.

*The last two partitions (ntfs, in the extended part) is where this particular windows user put all their documents and games.
Windows does not usually come in this configuration.


If you can, please be more specific about your partitions on your hard drive (how big are they, what are they, what formatting are they), and what you actually want to do (I think you want to install Ubuntu, but I'm not sure).

---

### Post by metzy85 on 2007-04-04
in my computer i see 3.3 volume (hda4) and then i have 38.7 gb Volume hda2 and dell utility and file system 

then on my desktop i have the hda2 and hda4 shortcuts and i can not move or copy anything to the hda2 the 38.7gb one and like so i want to like get rid of all this complicated ness or have someone explain it to me 

the disk manager says i have 4 partions 

Partition one is windows virtual FAT at  47 

Partion 2 windows ntfs (the one i can not move things to) 36.74 gb

partion 3  is extented 3 at 13.85gb

partion 4 is windows virtual FAT at 3.26gb

and how do u install thing in linux like gparted and wut ever eles and does gaim have popup notifications like aim does

---

### Post by drakazz on 2007-04-04
> **metzy85 said:**
> in my computer i see 3.3 volume (hda4) and then i have 38.7 gb Volume hda2 and dell utility and file system 

then on my desktop i have the hda2 and hda4 shortcuts and i can not move or copy anything to the hda2 the 38.7gb one and like so i want to like get rid of all this complicated ness or have someone explain it to me 

the disk manager says i have 4 partions 

Partition one is windows virtual FAT at  47 

Partion 2 windows ntfs (the one i can not move things to) 36.74 gb

partion 3  is extented 3 at 13.85gb

partion 4 is windows virtual FAT at 3.26gb

and how do u install thing in linux like gparted and wut ever eles and does gaim have popup notifications like aim does
sudo apt-get install gparted

sudo means that you run it as the super-user (root), who has all the priviledges
apt-get is the program that controls all the installation stuff
install means the action to do
gparted is the program to be installed


It would be helpful to everyone if you re-uploaded your screenshots so that we would be able to see them. I am sure that you can attach them to the forum easily.
It would be also helpful if you gave us the output of "sudo fdisk -l", which would show all the disk drives available. Having "sudo mount" output will be nice too.

Can you explain what exactly you want to do?
What I figured out is that you want to write to your ntfs partition. I am not using Ubuntu at the moment, but I think that you could get away with "sudo apt-get install ntfs-3g", which would install the writing drivers. But I am sure that Google or someone else in the forum can guide you on this.

Regards

---

### Post by drakazz on 2007-04-04
> **drakazz said:**
> sudo apt-get install gparted

sudo means that you run it as the super-user (root), who has all the priviledges
apt-get is the program that controls all the installation stuff
install means the action to do
gparted is the program to be installed


It would be helpful to everyone if you re-uploaded your screenshots so that we would be able to see them. I am sure that you can attach them to the forum easily.
It would be also helpful if you gave us the output of "sudo fdisk -l", which would show all the disk drives available. Having "sudo mount" output will be nice too.

Can you explain what exactly you want to do?
What I figured out is that you want to write to your ntfs partition. I am not using Ubuntu at the moment, but I think that you could get away with "sudo apt-get install ntfs-3g", which would install the writing drivers. But I am sure that Google or someone else in the forum can guide you on this.

Regards
Just if anything, if you don't know how to execute these commands, there is a shell terminal available through the main menu, going to accessories and then "terminal". Should help

---

### Post by Rhubarb on 2007-04-04
Ok, it seems that you are able to read the contents of hda2 (the windows ntfs partition), but you are unable to write to it.

What you'll need is ntfs-3g   - This will allow you to read and write to it like you would expect it should.
This should get you going:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

If you want to install gparted, in the terminal, copy n paste this in:
```
sudo apt-get install gparted
```
it'll prompt you to enter in your password after entering this line.

Other programs can be installed via Applications --> Add/Remove
or via System --> Administration --> Synaptic Package Manager

Gaim has a notification plugin in-built, in gaim, go to Tools --> Plugins, and you'll find it in there.

---

### Post by metzy85 on 2007-04-04
thank you u have really helped

[http://i149.photobucket.com/albums/s43/metzy85/Screenshot-GParted.png](http://i149.photobucket.com/albums/s43/metzy85/Screenshot-GParted.png)

there is that they are all locked and the instructions are hard 
for me to understand is there easier way 

wut i don't understand is why there is a FAT drive and a NTFS drive y is that

---

### Post by Rhubarb on 2007-04-04
The FAT drive is Dell's Hidden Diagnostics partition.
When you press F12 during boot up (to bring up the boot menu), select "Diagnostics".
You'll be presented with lot's of diagnostic tools that allow you to test your RAM / Hard drive / video / sound.
If you're confident, you may delete this partition (I have done so, but it may present problems for you if you need to make a Dell technical support phone call).

The NTFS drive is where Windows XP (or Vista) is living.  This is probably where all your applications and documents live.

This may be of help to you:
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

Thanks for the screenshot - that helps a lot!

There probably is an easier way to get ntfs-3g installed (so you can read + write to your ntfs drive).
But, alas, it's getting late here, and my brain isn't working too well at the moment now.
Your best bet is to search the ubuntu forums or google for "ntfs-3g ubuntu write".

---

### Post by metzy85 on 2007-04-04
dude u have done more then enough for thank u so much i will prolly have some questions when ever u get back on

---

### Post by metzy85 on 2007-04-04
ok so i unmounted the 38gb ntfs and now i can't re mount it

---

