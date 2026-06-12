---
title: "Expanding or Carrying Home Folder"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by cmfrtblynmb on 2008-02-10
Hello everyone

Recently I installed ubuntu to give it a try. It would be my secondary os in hd. But then, naturally I loved it, and decided that windows would be the secondary os.

The problem is I gave a very small area to my Linux(comparing to Windows). I will cut the cr**p and give info about the situation, 

my root folder is 30 gb, home folder is 30 gb. I would like to add an empty partition (which is 100 gb) to my home folder. Or carry my home folder to that big partiton.

What should I do now? What is your advice? And how will I carry my home folder to this newly formatted partition?? (I guess simple copy-paste will not work)

Thnx

---

### Post by jimrz on 2008-02-10
why add the new partition to /home? just create the partition, name it "data" or something like that and keep all your data/music/whatever files there. an added bonus to this is that when you upgrade to a new version of ubuntu you will be able to do a clean install and all of your data on the new partition will remain untouched.  also when you do your next clean install. 30 Gb for "/" is way overkill, 4or 5 will work and 12-15 would be about the max anybody would actually use.

---

### Post by cmfrtblynmb on 2008-02-10
Thanks

You are absolutely right

But the problem was that I did not know that 30 gb was overkill, I am used to windows style, where you usually put all your eggs to same basket as default!! Other than that vista alone uses sth close to 10 to 20 gigs with softwares u install. 

But there is not much I can do about space management right now:((

best

---

### Post by erfahren on 2008-02-10
> **cmfrtblynmb said:**
> Thanks

You are absolutely right

But the problem was that I did not know that 30 gb was overkill, I am used to windows style, where you usually put all your eggs to same basket as default!! Other than that vista alone uses sth close to 10 to 20 gigs with softwares u install. 

But there is not much I can do about space management right now:((

best
no worries - you can use GParted to resize your root - if your /home is next to it (which it probably is) you can shrink down the root to about 5 GB and add that to your /home

GParted is included on the Ubuntu LiveCD - when booted up from the CD enviroment you can modify the partitions

why don't you do this to start - install GParted and launch it. Take a screenshot (Alt+PrntScrn) of your partition table in it and post it here.

To do that, open a terminal (Apps > Accessories > Terminal) and in there enter:
```

sudo apt-get gparted

```

once installed - it'll be in the menu (System > Admin > Partition Editor)

(It works well - I've resized and moved my ext3 partitions with it a couple times)

---

### Post by erfahren on 2008-02-10
OOPS! sry

that's
```

sudo apt-get install gparted

```
(I kenw that command looked too short!)

---

### Post by cmfrtblynmb on 2008-02-10
Thanks

I know about gparted, actually I used it before using Linux, I have the live cd. 

I will resize my partitions, though it is a very long and painful job

---

