---
title: "Seperate root and home folders"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by senrew on 2007-09-02
Ok. I have kubuntu 7.04 installed to a 160g drive. I want to install the OS fresh to a second 40g drive and keep the /home folders on the 160g since I have so much stuff in there.

I've figured out how to mount the 160g drive under /home from the install on the 40g, but I was wondering what other files from the current install do I need to transfer to the new one in order to make this a seamless swap?

I have apache setup with several vhosts. Pretty much everything else I have installed app wise I can easily reinstall again without worrying about losing everything. I'm just worried about the specific apache config files and the user/password info from the current install.

Not sure if I'm explaining my situation correctly here...

---

### Post by senrew on 2007-09-02
Thinking about this, I've found a way to rephrase the question.

My problem is that my home folders are currently using 80g of space, and I don't have another drive big enough to hold it all temporarily.

The question is this. Is there a way to copy everything from the drive minus the /home folder to the 40g (which fits with lots of space left over), then delete what was just copied from the 160g, and simply symlink or mount the 160 with just the /home contents remaining to /home on the now transplanted system on the 40g?

---

