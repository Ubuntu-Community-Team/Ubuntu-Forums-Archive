---
title: "Mac Pro configuration"
date: 2008-06-30
forum: Apple Hardware Users
---

### Post by takeawaydave on 2008-06-30
Community....

Just wanted to get some feedback on an idea I'm having...

Currently I have a requirement to run multiple machines each of which is fairly resource hungry (hosting various databases, web and app servers). 

This is for my work - I also however need to upgrade my existing mac which I use for photo/video editing.

I'm thinking down the lines of a dual xeon quad core with a heap of RAM. 

I would like to triple boot (Panther, Windows (for games), Ubuntu)

This I know is possible.

Furthermore I would like to have Xen/Ubuntu setup for running multiple OS's:

1 x Redhat/Centos, 
1 x Windows
1 x Solaris10

Xen providing bare-metal virtualisation will provide me with as close as possible native performance of these machines .

Not having ever delved anywhere beyond VMWare WS I would like to get some an idea of feasilibity here and whether there are any known limitations  with the above proposed setup before spending my hard earned ££'s.

Any feedback greatly appreciated.

---

### Post by cyberdork33 on 2008-06-30
the xen setup will likely be tough because of the legacy partitioning limitations of the emulated MBR/BIOS. I don't think anyone has posted here that has attempted what you are proposing.

---

