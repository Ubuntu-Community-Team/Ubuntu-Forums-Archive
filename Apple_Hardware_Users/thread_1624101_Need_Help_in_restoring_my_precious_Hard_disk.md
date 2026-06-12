---
title: "Need Help in restoring my precious Hard disk"
date: 2010-11-17
forum: Apple Hardware Users
---

### Post by prasjustme on 2010-11-17
Guys,
I have this 1 TB HDD , which had a single NTFS partition. I was planning to repartition it using my Mac OSX Disk Utility( my blunder). Once I did the reparitioning disk  utility ran for like 8 hrs for reparition of 120 Gigs. After seeing no status after 8 hrs , I just plugged it out.
After that am not able to use my HDD seems this wretched utilit has screwed the partition table. Needless to say this 1 TB contains my 10 years of life time.
Till now I have done :

Used R3cover to recover partition table: No luck
Used Stellar for Mac : NO luck( this tool ran for 36 hrs before shouting No Data Found!!)
Am runnig Test Disk: Interesting tool  ran for 30 hrs and asked me to do a deep search now its been running for 2 days with status showing 50% usage
The status shows some 20 Linux parition, 1 Swap parition and 1 unknown partition.
As Far as I know I never created any Liux partition.

  Linux                  329525360  746620911  417095552                                                                                                                                                         
  Linux                  329525384  746620935  417095552                                                                                                                                                         
  Linux                  329525408  746620959  417095552                                                                                                                                                         
  Linux                  329525432  746620983  417095552                                                                                                                                                         
  Linux                  329525592  746621143  417095552                                                                                                                                                         
  Linux                  329525976  746621527  417095552                                                                                                                                                         
  Linux                  329526840  746622391  417095552                                                                                                                                                         
  Linux                  329526896  746622447  417095552                                                                                                                                                         
  Linux                  329527624  746623175  417095552
followed by 1 SWAP and 1 uknown. I still 50% done and would run maybe for another 2 days.
Guys please help me,am not sure sure if this is gong to help, I can try once more with **gpartd** bu tlooks like its more of guess work.
I have seen people with PArition table issues getting solutiong.
Help me guys!!

---

### Post by shawnhcorey on 2010-11-17
Can you run this command and report the results?
```
sudo fdisk -l
```

fdisk is Linux low-level disk utility.  See `man fdisk` for details.

---

### Post by prasjustme on 2010-11-17
Am on macbook and fdisk does not -lu option .The only option I see is
    -i: initialize disk with new MBR
    -u: update MBR code, preserve partition table
    -e: edit MBRs on disk interactively
    -f: specify non-standard MBR template
    -chs: specify disk geometry
    -S: specify disk size
    -r: read partition specs from stdin (implies -i)
    -a: auto-partition with the given style
    -d: dump partition table
    -y: don't ask any questions
    -t: test if disk is partitioned
I did sudo -d to dump the parition and I got
0,0,0x00,-,0,0,0,0,0,0
0,0,0x00,-,0,0,0,0,0,0
0,0,0x00,-,0,0,0,0,0,0
0,0,0x00,-,0,0,0,0,0,0

I did a read able format of partition dump and here is the scary message I see
Disk: /dev/rdisk1    geometry: 121601/255/63 [1953525168 sectors]
Signature: 0x0
         Starting       Ending
 #: id  cyl  hd sec -  cyl  hd sec [     start -       size]
------------------------------------------------------------------------
 1: 00    0   0   0 -    0   0   0 [         0 -          0] unused      
 2: 00    0   0   0 -    0   0   0 [         0 -          0] unused      
 3: 00    0   0   0 -    0   0   0 [         0 -          0] unused      
 4: 00    0   0   0 -    0   0   0 [         0 -          0] unused 
I shudder at very thought that I might have lost all data :(

---

### Post by shawnhcorey on 2010-11-17
Sorry, don't know that much about OS X.  Do you have a LiveCD with Linux?

---

### Post by prasjustme on 2010-11-17
Nope, I dont.
Am running testdisk on the harddisk . Does anybody know why is it taking so long , I mean its like 2 and half days noe since Advanced Search started and it still says 52% complete.

---

### Post by prasjustme on 2010-11-17
If it might help, I was able to restore some files from photorec, the thing is I dont have a spare 1TB hard drisk where I can store this data. Getting 1TB will be my last resort.If testdisk can correct my paritition table then am good.

---

