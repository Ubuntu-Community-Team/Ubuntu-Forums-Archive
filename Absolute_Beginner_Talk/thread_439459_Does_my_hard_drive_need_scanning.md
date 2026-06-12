---
title: "Does my hard drive need scanning?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-05-10
I'm trying to install Feisty on a Maxtor 52049u4 hard drive.

It seems to take longer to install than it does on my other hard drives and then, when I re-boot, the program will not install beyond ' UBUNTU ' plus about 1/4" of color in the rectangular box.

Should it be possible for me to run ' fsck ' to check for disc errors?

When I try ' showfsck ' in Terminal I get:-

>>>>>
The program 'showfsck' is currently not installed.  You can install it by typing:
sudo apt-get install showfsck
Make sure you have the 'universe' component enabled
bash: showfsck: command not found
<<<<<

When I look in Synaptic, the closest thing I can see is ' e2fsck - static ' but I don't know if this is what I need. 

Here is the description:-
>>>>
statically-linked version of the ext2 filesystem checker
This may be of some help to you if your filesystem gets corrupted enough
to break the shared libraries used by the dynamically linked checker.

This binary takes much more space than its dynamic counterpart located
in e2fsprogs, though.

You may want to install a statically-linked shell as well, to be able
to run this program if something like your C library gets corrupted.
<<<<

---

### Post by tophatandy on 2007-05-10
Well.. this certainly isnt a suggestion.. but I had the exact same problem on my desktop a while ago (before 7.04) and I had to zero fill my drive to eliminate any trace of vista.

I will be looking into this tho.

---

