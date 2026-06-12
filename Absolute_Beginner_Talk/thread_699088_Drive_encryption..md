---
title: "Drive encryption."
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Dissident85 on 2008-02-17
I have herd that you can encrypt a drive when you install ubuntu, I was wondering if it was possible to encrypt one after you have installed ubuntu? and if so how?

also, I have a usb memory stick which I keep sensitive documents. is it possible to encrypt that? can ubuntu do it? or do I need some third party software?

---

### Post by tact on 2008-02-17
G'day mate...

Yes using the ubuntu alternate installer CD you can encrypt right from installation.  Fantastic if you are doing a clean new install.     But it is destructive, data on any partition you encrypt will be lost.

Its possible to end up with a whole disk encrypted (except for /boot of course) after you have already installed ubuntu by doing it partition by partition - BUT..it is still destructive of any data on the partition being encrypted.  Thus meaning you having a LOT of spare space on other partitions, or able to back up all data off the disk AND jumping thru a lot of hoops.

If you do it that way (encrypting partition at a time and moving data around to free space) you will end up with an "awkward" system requiring you to enter in passphrase separately for each partition encrypted.  If you do it at install time you can set up so that only ONE passphrase is needed and that at boot time only.

Instead of thinking "whole disk encryption" and doing it in a piecemeal manner post installation - perhaps its better to just consider having one partition or container set up as encrypted.  If you go this way there are so many choices its not funny.  You don't even have to preallocate a container (partition or file)...  you can use stuff like encfs as well according to your needs.

Yes also - you can encrypt all or part of memory sticks or usb drives etc.  Too many tools to list. :)

What I have done is...  when it came time I wanted to have a clean new install I used the ubuntu alternate installer to do the whole disk encrypted from install time.

I chose to do the partitioning manually so that i can have /home on its own (encrypted/logical volume) partition.   Of course "/" and swap are also encrypted inside the same encryption container - just separate logical volumes.  The only non-encrypted space is 200MB for /boot.

I am prompted once only at boot time for a passphrase.  All lovely and seamless.

Then...  for stuff I want private even when the computer is booted (personal financial data on a company laptop) I use encfs.   I linked the encfs mount and unmount commands to buttons on my panel so that mounting is as easy as "click" and enter passphrase too.
(I guess I could also use the inbuilt dm-crypt/LUKS for that too and just have a different passphrase.  Will look into that later).  :)

---

### Post by spacefreak86 on 2008-02-17
Can't you use TrueCrypt? I had it on windows and it was awesome. I noticed that it was available for Linux, but I don't know how to get it working.

---

### Post by hyper_ch on 2008-02-17
truecrypt can't full encrypt your system in linux. However it can encrypt other partitions....

---

### Post by Sinkingships7 on 2008-02-17
i use truecrypt. it's great. just search for it in the repo's. you'll be able to create a virtual image, which will be mounted (by truecrypt) as a hard drive. you can then store your files on it (they're encrypted as it goes in) and put the image file onto your flash memory stick. 

keep in mind that you won't be able to access the files on your flash drive on another computer without truecrypt.

---

