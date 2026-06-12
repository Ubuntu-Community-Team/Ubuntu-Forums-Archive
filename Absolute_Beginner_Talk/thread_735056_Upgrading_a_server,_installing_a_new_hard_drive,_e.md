---
title: "Upgrading a server, installing a new hard drive, etc"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by Los Frijoles on 2008-03-25
I currently have 6.06 LTS installed on my server, but I am finding that various applications such as torrent clients are no longer usable on my system. I would like to upgrade to the most recent version (8 I think?), but also be able to keep my files. I have it in my head that in order to upgrade, the hard drive must be formatted. Since I have two drives, I have the hard drive organized so that the OS data is on hard drive 1 and the server content is on hard drive 2 (just the HTTP content, not any of the servers (apache, postfix, etc). How can I go about doing this easily? It took over 48 hours to get the server to work properly on Ubuntu. And being a beginner with Linux, I pretty much require the GUI so getting the server edition is not much of an option.

About hard drives: I have dual SCSI hard drives in my server, but they are very very small (10Gb each). There is something that appears to be a SCSI expansion port on the back of the server box, but I am not sure how to connect additional hard drives to it. I know that these hard drives can be purchased cheaply off ebay, so I think I could add a few. Or, would it be easier to find a small mybook and plug that in and use that as the server drive if that is possible (mounting external USB hard drives)?

---

### Post by mwcrowley on 2008-03-25
The next upgrade is Hardy and is a Long Term Support release that is due out 24 April.  You should think about waiting until then because you will be able to upgrade from your current version to  Hardy Heron (the new one).  
In case you were thinking about trying the beta version, I would suggest against that if you need GUIs to configure.

You will not need to format your hard drive to update.

---

