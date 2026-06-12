---
title: "Help with installation"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Rioku on 2007-02-25
Ok im afraid to admit it but im a complete noob at trying to install ubuntu.

I have the live cd of version 6.06? i think and i did agges ago install it on my old laptop which only had a 40 gb HD (my c: dive) installing was pretty easy at it let me move a scroll bar along letting me choose how much space linux gets to be installed on. 

This time im trying to install it on my new laptop (dual core 2 rocks!) and its  120gb hardrive 
which is split on windows as c: and d:.

i tried do the manual partitioning thing while running the installation and i thought or think i had took 5 gb from the d: to install ubuntu onto. 

However now iv lost that 5gb completely as its reduced in windows when i view the size of d:.

im afraid to install it now incase if i install on the c: which has i think 11 gb of free space on and the rest is all my windows stuff, im afraid it will wipe it all.


can anyone help me out? this sounds veerrry confusing i know and i apologise for my ignorance but i realy wonna try out ubuntu again and realy get into it because its such a great thing.

---

### Post by Rioku on 2007-02-25
sorry just bumping this so it doesnt get ignored, realy need help with this

---

### Post by raja on 2007-02-25
The problem is not completely clear to me. I assume you have about 20 GB or so as C: and the remaining as D: and that both are formatted as NTFS. If that is the case, you wont have to touch C: at all and only shrink D: to get space for Ubuntu. You should back up any important data you have before beginning -- just in case. When using the partitioner in the live cd, shrink the D: partition - this is non-destructive. 5 GB is the minimum for an Ubuntu install and I would suggest giving a little more space for the system install (Maybe about 7 GB). Also you will need a separate swap partition with about 1 - 2 GB of space. Also preferable is a separate home partition for data. Once you have these partitions set up, all the formatting and installation will be done on them - so your C: partition should be safe.

---

### Post by Rioku on 2007-02-25
well My c: is called ACER C: which has everything installed onto it it has 53.1gb in total 

but iv used up allot and now it has only 11gb of free space on that 


------------------------------------------


next is the d: which is ACERDATA D: 

this has nothing installed onto it yet (i havnt needed to use much space) it now holds 47.8gb

it used to hold 53gb ish but when i tried the partitioning thing i took 5 gb of it away to hopefuly install ubuntu on. But this would not work and now iv lost that 5gb for good.

Does ubuntu need to be installed on the same drive that windows is ?

---

### Post by Sovereign Entity on 2007-02-25
I had the same problem. It seems that the partition was the problem. So I installed it on a single drive and let ubuntu make the partition I just told it what size. Now I can go into windows and create another Ntfs drive for storage

---

### Post by Rioku on 2007-02-25
so do i need to combine the c: and d: together? into one?

---

### Post by rusty4r on 2007-02-25
D: is not a restore partition is it? Some new pc's come with restore disks that point to files stored on a partition like this.

---

### Post by Rioku on 2007-02-25
i dont think it is its completely empty too

Im abit confused with this new laptop lol the other one was very simple compared to this new acer one.

my old laptop was a toshiba saterlite pro l20 
1.6ghz
512mb ram
128mb ati graphics
40gb hardrive

and the hardrive was just one single drive ( C:)

the new one im using now is an Acer laptop
1.83ghz dual core duo 2
2gb of ram
256mb geforce card
120gb hardrive
Running on media centre 

the hardrive is split ( C: and D:)

All installed programs are on c: and windows also the d: is completely empty as i havnt needed to use it yet

i have 11gb of space left on c: which is now where i think i should put ubuntu

---

### Post by rusty4r on 2007-02-25
It didn't just come with a D: drive for no reason I wouldn't think and you said that you already tried to resize D:.

Sorry if I'm wrong but I learned this the hard way

---

### Post by raja on 2007-02-25
What was the problem exactly when you tried to install Ubuntu on the 5 GB that you took from D: ? Sometimes restore files are set up on a separate partition, but with the size of your D: partition, I dont think that is the problem. Can you use the live cd to boot up and then look at your partitions with gparted. A screenshot of that might help.

---

