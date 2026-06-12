---
title: "Partition assistance/guidance"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by k3lt01 on 2007-12-25
I have just installed Gutsy on my desktop but didn't really think about the partition sizes etc. because I just wanted to see at first if it would run.

First some info. The Desktop has 2 hard drives an 80 Gb which used to be my Windows Vista drive, and a 200 Gb which used to be the "My Documents" drive and it has ALL of my data etc on it. The drives were NTFS but now the 80 Gb is etx3 and the 200 Gb is still NTFS. My initial install of Gutsy has 10 Gb for /, 2 Gb for Swap, 10 Gb for /usr and 53 Gb for /home on the 80 Gb drive. The machine will eventually have Ubuntu Studio on it and also be my Entertainment centre (Elisa?) as I had Vista Ultimate and used it to watch Dvds and do all of my analog to digital music conversion work on it. It is also the main PC for printing, university work, education work (I am a high school teacher), etc. You name it this machine is the main machine for it so I want to set it up so it ash enough capacity to install programs, use WINE so I can use (unavoidable I'm afraid) some Windows based programs.

My question is, is there a better option for the partitions? I would like to use the 200 Gb drive for /home or at least let it be part of /home so /home could be more than 200 Gb. Is 10 Gb for /usr overkill? What other partitions would be a good option and how big should I make them? I will probably keep the / and /usr as ext3 and probably the /home as well, but considering what I use the machine for is there a better option for the file system types or is it just personal choice?

Thanks in advance for any help.
Michael.

---

### Post by blueridgedog on 2007-12-25
Obviously the 200 /home is agreed.

The 80 I would simply make swap and /.  That way, you have the most flexibility.  You have no more spindles and the point (IMHO) would then be moot.  I used to get very involved in slicing the drive up, but the reality is that stemmed from a server background where having different items on different spindles made sense.

You may get 100 opinions on this, but now you have mine.

---

### Post by k3lt01 on 2007-12-25
thanks mate, your opinion is appreciated

---

### Post by iris-n on 2007-12-25
As there are plenty of opinions, there's mine.

Aside from /home, there is no real need to make separate partitions, for /usr and etc. A 80 GiB for / seems great to me, and with 2 GiB of swap you won't have trouble. Now I would also make the 200 GiB one ext3, for a matter of elegance and compatibility.

---

### Post by k3lt01 on 2007-12-26
Thanks Iris, that is exactly what I have done. It is running smoothly and I am currently adding my Dvd and Music collection to it as I am typing this on my laptop.

---

