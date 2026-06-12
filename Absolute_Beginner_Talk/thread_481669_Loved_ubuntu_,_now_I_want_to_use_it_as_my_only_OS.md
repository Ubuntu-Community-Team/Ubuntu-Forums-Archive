---
title: "Loved ubuntu , now I want to use it as my only OS"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by babacan on 2007-06-22
Greetings,
I personally loved Ubuntu and decided to stop using Windows at all. Now I am planning to solo use Ubuntu as I am a future computer scientist (currently studying) since it is serving everything I want. Also I have no desire to play games (hell , even if I do , I can simply find it out via Wine or whatever :) ).

Now comes the question.

I have single HDD which is divided into partition such as:
 
Partition one: Windows (around 50 gbs)
Partition two: Storage (such as mp3s videos etc) (around 80 gbs)
Partition three: Ubuntu storage (5gb)
Partition four: Swap space for Ubuntu (like 500 mbs)

Now , as I want to single use Ubuntu , I want to get rid of the Partition one(windows partition). Here are my questions regarding it:

1- Considering I have around 100~ gb empty space after merging and formatting Ubuntu+Windows+Swap ; How much space do you recommend for the swap area and the Ubuntu partition.

2- I am not able to modify the Storage partition as it is currently shown as "read only" , what do you recommend me to do with it , how to make it a partition which I can use as storage (add , remove files) Also will it still possible to make this part as "home directory" or merge it to my home directory or such?
Thanks in advance!

---

### Post by NeoLithium on 2007-06-22
1- Not entirely sure, it's mostly up to you. I have my swap as equal to my RAM, and generally a 10GB / partition is good. I'd recommend that you have a seperate /home should the need for a reinstall happen as well.  I'm not CERTAIN about how, but you could decide those sizes and probably merge the remaning space into a larger storage partition for however you like.  The possibilities are actually quite wide open for you :)

2- Since your storage partition is *probably* nfts, due to windows, you can take a look here, which will show you about keeping it as NFTS but having read/write permissions on it from within linux: [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by babacan on 2007-06-22
Thanks NeoLithium for taking your time , I will try what you said :) Guess I should leave a 10gb swap space since I have 1gb ram :)

---

### Post by diatribe on 2007-06-22
10GB is WAY too much swap space, 1gb will do fine and probably be too much

---

### Post by Nekiruhs on 2007-06-22
> **diatribe said:**
> 10GB is WAY too much swap space, 1gb will do fine and probably be too much
He was referring to the / section of your hard drive. Not Swap.

---

### Post by molly_001 on 2007-06-23
Ubuntu will take just under 3 GB on a fresh CD install onto /(root),
if using the Alternate Install CD.

Then it will pop to about 3.3 GB after updates, Automatix, etc.

So I'd say you will want 10GB for the Ubuntu /(root)

... more if you are going to have /(root)/home .

(whereas /home, whether you place it on a separate partition for itself or not, will be the default directory for your docs.  I like a separate partition (ext3) for home, so that I can upgrade Ubuntu whenever I want without affecting my personal docs.)

---

