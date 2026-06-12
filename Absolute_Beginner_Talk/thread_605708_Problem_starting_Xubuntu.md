---
title: "Problem starting Xubuntu"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by nwrann on 2007-11-07
Hi everyone, I have an old Dell laptop that we've been upgrading (i.e. new HD, SDRAM, DVD player) , and I've finally got Xubuntu on it. It's been fine for a few weeks, but this morning I got this message when I turned it on:

          /dev/hda1 contains a file system with errors; force disk check

/dev/hda1 : UNEXPECTED INCONSISTENCY;  run fsck manually
       (i.e. without -a or -p options)
fsck died with exit status 4                                                [fail]
*An automatic file system check (fsck) of the root system failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.
*The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system mainenance, press CONTROL-D to terminate the maintenance shell and restart the system.
      bash: no job control in this shell
      bash: groups: command not found
      bash: lesspipe command not found
      bash: The: command not found
The program 'apt-get' is currently not installed. You can install it by typing apt-get install apt
      bash: apt-get: command not found
      bash: dircolors: command not found
      bash: The: command not found
The program 'apt-get' in currently not installed. You can install it by typing: apt-get install apt
      bash: apt-get: command not found
      root@laptop: 



So that's my issue. I haven't really done much by way of messing around with Xubuntu so I really only have a mild understanding of what's going on here. The dev/hda1 error I understand, but all of the bash errors and The apt-get error is very confusing to me, as it seems to be a Catch-22. 

I'm thinking I should try and start again from scratch, burn a CD and try and load maybe the Gutsy version of Xubuntu?


Neva

---

### Post by taurus on 2007-11-07
At the prompt, run

```
fsck -y /dev/hda1
```

---

### Post by nwrann on 2007-11-07
OK, I did that...and this happened:

     usage: fsck.ext3 [-panyrcdfvstDFSV] 
[-b superblock][-B blocksize][-I inode_buffer_blocks][-P process_inode_size][-l|-L bad_blocks_file][-C fd][-j external_journal][-E extended options] device
   
     Emergency help:
         -p                                   Automatic repair (no questions)
         -n                                   Make no changes to the filesystems
         -y                                   Assume "yes" to all questions
         -c                                   Check for bad blocks and add them to bad block list
         -f                                    Force checking even if filesystem is marked clean
        -v                                    Be verbose
         -b superblock                Use alternative superblock
         -B blocksize                  Force blocksize when looking for superblock
         -j external_journal         Set location of the external journal
         -l bad_blocks_file         Add to bad blocks list
         -L bad_blocks_file       Set bad blocks list
 root@laptop:#

I hope this is a good sign...?

---

