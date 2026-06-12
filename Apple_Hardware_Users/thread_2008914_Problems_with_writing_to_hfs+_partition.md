---
title: "Problems with writing to hfs+ partition"
date: 2012-06-23
forum: Apple Hardware Users
---

### Post by bogren on 2012-06-23
Hi I am dualbooting os x Lion and ubuntu 12.04 on my macbook 5.1. I use os x as my storage partition and have symlinks in my linux home folder. 

But very often ubuntu stops being able to wright to the hfs+ volume  (journaling disabled). There's a lock on the symlink icons and the only fix I've found is to reboot into os x and repair permissions in disc utility. But after some use the problem returns.

What is wrong?
I have same uid on both systems.

This is very frustrating as I have my shotwell-folder and downloads folder on the hfs+ volume.

Thank you!

Edit: When I repair permissions it is usr/lib/ruby that has errored. I don't now if that can help figure out what the problem is. Also I dualboot with refit. I don't have to startup os x for the permissions to be changed to the wrong values.

---

