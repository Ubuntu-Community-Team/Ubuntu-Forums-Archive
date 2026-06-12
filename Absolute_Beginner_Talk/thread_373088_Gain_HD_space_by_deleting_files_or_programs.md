---
title: "Gain HD space by deleting files or programs??"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by gwilson on 2007-02-28
I not exactly a newbie but thought this might be a good place to ask this question.

I have Edgy installed on an old Toshiba laptop with only a 6 GB drive. I prefer Gnome and do not want to change my desktop or window manager, but I would like to get rid of stuff I do not need. I am thinking things like MAN pages, DEBs for things already installed, source code files, and maybe some large programs that I dont really use. I have used synaptic to remove all of the most obvious programs. Please offer any suggestions you can. Thanks

---

### Post by rccharles on 2007-02-28
> **gwilson said:**
> I not exactly a newbie but thought this might be a good place to ask this question.

I have Edgy installed on an old Toshiba laptop with only a 6 GB drive. I prefer Gnome and do not want to change my desktop or window manager, but I would like to get rid of stuff I do not need. I am thinking things like MAN pages, DEBs for things already installed, source code files, and maybe some large programs that I dont really use. I have used synaptic to remove all of the most obvious programs. Please offer any suggestions you can. Thanks

How much free space do you have now?

applications > accessories > terminal
df

How do you have your harddrive partitioned?
fdisk -l

Clean out your apt-get archive.  All (most?) the various Ubuntu download programs use this archive.
man apt-get
apt-get clean


How much space do you want?

Robert

---

### Post by gwilson on 2007-03-02
> **rccharles said:**
> 

How much space do you want?

Robert

Thanks, Robert. 

I just want to pick up what I can so that I can load on a bit more music. I mainly use this laptop to listen to music files or streaming audio while I fall asleep.

I just have an ext3 partition plus a swap of about 500 MB. Very simple. I suppose the swap could be smaller. I deleted all of the DEBS and set Synaptic to not save future debs.

Might there be any source code files that I can get rid of?

How about an old kernel that has been updated?

Glen

---

### Post by punx45 on 2007-03-03
most source packages never break out of the kilobyte range.   and the kernels by convention are kept at a megabyte or two.  you aren't going to make any considerable storage gains by removing them.   

if you are really struggling to keep your drive from bursting you might want to consider adding an external drive for the media, or moving to network storage if you have a desktop with some free space.

and for goodness sake, don't hurt the man pages!! :cry:

---

### Post by rccharles on 2007-03-03
> **gwilson said:**
> Thanks, Robert. 

I just want to pick up what I can so that I can load on a bit more music. I mainly use this laptop to listen to music files or streaming audio while I fall asleep.



I am not a Linux power user...  I am surprised more folks haven't commented.

...

I noticed in my Ubuntu 6.10 install there is a program that displays the size of folders.  You find it via:
Applications > Accessories > file size ???

( I forget the name )

...

in Applications > Accessories > Terminal  You can poke around with the find command:
# to list files that haven't been accessed in the last three days on the Desktop
 find ~/Desktop -atime 3 

# Find files greater than 512 * 50
find ~/Desktop -size 50

# complete system

find / -size 5000

...

Open Office is fairly big ... if you don't need it x

Robert

---

### Post by rccharles on 2007-03-06
> **gwilson said:**
>  I would like to get rid of stuff I do not need.

Consider using baobab -- Disk Usage Analyzer

See:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=baobab&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=baobab&searchon=names&subword=1&version=all&release=all)

Robert

---

