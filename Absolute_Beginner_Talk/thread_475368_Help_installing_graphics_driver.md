---
title: "Help installing graphics driver"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by czhou on 2007-06-16
Hi all,

I'm trying to install the driver for my intel graphics accelerator. I found the driver on intel's website, and I've downloaded the driver. The file format is .tar.gz, and I'm running 6.10 Edgy. what commands do I use to install this driver?

thanks in advance.

---

### Post by Brightbelt on 2007-06-16
I'm not as familiar with Edgy since I'm on Feisty, but...I would try this: Find a way to extract your tar.gz file onto your desktop (in Feisty, it's right-click and choose 'Extract Here'). 

Then double click the extracted driver folder to open it. Look for a 'Readme' file or an 'Install' file. Many times, there are installation instructions there. 

Btw, when I asked a similar question once and I got this response about checking out the 'Readme' or 'Install' files,  I hated getting this answer because it seemed like the person wasn't helping me. But actually through experience, I've come to really appreciate the advice, since I have found installation instructions many times this way. 

Oftentimes with a tar.gz file, it's this series of commands, but I can't guarantee it without seeing the files:

```

./configure
sudo make
sudo make install

```

I hope this helps,...Frank B.

---

