---
title: "[SOLVED] accidently deleted all partitions in gparted"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by ronaldor9 on 2007-11-17
now ubuntu wont install and it asks

You need to specify a partition for the root file system (mount point "/") with a minimum size of 2 GB, and a swap partition of at least 256 MB. You may also set up other partitions if you wish.

as step four doesent even ask for guided or manuall partitioning what shoudl i do help please

---

### Post by Inxsible on 2007-11-17
> **ronaldor9 said:**
> now ubuntu wont install and it asks

You need to specify a partition for the root file system (mount point "/") with a minimum size of 2 GB, and a swap partition of at least 256 MB. You may also set up other partitions if you wish.

as step four doesent even ask for guided or manuall partitioning what shoudl i do help pleaseInsert the Live CD and re -install. There is nothing else you can do. If you had a dual boot, you probably lost Windows too :(

---

### Post by ronaldor9 on 2007-11-17
noo i had no windows or anything on the harddrive its that i cant install Ubuntu it just wont let me beacuse it says 
You need to specify a partition for the root file system (mount point "/") with a minimum size of 2 GB, and a swap partition of at least 256 MB. You may also set up other partitions if you wish

i cant choose any options such as use entire disk or anything its just soo messed up beacuse i deleted every partition on the hd and then just created one ext3 partition now i have no clue what to do helpp fast please

---

### Post by Inxsible on 2007-11-17
> **ronaldor9 said:**
> noo i had no windows or anything on the harddrive its that i cant install Ubuntu it just wont let me beacuse it says 
You need to specify a partition for the root file system (mount point "/") with a minimum size of 2 GB, and a swap partition of at least 256 MB. You may also set up other partitions if you wish

i cant choose any options such as use entire disk or anything its just soo messed up beacuse i deleted every partition on the hd and then just created one ext3 partition now i have no clue what to do helpp fast pleaseAre you using the live Cd to boot up with ? If yes, then simply click Install.

I am sorry to break this to you, but you have probably lost everything you had on the drives.

---

### Post by meindian523 on 2007-11-17
Well,that means you have to manually create a partition for / around 7 GB is more than enough,a partition for swap(2*size of RAM) and the rest as /home on your "clean" HDD.....

edit: oops,just noted that you have only 1 big ext3 partition,so right now what you can do is delete that partition and remake according to the scheme as above or another of your choice.....

---

### Post by ronaldor9 on 2007-11-17
ok well ididint have naything on the harddrive so ididnt lose any information that was valuable

ok so hwo do i go about creating a partition caled / in gparted beacuse it wont allow me to name anything

---

### Post by meindian523 on 2007-11-17
well,I'm illiterate in GParted,I've always made partitions in Winblows Disk Management and through the installer partition utility.......

---

### Post by forestpixie on 2007-11-17
you don't need to name anything in gparted - just use it to create your partitions as you want them, then once you've done that you can then install - use the manual install option 

then you can edit partitions and give them the / and /home names as necessary

---

### Post by Zack McCool on 2007-11-17
> **ronaldor9 said:**
> ok well ididint have naything on the harddrive so ididnt lose any information that was valuable

ok so hwo do i go about creating a partition caled / in gparted beacuse it wont allow me to name anything

Just use gparted to delete all the partitions.  Do not add anything.  Then, boot to the liveCD and run the installer.

---

### Post by tact on 2007-11-17
start over... 

shut down

boot again with the liveCD

BEFORE you double click on the "install to HD" icon...  go to the menus..  System>Administration>Disk Partitioner...

Run gparted that way.  delete all partitions on the HDD.   exit

now double click on the install icon...  I think you should now have the option to "use whole HDD" 

If not..  after beginning the installer select the manual option...  manually partition inside the installer.

---

### Post by ronaldor9 on 2007-11-17
AHHHH no wonder nothing was working beacuse its not detecting my HD      arrrrrrrrrrrghh
now i have no clue what to do beacuse it doesent detect my hd but i got it all wired up correctly power pluged in and it spinning i can hear it but not detected in ubuntu whats the deal in the bios it shows up

---

### Post by meindian523 on 2007-11-17
How do you know your HDD is not getting detected?

---

### Post by ronaldor9 on 2007-11-17
beaccuse gparted doesent scan any devices in ubuntu  it cant find ?????? i have no clue what to do


i tried the gparted livecd and it was able to detect my hd but ubuntu cant so im not sure what to do

---

### Post by LowSky on 2007-11-17
use gparted live cd
partition the whole drive in EXT3

then boot ubuntu live cd
choose use entire disc option

your all set, ubuntu will do all the work for you

---

### Post by ronaldor9 on 2007-11-17
ok just did that Exactly but same problem doesent ubuntu doesent detect it soo furstrating ive tried and tried i have no clue what to do

---

### Post by bumanie on 2007-11-17
Hello ronaldor9. You are obviously very frustrated, so the first thing you should do is sit back, take three slow, deep breaths and try to relax.
After doing that, try to stay calm because the people on this forum do try their best to help. Sometimes it takes longer than expected to get to the final answer, but it usually comes given time.

I know that you have checked bios re that it recognises the hard drive, did you also check that bios is set to bbot from cdrom?

---

### Post by ronaldor9 on 2007-11-17
yes i understand and am very thankful for all the help             but im trying to figure out what it can be in the bois it does recognize the drive maybe its the jumper settings but i have no clue how to do anything with jumper settings since i just got this drive form another old pc

---

### Post by bumanie on 2007-11-17
That is a bit of problem, but there should be a manufacturers label on there somewhere. You could look up the website and get the jumper setting from there. Obviously if it is the only hard drive, you need to set it to master (which I guess you already know).

---

### Post by ronaldor9 on 2007-11-17
YEss it was the stupid jumper settings i just wanted like 8 hours of my life lmfao thanks everyone so much

---

### Post by bumanie on 2007-11-17
if that has sorted your problem, itis good to mark the thread as solved. Go to thread tools and it is the last item in the drop down menu.

---

