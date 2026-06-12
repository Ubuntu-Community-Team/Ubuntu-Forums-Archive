---
title: "simple command line questions"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by hill0093 on 2007-07-02
is there a way to have ls list the last modification time
instead of the last access time?
is there a way to have ls count files and directories like dir?
No I really don't want it to be microsoft,
just to do some of the things I am used to using.
For example, I use ls -latr a lot.

---

### Post by davidjmayo on 2007-07-02
```
ls --help

or 

man ls
```

---

### Post by dwanders on 2007-07-02
Not a Linux guru or anything, but coming from Windows myself, sometimes you just plain get used to things a certain way. Problem is Linux & Unix in general are much more flexible than WIndows ever could be.  

I think ls -latr should already be sorting by modification time (thats what the man says any way)

to get a file count you want to send your output to a counter
ls -latr | wc -l

So you could very quickly and easily get a list with a file count by doing the following:

1) open a terminal
2) gedit .bashrc
3) scroll down to the very bottom of the file
4) add this line:
------> alias dir='ls -latr && ls -later | wc -l'
5) save and exit gedit
6) close your terminal
7) open a new terminal and type dir see what you get

You can get much more creative, by looking up more info on the .bashrc alias. I did a Google search on "counting files with ls" and "bashrc alias" to provide the information I gave you.

Hope this helps you out.

---

### Post by Rocket2DMn on 2007-07-02
> **dwanders said:**
> 

So you could very quickly and easily get a list with a file count by doing the following:

1) open a terminal
2) gedit .bashrc
3) scroll down to the very bottom of the file
4) add this line:
------> alias dir='ls -latr && ls -later | wc -l'
5) save and exit gedit
6) close your terminal
7) open a new terminal and type dir see what you get

You don't have to close the terminal, just type
```
source .bashrc
```
This works for any scripts or shell configs you modify.

---

### Post by hill0093 on 2007-07-02
I was too dumb to understand the man ls.
That is why I asked. All I have to do is copy
a file and the time changes, not as useful.
The ls -a seems to be invalid.
What does the && do?
thanks for the wc -l that I did not know existed.
;)

---

### Post by kpkeerthi on 2007-07-02
Its a command seperator.

```

command1 && command2 && command3 

```
is equivalent to 
```
command1 <press-enter> 
command2 <press-enter>
command3 <press-enter>

```

---

### Post by dwanders on 2007-07-02
The && will execute the next command only if the first command succeeds. So when I said:

ls -latr && ls -latr | wc -l

the ls -latr | wc -l will only run if the ls -latr run without error. 

What I would really do (and I plan to tinker with this a bit tonight as I would like to learn this stuff =) too ) is write a small shell script called dir and put it in the /usr/local/bin folder that does exactly what you want. Then when you type dir at the command line - you will get the output you want without having to do the alias sutff.

---

### Post by hill0093 on 2007-07-02
Thanks, That would be nice. 
I made an error earlier.
I meant ls-e seems to be in error.
Also try copying a file and 
see that the time changes.;)

---

### Post by dwanders on 2007-07-02
OK, I am sure this is unsecured, or written bad, or could even not display things correctly, but this what I have so far:

1) open a terminal
2) gedit DIR      <- note: there is a command called dir in /bin/dir check man dir for what it does
3) past the following into said file:

#!/bin/bash
#  DIR - pretend we're the DIR command in DOS and display 
#  something similar to the DOS stuff

dircount=`ls -lAtr | grep '^d' | wc -l`
totalcount=`ls -lAtr | wc -l`
filecount=`expr $totalcount - $dircount`

ls -lAtr
echo $filecount " File(s)"
echo $dircount " Dir(s)" 
df -h .

exit 0

4) File save
5) chmod 777 DIR
6) su cp DIR /usr/local/bin
7) DIR  <-- see what it does

I think the counting is also counting the total at the top of the display causing the file count to be 1 greater than it should be. :-k hummm

---

### Post by dwanders on 2007-07-02
Yes, I think this clears up the miscount:

#!/bin/bash
#  DIR - pretend we're the DIR command in DOS and display 
#  something similar to the DOS studd

dircount=`ls -lAtr | grep '^d' | wc -l`
totalcount=`ls -lAtr | wc -l`

finalcount=`expr $totalcount - 1`

filecount=`expr $finalcount - $dircount`

ls -lAtr
echo $filecount " File(s)"
echo $dircount " Dir(s)" 
df -h .

exit 0

---

### Post by LouisvilleLIP on 2007-07-02
This is reasonably helpful

[http://www.linuxcommand.org/learning_the_shell.php]("http://www.linuxcommand.org/learning_the_shell.php")

---

### Post by dwanders on 2007-07-04
Here is another one, this was purely a learning exercise:

copy and past this into a file:

#!/usr/bin/perl

my $ls_output = `/bin/ls -lAtrsgF --time-style=long-iso`;

my $dircount = `ls -lAtr | grep '^d' | wc -l`;
my $totalcount =`ls -lAtr | wc -l`;
my $filecount = --$totalcount - $dircount;
my $apparent_du = `du -sh`;

my @files = split /\n/, $ls_output;
my $line;

foreach $line (@files)
{
        #remove the caridge return (chomp), then split the line into its useable
        # fields. Then printflog() them out specifically spaced with printf()
        chomp($line);
        $line =~ s/ +/,/g;
        ($blank, $number, $permissions, $links, $owner, $size, $date, $time, $filename)=split(/,/,$line);
        if ($blank eq "total")
        {
            next;
        }
        elsif ($blank ne '')
        {
            print "$size  $date  $number\t$owner\t$time\n";
        }
        else
        {
            print "$date  $time  $permissions\t$size\t$filename\n";
        }
}
printf "            %d File(s)\n", $filecount;
printf "            %d Dir(s) - Disk Usage %s", $dircount, $apparent_du;

---- stop copying above

save the file as john (or what ever you want to call it)
exit the editor
open a terminal
chmod 777 john
sudo copy john /usr/local/bin

then run it
john

Should give you an output similar to DOS. I also played around with DOS emulator it was pretty cool, and might do what you need if your willing to dig into it. I would also only run john on small directories, or I would remove all the Disk Usage stuff from the perl above. 

Anyway, I think I am done playing with this =) it was fun for a bit.

---

### Post by hill0093 on 2007-07-06
Thanks.;)
Is there a way to list hard drive partitions on 
my machine and some info maybe like format?

---

### Post by az on 2007-07-06
> **hill0093 said:**
> Thanks.;)
Is there a way to list hard drive partitions on 
my machine and some info maybe like format?

Sudo parted

then

print


As well, to find files by date:

See ([http://www.securityfocus.com/infocus/1738](http://www.securityfocus.com/infocus/1738))

Quote:
The find command is one that can be quite useful. find can be used to search the file system for files that have been changed, accessed, or modified using the -ctime, -atime, and -mtime arguments. Be aware that the atime will change on directories as you run find. If the purpose of using find is more formal than exploration, you should be working on a read-only image. 

Most Linux systems include GNU find[10], from the coreutils package. The GNU version of find is quite powerful because of the variety of features it offers to users. A time range can be specified and find will print the timestamps on the data in that range. If you want to search for files modified more than two, but less than seven days ago and print their mtime, ctime, and inode, you can use: 

# find / \( -mtime +2 -a -mtime -7 \) -a -printf "M:%t  C:%c  %i\t%p\n"
If you don't have GNU find, you can use the stat command, assuming you are using Linux. If you don't have access to the stat command, but do have perl, you can use perl as a stat(2) wrapper: 

# find / \( -mtime +2 -a -mtime -7 \)|perl -ne 
    'chomp;($i,$m,$c)=(stat)[1,9,10];printf"M:%s\t$i\t$_\n",localtime($m)."  C:".localtime($c)'
One possible attack vector for compromising a *nix host is to use a broken suid or sgid binary to escalate privilege. Attackers also sometimes leave suid root shells on the file system for their convenience. find can be used to hunt down such files. To search for suid and sgid files and display their information, use: 

find / -perm -6000 -ls
A few more examples of using find appear below: 

the find command in action:  
##==
##== find all files which have had their status changed in
##==   the last 24 hrs (display ctime, inode, and filename)
# find / -ctime -1 -printf "%c  %i\t%p\n"
Fri Sep  7 11:55:14 2003  174945        /var/lib/rpm
Fri Sep  7 11:55:14 2003  174946        /var/lib/rpm/__db.001
Fri Sep  7 11:55:17 2003  174947        /var/lib/rpm/__db.002
Fri Sep  7 11:55:17 2003  174948        /var/lib/rpm/__db.003
Fri Sep  7 11:55:55 2003  160125        /var/lib/random-seed
Fri Sep  7 11:55:16 2003  222706        /var/log
Fri Sep  7 12:17:05 2003  224545        /var/log/messages
[ output deleted ]
##==
##== find all files which have had their status changed from
##==   5 to 30 (inclusive) days ago and display the ctime, inode, and filename
# find / -ctime +4 -ctime -31 -printf "%c  %i\t%p\n"
Sat Aug 30 19:49:52 2003  414661        /boot/System.map-2.4.20-20.8bigmem
Sat Aug 30 19:49:52 2003  414662        /boot/config-2.4.20-20.8bigmem
Sat Aug 30 19:49:52 2003  414663        /boot/module-info-2.4.20-20.8bigmem
Sat Aug 30 19:49:53 2003  414664        /boot/vmlinux-2.4.20-20.8bigmem
Sat Aug 30 19:49:53 2003  414665        /boot/vmlinuz-2.4.20-20.8bigmem

---

### Post by hill0093 on 2007-07-06
What i meant was that I want to see how 
my disks are partitioned and formatted. 
Even the unmounted ones.

---

### Post by az on 2007-07-06
> **hill0093 said:**
> What i meant was that I want to see how 
my disks are partitioned and formatted. 
Even the unmounted ones.

Well, parted will show you that.  It can only do one drive at a time, though.

To run parted on a drive other than your default one, do

sudo parted /dev/sdb

where /dev/sdb is a second hard drive on your system.  In parted, print will show you the different partitions as well as the filesystem in it,

---

