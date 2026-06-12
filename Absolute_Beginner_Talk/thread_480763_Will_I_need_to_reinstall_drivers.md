---
title: "Will I need to reinstall drivers?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Dainn on 2007-06-21
Hello, 
I currently have ubuntu 6.06 with a seperate partion for /home on my computer.  I am interested in changing to xubuntu 7.04.  I am planning to just overwrite the current 6.06 install.   From what I understand, I should be able to do this because it would be a fresh install of xubuntu overwritting the old ubuntu, but keeping the /home folder becuase it's on a seperate partition.  If this is incorrect, please let me know.

Any way, back to my question.  I had to manually install the driver for my wifi card.  If I go ahead with this change, will I need to reinstall any drivers that I manually installed in the previous version?  I'm not sure where the driver(s) are kept in the file system.

Thanks in advance for any  help provided.

---

### Post by steve.horsley on 2007-06-21
I am pretty sure that you would have to go through the driver installation process again. Drivers don't go in users home directories, which is all that you would be keeping.

---

### Post by 5-HT on 2007-06-21
Yup, you will need to recompile the driver if the card is not supported in 7.04.
Best to do a recompile instead of just copying the module over to the new kernel (would have to save it first), but you could always give it a go.

---

### Post by Dainn on 2007-06-21
The answer is what I figured it would be, but I wanted to make sure.

Thanks for the quick replies.

---

