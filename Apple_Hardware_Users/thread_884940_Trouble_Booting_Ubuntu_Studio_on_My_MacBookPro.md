---
title: "Trouble Booting Ubuntu Studio on My MacBookPro"
date: 2008-08-09
forum: Apple Hardware Users
---

### Post by markyboy1980 on 2008-08-09
Hi there

I'm completely new to the Ubuntu experience, but have just managed to partition the hard drive and install Ubuntu Studio on my MacBookPro.

Anyway, when I ask it to boot into Ubuntu Studio it begins launching, then asks me for my login (just my christian name, "mark"), then asks me for my password... This it accpets, then it begins telling me about how "Ubuntu comes with ABSOLUTELY NO WARRANTY" etc etc... (yeah well, I wasn't expecting one!)

It then says...

"To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

And it then gives me the following prompt...

mark@ubuntu:~$

And I'm now screwed if I know what to do!

PLEASE PLEASE PLEASE HELP!!!

---

### Post by markyboy1980 on 2008-08-09
I should just add that when the prompt comes up, it just waits indefinitely until I write anything... But what???

---

### Post by adewale on 2008-08-09
Enter sudo /etc/init.d/gdm start

---

### Post by cyberdork33 on 2008-08-10
That is the commandline! IDK why the GUI is not starting automatically, but the results of the command posted in the last post will help get more info.

---

