---
title: "Repository problem in Edgy"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Stunt Double on 2007-06-11
Whenever I use "sudo aptitude update" or any other update method,  I get the following output:

93% [6 Sources gzip 0] [5 Packages bzip2 0] [9 Packages 959/42.3kB 2%] 
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources                    
  Sub-process gzip returned an error code (1)
94% [7 Sources gzip 0] [5 Packages bzip2 0] [9 Packages 6767/42.3kB 15%]
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Sources                
  Sub-process gzip returned an error code (1)

    The problem started when I tried to use the update manager to upgrade to Feisty. No matter which method I use, the same failed output occurs.
   I've decided to stay with Edgy for now but would like to update Edgy packages when necessary.

Is there a fix?
Thanks

---

### Post by malathia on 2007-06-11
post your /etc/apt/sources.list please. Thanks

---

### Post by Stunt Double on 2007-06-11
Here it is:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

Thanks

---

