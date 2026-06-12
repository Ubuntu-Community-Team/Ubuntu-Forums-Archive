---
title: "OpenOffice Recovery"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by in_flu_ence on 2007-02-09
Hi,

   My openoffice crashed once when i was loading a temporary word document. From then on, it starts to recover the file. Nevertheless, the recovery process fails because the document is no longer there (temporary).

   I have this recovery process ongoing everytime i start my Openoffice from then. How can I remove the recovery of that file and move on?

Thanks

---

### Post by lhtown on 2007-02-09
I had that happen once. You should be able to delete or rename the open office folder that stores your user information.

You can go to your home directory and click on view hidden files and then find the file .openoffice.org2 and either delete it or rename it(safer). 

If you are concerned about loosing your preferences for open office, you could look for the particular file in the above folder that holds the recovery process preferences.

---

### Post by in_flu_ence on 2007-02-09
Thanks and I think i have gotten it fixed

The recovery file is located as follows for those who have the same issue.
/home/username/.openoffice.org2/user/registry/data/org/openoffice/Office/Recovery.xcu

I have renamed it to recovery1.xcu but i suppose deleting it will be fine since OOo will recreate the file after exit.

---

