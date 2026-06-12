---
title: "[SOLVED] OpenOffice.org 2.2 instead of 2.3"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by t.septekin on 2008-02-15
I have just bought a second laptop and installed Gutsy on it, while my old one has the Feisty. I am not happy with the performance of OpenOffice.org 2.3: I do not appreciate it giving an error message and then opening a blank page when I attempt to close it and I do not like seeing a  horizontal red line across the sheet every other page or so. Is there any way I can install the version 2.2 from the Gutsy disk? I cannot find the application on the disc but whenever I've re-install ed the Gutsy in the old laptop, it installed the 2.2 which does not give the error message on closing.

---

### Post by LowSky on 2008-02-15
I dont have any errors opening or closing OOo.. Have you tried to reinstall openoffice from synaptic? It could also be Java, have you installed that as well?

---

### Post by bumanie on 2008-02-15
I am not sure how you would do what you wish. I think you could uninstall Ooo 2.3 from add/remove by deselecting the tick boxes or else purge Ooo 2.3 from your computer altogether. All that sounds rather radical, because even if you managed to do that, you would probably have to compile Ooo 2.2 from source. If you are mostly word processing, why not deselect 2.3 and enable abi word and see if that behaves any better for you.
Alternatively, wait, and someone else may have an answer as to how to fix 2.3.

---

### Post by t.septekin on 2008-02-15
Thanks for the idea: I have just re-installed it via Synaptic, still get the "Due to an unexpected error, OpenOffice.org crashed..." error in closing, It then starts with a blank page and I can close that with no further trouble. I mainly use the spreadsheet and that is where I experience the problem; the word processor side closes fine.

---

### Post by Yoke &amp; Chung on 2008-02-15
Strange indeed, have been using Gutsy and no problems on running OO. Maybe you can try uninstalling OO 2.3 first before install again?

---

### Post by t.septekin on 2008-02-15
> **Yoke & Chung said:**
> Strange indeed, have been using Gutsy and no problems on running OO. Maybe you can try uninstalling OO 2.3 first before install again?

I shall try; however I am not hopeful: a few days after Gutsy came out I had downloaded and run it on my old laptop when the OO problem appeared. I then reverted to Feisty. My new machine (Sony Vaio FZ21M) feels rather ticklish, I could not install Feisty on it (I could not install Windows XP, either; it has an Italian version of Vista which is not my cup of tea), I was happy to install Gutsy because of its better Wi-Fi and Bluetooth support. I guess I shall have to live with an inconvenient closing procedure.

Thanks to all who tried to help. My problem has not been solved but I have a warm feeling inside.

---

### Post by Hagar Delest on 2008-02-15
You can try to rename your OOo user profile folder (~/.openoffice.org). If no improvement, you can try to install the official version of OOo : [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by t.septekin on 2008-02-16
Thanks Hagar de l'Est, the official version has done it, after completely removing the old one. Now, to my next problem..

---

### Post by Hagar Delest on 2008-02-16
> **t.septekin said:**
> Now, to my next problem..
The red line thing on pages? Can you upload a screenshot?

---

### Post by The Cog on 2008-02-16
Those red lines have never been a feature of OOo. Iwonder if there's something odd saved in your local profile. Try renaming .openoffice.org2 to something else so OOo can't find it. It will then start up as though freshly installed. See if that fixes it.

---

### Post by Hagar Delest on 2008-02-16
It can be the manual page break tag.

---

### Post by t.septekin on 2008-02-24
Sorry for the delay in replying: I now have a graver problem in networking.

As for the red line across the row, it turned out that it was appearing to tell me one of the columns was too narrow to display the contents, increasing the column width eliminated the red line

Cheers..

---

