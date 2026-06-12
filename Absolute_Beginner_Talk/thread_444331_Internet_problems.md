---
title: "Internet problems"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Johnny p on 2007-05-15
:mad: I decided to try out Ubuntu on my old Dell and I like what I see so far, the only problem I have is the network card is not built into the motherboard and I don’t think Ubuntu is recognizing it. I’m such a noob to this OS so any help would be appreciated. Thanks.

---

### Post by dstew on 2007-05-15
Open a terminal window and enter:```
sudo lspci
```Post the results to the forum.
What version of Ubuntu did you install? And what model is your Dell? Is your network card possibly a PCMCIA card (goes into the slot on the side?) If so, we  need to know the make and model.

---

### Post by prestonspcworx on 2007-05-15
i am also a noob, & had the same problem.  i switched pci slots w/ my NIC & it worked just fine.  probably a device conflict.  hope this helps!!

---

### Post by Johnny p on 2007-05-15
When entering that Code it said it could not find anything.

My dell Model is very old, Dell Dimension XPS T500

My card is 3Com -  Etherlink III 3C509B-TPO ( very old too, copyright 97 )

Card did work with windows, so card works fine as well as the pc in whole.

---

### Post by dstew on 2007-05-15
What version of Ubuntu did you install? Also, post the text of the terminal command **sudo lspci** and the output, even if it is an error message.

---

### Post by Johnny p on 2007-05-16
I have version Ubuntu 7.04 - Supported to 2008

Ill post the error message when I get home from class.

---

