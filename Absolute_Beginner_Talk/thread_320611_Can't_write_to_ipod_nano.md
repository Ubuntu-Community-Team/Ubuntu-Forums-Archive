---
title: "Can't write to ipod nano"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by Jonked on 2006-12-17
Have just bought a brand new Ipod nano and can't get it to play nice with Ubuntu. An older nano that I have is autodetected and works fine.

It shows up in the Computer location as 'Apple Ipod Music Player' but when double clicked, I get:

[COLOR="Red"]Unable to mount the selected volume. The volume is probably in a format that cannot be mounted 
 

mount: wrong fs type, bad option, bad superblock on /dev/sda,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so



mount: wrong fs type, bad option, bad superblock on /dev/sda,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so


error: could not execute pmount[/COLOR]


I've tried to mount it by hand, and this seems to work, until I actually try to use Amarok or GTKPod to actually do anything. In GTKPod I get:

[COLOR="Red"]Error opening '/media/ipod/iPod_Control/Music/F10/gtkpod007627.mp3' for writing (Permission denied).[/COLOR]

And in Amarok:
[COLOR="Red"]
Media Device: failed to create lockfile on iPod mounted at /media/ipod: Permission denied[/COLOR]

Any ideas? Am fairly new to Ubuntu and have been loving it so far - really really don't want to be forced back to Windows...

---

### Post by x64Jimbo on 2006-12-17
Is it formatted with FAT32? Some of them use HFS+ which may be the problem.

---

### Post by Jonked on 2006-12-17
Yep, it's definitely FAT32, according to the Properties within Windows anyway.

---

### Post by KLineD on 2006-12-17
You actually got it to mount? My older 2gb nano works just fine with Listen and libgpod but Ubuntu wouldn't mount the newer nano so I gave up with them thinking that an update of Ubuntu would take care of that.

---

### Post by Jonked on 2006-12-17
After much messing around, I got it to mount with a ```
sudo mount -t vfat /dev/sda2 /media/ipod
```

Not that that's helped me to actually USE it...

---

### Post by x64Jimbo on 2006-12-17
I've heard something about new nanos being unable to connect in Linux...
There is something that will work for you as a temporary fix until you can find out what's wrong with pmount:
sudo gtkpod

---

### Post by Jonked on 2006-12-17
Thanks for the tip - that does seem to be working - just in the middle of transferring several GBs of music.

Do I need to be worried about yanking out the USB cable when the screen seems to permanently say 'Do not disconnect'? Or is there some unmount/eject type option within gtkpod I haven't come across?

---

### Post by x64Jimbo on 2006-12-17
gtkpod is just a way to manage the files on a mounted device. You still need to umount the device when you're done adding stuff to it.

---

### Post by KLineD on 2006-12-17
glad to see gtkpod works with newer ipods, I'm thinking about getting one of those for my gfriend xmas gift...

---

### Post by x64Jimbo on 2006-12-19
Your girlfriend runs Linux? Bravo, good sir. Well played. ;)

---

### Post by KLineD on 2006-12-20
> **x64Jimbo said:**
> Your girlfriend runs Linux? Bravo, good sir. Well played. ;)

Not really, she uses my computer (Linux) but I'll bet she would gladly run Windows or OS X or anything that can surf the net and listen to mp3.

---

### Post by x64Jimbo on 2006-12-21
Nice. She sounds like a keeper. Reminds me of when I logged in on VNC and caught my GF backing up DVDs on my Kubuntu Edgy box - made me kinda proud.

---

### Post by xyz on 2006-12-21
A bit off topic bu just in case someone's interested in an alternative to nano:
[Meizu!]("http://www.ubuntuforums.org/showthread.php?t=314185&highlight=china")

---

### Post by Jonked on 2006-12-24
In case any other ubuntu newbie is having difficulties, I did eventually sort this out - haven't got the ipod to autodetect but it's now working in a fairly user-friendly manner...

I edited my etc/fstab file:
```
sudo gedit /etc/fstab
```
I added the following to the end of the file:
```
/dev/sda2   /mnt/ipod   vfat   defaults,user,noauto,sync,umask=000
```
I created a place for it to mount:
```
sudo mkdir /media/ipod
```
I changed that directory to be owned by myself:
```
sudo chown <my_username>.<my_username> /mnt/ipod
```
I created a launcher on the desktop - right clicked anywhere, and selcted Create Launcher. 
Changed it to be an 'Application in terminal' and named it 'Mount Ipod'
Put mount /media/ipod as the Command. 
Similarly, I then created another launcher to eject - making the Command eject /media/ipod

Then, in Amarok I selected 'Configure Amarok' under the settings menu. Under media devices tab, I added a media device using the Apple ipod plugin. Entered the mount point media/ipod. Then finally, I clicked on the little 'Configure device' icon and entered mount / media/ipod as the pre-connect command and eject /media/ipod as the post-disconnect command.

Now, once I boot up and plug in the ipod and run Amarok, the ipod is *usually* detected and works fine. Occasionally Amarok doesn't detect it - in which case I use the launcher on the desktop to mount it that way.

---

