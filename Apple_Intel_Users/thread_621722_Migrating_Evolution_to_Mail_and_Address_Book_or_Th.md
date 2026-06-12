---
title: "Migrating Evolution to Mail and Address Book or Thunderbird"
date: 2007-11-24
forum: Apple Intel Users
---

### Post by ridl on 2007-11-24
Hi all,

I just got a new iMac for home use. I still want to use my old $300 feisty laptop, but the iMac will become my primary box. While my fantasy would be to sync contacts between evolution and address book, I'm don't have my fingers crossed. 

I do feel that maybe there's a way to at least move contacts from evolution to address book? What about old messages from evolution to mail?

If the native mac programs won't do it, what about Thunderbird? Can I move all my evolution stuff into thunderbird and then use that info on mac thunderbird? Maybe then move from thunderbird to mac mail and address book?

Basically, how do I migrate from stupid evolution mail (which I won't miss, man... buh-bye!... I wish I'd just started with Thunderbird, but I thought I liked the built-in calendar...) to... um... anything else, hopefully the native mac programs?


Thanks in advance for the help,
-ridl

---

### Post by Grey Box on 2007-11-24
**Migrating Thunderbird Between OS's**

I have done this heaps of times. I don't know if it's the most elegant method of migrating Thunderbird but here goes..

When I moved from OS X to Ubuntu recently on my macbook it was not difficult (but still a bit of work) to move the Thunderbird accounts over to Ubuntu from OS X. I did the following:

1. First I installed Thunderbird and set up a dummy account in Ubuntu.

2. I had to open Nautilus (or equivalent file manager) as sudo (I used gnome-commander which is a bit like Norton Commader), then find my way to the OS X machine.. to the Users folder.. to my old account, and then the 'Library' folder, making sure I display 'hidden files' under View, find the .mozilla-thunderbird or .thunderbird folder. I also did the same thing in another window, finding my way to my home folder and into the .mozilla-thunderbird folder.

3. Inside there is a folder with a random name, eg: g3bisvsd.default,  and a profiles.ini file. I go inside the g3bisvd.default folder, and copy everything in that folder (on the OS X partition) over to the equivalent randomly named folder on my Ubuntu partition, replacing everything.

4. Then I change the ownership of everything in my Ubuntu .mozilla-thunderbird folder to my local user (otherwise, if you don't, the copied stuff will still have your OS X user's ownership details and your Thunderbird won't be able to open it). Make sure it's done recursively, so you don't miss anything.

Next time you open Thunderbird you'll find all your familiar, old settings and everything should just work without any further changes. No need to enter new passwords or change anything.

This is basically the way I recover my thunderbird mail from a backup, too.

---

### Post by ridl on 2007-11-25
Thanks for your reply. I'm trying to go the other way, though, from Ubuntu (Evolution) to Mac, so I don't know how helpful your tip will be. Have you ever gone from Ubuntu to Mac?

---

