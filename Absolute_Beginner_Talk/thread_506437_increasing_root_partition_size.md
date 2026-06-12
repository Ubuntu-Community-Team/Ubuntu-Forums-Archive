---
title: "increasing root partition size"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by tech_cheetah on 2007-07-21
I intially thought that 5GB would be enough for ubuntu, but now I find that i need to allocate more space to the root. My current disk status is as shown in the screenshot :

[IMG]http://img54.imageshack.us/img54/8726/screenshotdevsdagpartedwt3.png[/IMG]

Now I want to add the 5.8GB partition into the exiting "/" without any reinstallation. I tried using gparted from ubuntu Live CD, but its putting a lock on either sda5 or sda6 when i unmount other.
Please help me in resolving this problem ..

---

### Post by bernied on 2007-07-21
You would need to delete sda6, then resize sda5.

It sounds like your partitions are being automounted.
Try unmounting them manually from a terminal.
```
mount | grep sda
```This will tell you which is mounted
```
sudo umount /dev/sda5
```This will unmount sda5

---

### Post by tech_cheetah on 2007-07-21
I tried doing that only .. deleted sda6 and sda7 and then tried extending sda5, but sda5 would not extend beyond 4.66GB (however it was allowing me to reduce the space in sda5)

---

### Post by bigken on 2007-07-21
try using the gparted liveCD

---

### Post by manndani on 2007-07-21
> **bigken said:**
> try using the gparted liveCD

I used the Gparted live cd, it worked like a dream, great tool.
[http://tinyurl.com/rk4qp](http://tinyurl.com/rk4qp)

---

### Post by meierfra on 2007-07-21
Don't delete sda 7. You need the swap space. 
And yes, the gparted live cd works better then gparted on the ubuntu live cd.

---

### Post by bernied on 2007-07-21
If you are still having trouble after trying the gparted live-cd, there is another way.

First backup your data before you start. You may also want to read 'man fdisk'.

Then
- boot into a live-cd and open a terminal
- make sure all partitions on the disk are unmounted, you can simply 'sudo umount /dev/sda*' - watch out for 'device is busy' messages. You need to deal with these before continuing. Any '.... is not mounted' messages can be ignored.
- run fdisk with 'sudo fdisk /dev/sda'
- hit p (print) for a list of partitions, write all of this information down (especially the bits for sda5 and sda6)
- delete partition 6 (hit d, then 6)
- delete partition 5 (hit d, then 5)
- create a new partition 5 (n, then l for logical, then number 5 if it asks for a number, then accept the default for the start, and it should give you a new number for the end - check this against the detail of the partition table you wrote down earlier, it should match up with the old end of partition 6)
- exit fdisk with w (write)
- so now you will have a larger partition, BUT the filesystem will still be the same size, resize it with
- 'sudo resize2fs /dev/sda5'

You might have a problem with your swap partition after this, as it may change number from 7 to 6. This would need a change in /etc/fstab. But, if it works, don't fix it.

The important thing here is that fdisk doesn't delete your files, it just changes the partition table. Deleting a partition using fdisk does not delete any files within the partition. But if you mess up the location of the partition when you recreate it, the filesystem will not be there.

---

### Post by tech_cheetah on 2007-07-27
The gparted CD is not showing my hard disk. 
When i run **fdisk /dev/hda** it shows some partition of size 51 Mb which i guess, is the image of the CD in memory.
Also refreshing the device in gparted window doesn't show any hard disk partition.
I tried **mount /dev/hda** and **mount /dev/hda1** , but these dont make any diffrence  :(

---

### Post by meierfra on 2007-07-27
You need to down load the gparted-live-cd  iso at

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828&release_id=519163]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828&release_id=519163")

and then burn it to a cd. If you need help with burning an iso images, let us know.

---

### Post by st33med on 2007-07-27
You could also install gparted into Ubuntu itself, just do this code:
```
sudo apt-get install gparted
```

That will install it into your Administration file.

Also, there was a funny thing that happened when I did this in the Ubuntu LiveCD...
```
sudo gparted
```

It came back with a message saying that gparted was a 'weapon of mass destruction'

WTH? Why is there a Dubya reference here?

---

### Post by AlexenderReez on 2007-07-27
> **st33med said:**
> You could also install gparted into Ubuntu itself, just do this code:
```
sudo apt-get install gparted
```

That will install it into your Administration file.

hm..using gparted livecd is better than gparted application in this case..why?because you need to resize root partition..while running from normal boot,root partition is mount...and you can't unmount it as you are running the system inside :)

i prefer   [parted magic ]("http://news.softpedia.com/news/Parted-Magic-1-8-Available-Now-61073.shtml")instead of gparted livecd :)

---

### Post by tech_cheetah on 2007-07-28
@bernied .. thanks alot
Gparted Live CD didn't work for me ...
I used a Diabolic Live CD and used the fdisk commands to delete the sda5,sda6 and sda7.
Then I made a single partition of these three .. However, when I logged into ubuntu, it was still showing the old state .. after some analysis I ran **resize2fs /dev/sda5** and now its fine :)

Just one query .. I deleted the swap partition .. I have 1GB RAM .. Do I really need a swap partition ??
What will happen if I dont specify the swap partition ??

---

### Post by dptxp on 2007-07-28
1 GB total RAM w/o SWAP can give you 'low memory' problems. I believe that one should have minimum 2 GB total, minimum 1 GB SWAP.

---

### Post by bernied on 2007-07-29
> **tech_cheetah said:**
> @bernied .. thanks alot
Gparted Live CD didn't work for me ...
I used a Diabolic Live CD and used the fdisk commands to delete the sda5,sda6 and sda7.
Then I made a single partition of these three .. However, when I logged into ubuntu, it was still showing the old state .. after some analysis I ran **resize2fs /dev/sda5** and now its fine :)

Just one query .. I deleted the swap partition .. I have 1GB RAM .. Do I really need a swap partition ??
What will happen if I dont specify the swap partition ??
You're welcome.

Regarding memory and swap space, what you need depends entirely on what you are doing with the machine. How many desktop sessions and applications running, how many web/file/mysql/etc servers etc etc.

See how you go without a swap - it will probably be fine. A few years ago, 256M was a lot of memory, and you'd have another 256M as swap and call it plenty. The operating system is not demanding much more than it was, so it depends entirely what else you are running.

---

