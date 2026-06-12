---
title: "how do i update ubuntu?"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Andrew79 on 2008-03-27
i want to know is there some sort of update for ubuntu? I dont seem to be able to find thunderbird in my apps ad remove or any of these places that people sugeest, and think maybe my copy I had was out of date????

---

### Post by StOoZ on 2008-03-27
type in terminal:
> sudo apt-get  update
> sudo apt-get  upgrade

---

### Post by codeslicer on 2008-03-27
What do you mean update? If you want to check for new versions, use the Update Manager in System->Administration->Update Manager.

If you want to update to Ubuntu 8.04 Hardy Heron Beta, press Alt+F2 and type in "update-manager --devel-release"

---

### Post by plucky on 2008-03-27
@Andrew79,

Make sure you have all the repositories selected.In **System > Administration > Software Sources** make sure the first four boxes are ticked and under **Updates** tag, make sure top two tags are ticked (see attachments).Also disable the CDROM as a source if it is selected.

Then do the commands **StOoZ** said.

You should then be able to find Thunderbird in the Repositories if you select all available applications.


Good Luck

---

