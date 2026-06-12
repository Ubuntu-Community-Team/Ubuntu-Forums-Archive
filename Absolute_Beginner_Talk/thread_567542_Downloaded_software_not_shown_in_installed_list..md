---
title: "Downloaded software not shown in installed list."
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by Rana1974 on 2007-10-04
Hi,
I am using Ubuntu Feisty. I downloaded some packages including mono and none of them are shown on the installed software list. Also if I use the terminal I am able to run python and mono but again there is no icon for these in the applications menu. If I try to use launch program I am not able to find these using the browse option. Is there a command similar to lshw that can show the list of softwares installed. may be I am not typing the correct spelling in the terminal. 
Thanks,
Rana

---

### Post by llamakc on 2007-10-04
What did you download? deb files or tar.gz files? If you installed debs you can see what files were installed by typing in a terminal:

dpkg -L nameofpackage

---

