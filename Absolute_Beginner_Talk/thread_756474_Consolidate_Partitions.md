---
title: "Consolidate Partitions"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by davidajohnson12 on 2008-04-15
I am in the initial stages of transitioning to Linux but I am getting the hang of it and I LOVE it so far. However, after installing Ubuntu 3-4 times without wubi and then once with wubi, my hard drive is now all messed up (see the attached image). I have my main hard drive which has windows and Ubuntu on it and then I have 2 partitions with unallocated space. The 10GB partition was the recovery partition that is created with Windows Vista. And the 102.96GB partition, I created to install Ubuntu on before Wubi worked with hardy heron. I would like to consolidate these into one hard drive, but gparted won't let me resize my main partition and I can only format the other two. Anyone know how I might accomplish this? Thanks.

Dave

---

### Post by Inxsible on 2008-04-15
I dont think you can merge partitions unless you delete them. So in short you will have to delete 3 partitions the 10GB, the NTFS is the middle and the 102 GB one to merge them.

You will probably have to re-install Ubuntu.

I am not sure if NTFS partitions can be moved. So if you delete the 10GB partition, you can probably move the NTFS partition which would then leave you with 102 GB at the end and the NTFS partition will be 10GB larger, You can then shave 10 GB off at the end of the NTFS and then merge that into the 102 giving you 112GB.

That means that you will have to reinstall Ubuntu at least.

---

### Post by davidajohnson12 on 2008-04-15
thanks for the prompt response. the two empty partitions have been deleted...they are only unallocated space at this point, no formatting or anything. I have tried merging the partitions every way I can think of and nothing works...any other ideas?

---

### Post by Inxsible on 2008-04-15
> **davidajohnson12 said:**
> thanks for the prompt response. the two empty partitions have been deleted...they are only unallocated space at this point, no formatting or anything. I have tried merging the partitions every way I can think of and nothing works...any other ideas?
and you dont have the move option on the NTFS partition, do you ?

---

### Post by davidajohnson12 on 2008-04-15
nope... :(

---

