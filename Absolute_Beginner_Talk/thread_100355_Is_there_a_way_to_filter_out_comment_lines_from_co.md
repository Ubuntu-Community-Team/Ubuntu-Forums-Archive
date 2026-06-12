---
title: "Is there a way to filter out comment lines from configuration files ..."
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by Akhran on 2005-12-07
... and redirect the filtered output into another file? So, basically what is saved in the new file is only the configuration lines without all the comment lines (ie. lines starting with #).

Thanks !

---

### Post by ChrisTheGeek on 2005-12-07
Hi Akhran,

There certainly is.  If the file you wanted to copy without comments was /home/akhran/input.txt then the following command will strip the comments out for you and save a file in the same location called output.txt:

cat /home/akhran/input.txt | grep -v "#" > /home/akhran/output.txt

Hope this helps,
Chris

---

