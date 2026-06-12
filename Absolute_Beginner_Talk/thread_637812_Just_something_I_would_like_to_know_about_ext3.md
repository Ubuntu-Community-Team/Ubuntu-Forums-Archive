---
title: "Just something I would like to know about ext3"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by billgoldberg on 2007-12-11
I know in windows, deleted files can be recovered by special (even freeware) programs if you delete them the normal way. You need to shred (overwite) the files a x ammount of times before it really never can be recovered again.

Is that the same with linux/ext3? 

Meaning, if I delete my trash folder, are all those file 100% completely gone, or can they still be recovered by some tech guy/police/hacker/ ...

Why would I want to know that? What did you say bunny?

[IMG]http://www.edu.lahti.fi/~lloikkan/art/paranoid.jpg[/IMG]

Indeed.

---

### Post by reckless2k2 on 2007-12-11
there are "wipe" programs for linux as well in active mode so you can delete/scrape any trace of that file once you delete it. 

to answer your question, a police hacker guy can recover it unless you do the same in linux. the police hacker guys are using linux. hahaha. 

BTW, the avatar is AWESOME!!! seriously.

---

### Post by Steveway on 2007-12-11
So and why don't you even try to search the information before you ask?
If you did then your first stop would be at wikipedia where you can find this:
> Undeletion

Unlike ext2, ext3 zeroes out block pointers in the inodes of deleted files. It does this to simplify read-write access to the filesystem when the journal is being replayed after an unclean mount. This, however, effectively prevents files from being undeleted. The user's only recourse is to grep the hard drive for data known to signal the start and end of the file. This provides slightly more secure deletion than ext2, which can be either an advantage or a disadvantage.
In short, you shouldn't been able to undelete files because it writes zeros over it.
--Just a little education as an added bonus to your answer.--

---

### Post by lswest on 2007-12-11
i believe you can run "rm" in verbose mode and have it re-write nulls over that space, not entirely sure though, worth checking out though

---

### Post by mcduck on 2007-12-11
> **Steveway said:**
> So and why don't you even try to search the information before you ask?
If you did then your first stop would be at wikipedia where you can find this:

In short, you shouldn't been able to undelete files because it writes zeros over it.
--Just a little education as an added bonus to your answer.--

That's true, recovering deleted files from Ext3 is pretty hard.

But it's not impossible. It's not a file system thing, but relates to the way hard disks work. To make absolutely sure that nobody can get the data back you'd need to overwrite it with random data couple of times. I'm not sure how to do this for a single file, but to shred a whole disk/partition this way is pretty easy in Linux (using 'dd' and /dev/random).

---

### Post by billgoldberg on 2007-12-11
> **reckless2k2 said:**
>  BTW, the avatar is AWESOME!!! seriously.

I know, that's why it there :p:p:)

Does anyone also knows a program to actually delete the files 100%. I'm not really good with the terminal except for the really basic stuff.

I never use wikipedia anymore ever since it's scandals.

---

### Post by HermanAB on 2007-12-11
Sigh... Wipe and shredder utilities DO NOT WORK with modern file systems.  See my previous posts.

The military collect old drives and toss them into steel smelters to delete the data.  There is a good reason for that.

Cheers,

H.

---

### Post by billgoldberg on 2007-12-11
> **HermanAB said:**
> Sigh... Wipe and shredder utilities DO NOT WORK with modern file systems.  See my previous posts.

The military collect old drives and toss them into steel smelters to delete the data.  There is a good reason for that.

Cheers,

H.

Are you sure about that?

Let's say i need to delete all the data on my drive. So i partition it to nfts and install windows. Shouldn't that have destroyed all the data from ubuntu?

I'll extend that question somewhat.

Is my linux partition even save, meaning, can someone get past ubuntu's username and password login without knowing my password? Or hang the harddrive in another computer and access it from another operating system and hacking into it that way?

---

### Post by mcduck on 2007-12-11
> **HermanAB said:**
> Sigh... Wipe and shredder utilities DO NOT WORK with modern file systems.  See my previous posts.

The military collect old drives and toss them into steel smelters to delete the data.  There is a good reason for that.

Cheers,

H.

Overwriting the disk multiple times with random data works just fine. It just takes long time to do as the disks are very big these days..

Even overwriting a modern 300GB disk once takes very long time, and doing it 20 times takes a lot longer than what many are willing to do, if they don't have to worry about the money issues.

---

### Post by HermanAB on 2007-12-11
Overwriting the disk multiple times with random data doesn't work either.  The only way to overwrite it with some modicum of success is to activate the built-in erase utility in the drive controller: [http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

If you really need to erase the data, get a very big hammer and anvil.

---

### Post by PetePete on 2007-12-11
theres a utility that comes with ubuntu (i think) called shred... just type it in the console and read its help output.

it will shred (overwrite iwth random data) a file  25 times which is considered to be secure enough to prevent any specalist equipment from being able to pick magnetic residue.
Some people may say that it doesnt work with ext3, this is all depended on if the file system has been set to data=ordered (if it has, then shred will work) which ubuntu does as default.

but yes.. a VERY hot fire is the only way to be 100% secure :)

---

### Post by mcduck on 2007-12-11
> **billgoldberg said:**
> Are you sure about that?

Let's say i need to delete all the data on my drive. So i partition it to nfts and install windows. Shouldn't that have destroyed all the data from ubuntu?

No, it's still possible to recover at least parts of the data with proper tools. But that's very expensive so unless you have loads of money I wouldn't count on that option..

The thing is that in the end hard disks are still analog devices, and the read/write head doesn't every time travel exactly the same route over the disk. This leaves traces of old data on the disk and while normal tools are not able to read them there are companies who have specialized in data recovery and can use that old information to find out what used to be on the disk.

Overwriting the disk multiple times with random data makes even this approach impossible, you just have to do it many times enough. But that takes a long time to do so it's often just easier to destroy the disk in some other way if you don't need to use it any more.

---

### Post by HermanAB on 2007-12-11
[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

---

### Post by LaRoza on 2007-12-11
Use "shred". ```
man shred
```

---

### Post by mcduck on 2007-12-11
> **HermanAB said:**
> [http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

After browsing a while on that site, and reading the PDF on the page you posted, I wans't able to find any other reason for overwriting the disk with random data multiple times than these:

 "it is vulnerable to malware and incomplete erasure of all data blocks. Examples are data blocks reassigned by drives, multiple drive partitions, host protected areas, device configuration overlays, and drive faults."

"the old data overwrite document DoD 5220 calls for multiple block overwrites of Confidential data, which can take more than a day to complete in today’s large capacity drives. So users make tradeoffs between the time required to erase data and the risk that the next drive user may know and use recovery techniques which can access weakly erased data."

I don't thing we have to worry about  malware when talking about 'dd' program in Linux, and it's easily able to handle the other problems mentioned, apart from possible bad blocks on the drive which the drive itself has reassigned to different parts of the disk. But I wouldn't think it's likely that you would have large enough part of the disk with bad blocks that they would contain any important data..

 So we are only left with the things I have already mentioned; it takes long time to do and because of that people may not do the overwrite as many times as would be required.

---

### Post by HermanAB on 2007-12-11
The special erase routine in the drive controller, will overwrite the whole disk, including the 'empty' space between tracks - this is good enough for ordinary mortals.  Normal write actions will run approximately down the standard tracks, with the result that all previous data can be recovered from the space between the tracks.  Military recovery systems can read 20 or more 'layers' of old data from a used disk by reading the gaps between the tracks!

So, for military use, disks can be erased for re-use at the same or higher classification, but the disk drive cannot be downgraded to a lower level.  The only permanent way to erase data is the physical destruction of the disk.  Old disks are collected and destroyed in a steel blast furnace so it becomes part of a new car or something.

Cheers,

H.

---

### Post by thelatinist on 2007-12-11
What all this boils down to is that unless you're looking to hide something from the military, an intelligence agency, specially-trained police forces, or a private individual with lots of money and a strong motivation to read your hard disk, shred should be more than adequate.

---

### Post by scorp123 on 2007-12-11
> **Steveway said:**
>  In short, you shouldn't been able to undelete files because it writes zeros over it.  You are mistaken ... or rather: You are misinterpreting the information you yourself provided. "ext3" only zeroes the block pointers pointing to the file ... but not the file contents themselves. Those could still be retrieved e.g. by someone who knows what he is looking for. With the block pointers gone it's just harder ... but not impossible.

EDIT .... or maybe I misunderstood what you wanted to say? Sooorry about it then, seems I am too tired.

---

### Post by HermanAB on 2007-12-11
Exactly, shred only works on Ext2. It doesn't actually work on any other file system.

---

### Post by Niniel on 2007-12-11
> **HermanAB said:**
> [http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

The interesting thing about that article though is that even their most secure method of "erasing" drives seems to rely on physically overwriting the encryption keys. 

The best thing to do is probably to use full disk encryption and then employ the hd erase function to wipe that. After overwriting that with another encrypted file system, your old date ought to be safe.

---

### Post by Martje_001 on 2007-12-11
> **billgoldberg said:**
> Is my linux partition even save, meaning, can someone get past ubuntu's username and password login without knowing my password? Or hang the harddrive in another computer and access it from another operating system and hacking into it that way?
No =]. Password are not saved on the computer. If you typ your password linux compares it to another file.

See it like this:
if **password you have given** x **password you have given** = **file which linux has saved**, the passord is OK

If **password you have given** x **password you have given** != **file which linux has saved**, the passord is wrong.

Edit: Yes, the person which hangs the drive into another computer can see all your files. 
Maby you want to setup encryption with EasyCrypt. EasyCrypt will make a vault, which you (even the goverment if you choose a strong password) **can't** read unless you have the right password.

---

### Post by Steveway on 2007-12-11
> **scorp123 said:**
> You are mistaken ... or rather: You are misinterpreting the information you yourself provided. "ext3" only zeroes the block pointers pointing to the file ... but not the file contents themselves. Those could still be retrieved e.g. by someone who knows what he is looking for. With the block pointers gone it's just harder ... but not impossible.

EDIT .... or maybe I misunderstood what you wanted to say? Sooorry about it then, seems I am too tired.

Now that you say it, I got a bit unsure.
You are propably right, and it got "lost in translation". (I'm not a native english-speaker so things like this can happen but shouldn't.)

---

