---
title: "isight after osx partition deleted?"
date: 2009-01-14
forum: Apple Hardware Users
---

### Post by Epamek on 2009-01-14
So I want to get my 4,1 macbook to single-boot 8.10.  It'll be my first time actually *using* Linux, as opposed to just knowing I have it on second partition.  I have all of my documents, etc backed up.
After I follow the documentation to get isight and other firmware (is there any other that requires using the macosx partition?) can I simply erase my Mac partition?  Or would it be better to keep it as on with like 5gb allocated to it?  Is there a way I can shrink the size of my mac partition and make Ubuntu the default OS without reinstalling OS X?

---

### Post by Rog-Mahal on 2009-01-14
I know for isight the necessary firmware components are placed in your linux partition, so you don't need anything from OS X for that. I would assume the same for other firmware, but you want another opinion on that, I have a Macbook 2,1. There are a variety of tools out there to shrink the size of your OS X install, and I believe you can use parted to resize your HFS+ partition, a quick google search reveals many threads. 

refit would probably be your best bet for dual booting, check the macbook community docs for a howto, you can even set linux as your primary OS. 

I run a dual boot using refit with a small OS X partition to take advantage of the extra wireless range and do software/firmware updates. It works wonderfully. I also singlebooted for about a year before switching back to two OSes. Both work well.

---

