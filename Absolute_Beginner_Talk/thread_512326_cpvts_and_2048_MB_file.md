---
title: "cpvts and 2048 MB file"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by skao on 2007-07-29
Hi 

I try to copy my DVD to my harddrive, when I use cpvts to create file in 1024 MB block it is fine but when I try  to create the file in 2048 MB block it gave me the error message that said "File Size limited exiscced" after the first file, but look like the file is created successfully. As I can use Totem to open and play it.

My file system is XFS, and when I type ulimit the respond is unlimited, and unlimit -a give me the following, 

core file size   (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 20
file size               (blocks, -f) unlimited
pending signals                 (-i) unlimited
max locked memory       (kbytes, -l) unlimited
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) unlimited
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) unlimited
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

so I think my file size is unlimited. Does anyone else got the same problem. My Ubuntu version is 7.04

Thanks and Regards,
Stephen

---

### Post by DBStevens on 2007-07-29
The question is who issued the message XFS or cpvts.

XFS is fully LFS the last I knew.  However  that doesn't mean much if the program producing the files thinks differently.  That program you are using is from April 13, 2003 

I suggest reading this link:

[http://en.wikipedia.org/wiki/Large_file_support](http://en.wikipedia.org/wiki/Large_file_support)   

paying particular attention to this line:

Andreas Jaeger (Feb 15 2005). "Large File Support in Linux". SuSE GmbH (now Novell, Inc.). Retrieved on 2006-09-10. 

noting the date.

I would suggest using a different program such as K3b  that has a more recent release date than the date of that paper above.

---

