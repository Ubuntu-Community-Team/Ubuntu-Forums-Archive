---
title: "how should i partition my new 250GB HD?"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by ice60 on 2006-03-31
hi, can someone tell me how many, and what sizes, partitions would be a good idea to make a new HDD? it will be the second HDD. i want to start with one distro, then maybe add 1/2 more later on. thanks.

i hope that first sentence makes sense, it's the best i can do :(

---

### Post by mauriciorossi on 2006-03-31
what itd do is partition it for ubuntu and in case i install 2 more distros so itd have it this way
208.5GB Ubuntu
20GB Partition in case for 1st other distro
20GB partition in case for the 2nd other distro
1.5GB Swap

---

### Post by ice60 on 2006-03-31
[QUOTE=mauriciorossi]what itd do is partition it for ubuntu and in case i install 2 more distros so itd have it this way
208.5GB Ubuntu
20GB Partition in case for 1st other distro
20GB partition in case for the 2nd other distro
1.5GB Swap[/QUOTE]
thanks :). but, i was also thinking of a partition for /home too and one for something else i can't remember lol. i hadn't thought of a swap. would it be better to let it use the swap partition on the other disk??

---

### Post by Alpha_toxic on 2006-03-31
3 x 15GB for the distros (those could be smaller, even 3x5 would do if you put /home on a separate partition)
1.5-2GB swap (preferably on this HDD, this way you can use this HDD without the other one)
everything else is one big partition or 2 half_the_size partitions. I'd make 2, so I have a spare partition to play with, but you can use one of the 15GB partitions for this (you will not install the other distros right away, right?)

Note that the HDD is not actually 250GB. They lie. The count 1GB=1000MB instead of 1024MB, so it should be about 230-240GB.

EDIT: by a "spare partition to play with" I mean a partition that I can format to FAT32 so I can take this HDD to a friend's windows box and copy sth big from him and 2 days later format to sth else for some other reason.

---

### Post by ice60 on 2006-03-31
[QUOTE=Alpha_toxic]3 x 15GB for the distros (those could be smaller, even 3x5 would do if you put /home on a separate partition)
1.5-2GB swap (preferably on this HDD, this way you can use this HDD without the other one)
everything else is one big partition or 2 half_the_size partitions. I'd make 2, so I have a spare partition to play with, but you can use one of the 15GB partitions for this (you will not install the other distros right away, right?)

Note that the HDD is not actually 250GB. They lie. The count 1GB=1000MB instead of 1024MB, so it should be about 230-240GB.[/QUOTE]
thanks, AT. i know what you've written makes sense, but you are saying make 3 15GB partitions plus one for home and one for the swap? that makes 5 partitions? i don't suppose anyone has a picture i could look at? thanks

---

### Post by Alpha_toxic on 2006-03-31
I'll try to draw one in a minute :)

EDIT: Here it is
First 3 (green) partitions are for the distros you want to install. There size should be  5-15GB. If you have a separate "/home" partition you don't need very big partitions for the distros. 10GB is absolutely enough (currently my Ubuntu install takes ub about 3.50GB).

The swap is the yellow one. It can be either here, or between the first 2 prtitions for the distros. In general it's best to have your main distro on the first partition and the swap right after it, but I'm not sure how much the performance gain actually is, so you can put the wherever you like. Also (as I said in the prev post), by putting a swap partition on that HDD, it becomes absolutely independant, and you can use it without your main HDD.

The pink ones are the "storage" partitions. They can be either 2 separate or 1 big. I'd go for 2 separate, mount the first one as "/home" for ALL the distros (there should be no problem with that, as long as you use separate usernames for each distro), and leave the second one for just_in_case. I'd make them in about 2:1 ratio (the "/home" one would be 2 times bigger than the spare one, if you have 200GB left for both, make the "/home" about 140GB and the other one about 60GB)

I hope this will help :)

EDIT 2: lol I saw your post after I did that:)

---

### Post by ice60 on 2006-03-31
[QUOTE=Alpha_toxic]I'll try to draw one in a minute :)[/QUOTE]
lol, i ment with something like Gparted, sorry. 

i know i'm being abit thick, luckily i'm not the brain of the family, hold on a second... maybe i mean unluckily. hmmm :D

---

### Post by ice60 on 2006-03-31
[QUOTE=Alpha_toxic]I'll try to draw one in a minute :)

EDIT: Here it is
First 3 (green) partitions are for the distros you want to install. There size should be  5-15GB. If you have a separate "/home" partition you don't need very big partitions for the distros. 10GB is absolutely enough (currently my Ubuntu install takes ub about 3.50GB).

The swap is the yellow one. It can be either here, or between the first 2 prtitions for the distros. In general it's best to have your main distro on the first partition and the swap right after it, but I'm not sure how much the performance gain actually is, so you can put the wherever you like. Also (as I said in the prev post), by putting a swap partition on that HDD, it becomes absolutely independant, and you can use it without your main HDD.

The pink ones are the "storage" partitions. They can be either 2 separate or 1 big. I'd go for 2 separate, mount the first one as "/home" for ALL the distros (there should be no problem with that, as long as you use separate usernames for each distro), and leave the second one for just_in_case. I'd make them in about 2:1 ratio (the "/home" one would be 2 times bigger than the spare one, if you have 200GB left for both, make the "/home" about 140GB and the other one about 60GB)

I hope this will help :)

EDIT 2: lol I saw your post after I did that:)[/QUOTE]
wow, thanks :-D it makes sense now.
:idea:
:lol:

i'll install and partition when i get back home later. thanks for the help AT

---

### Post by Mustard on 2006-03-31
That's a brilliant little diagram and explanation, Alpha toxic. :)

The second 'just in case' partition would be good for making backups on.

---

