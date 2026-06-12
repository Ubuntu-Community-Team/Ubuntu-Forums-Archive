---
title: "Deleting Gedit back-up files - poor grammar saved the day"
date: 2010-06-11
forum: Apple Hardware Users
---

### Post by eMacDude on 2010-06-11
I had some poorly named files from some time ago that I wanted to delete.  The files were simple C programs that I was playing with while trying to learn basic programming.  Unfortunately I saved the files using names with spaces between words and one that was wrapped in quotation marks.  Yes, I really did.  For example:

[B][FONT=Courier New]File Name

"File Name"[/FONT][/B] 

Besides not realizing that this was poor form I didn't realize that Gedit was by default making back-up files.  As a result I ended up with:

[B][FONT=Courier New] File Name~

"File Name"~[/FONT][/B] 

Tried using the command line to remove the files but this didn't work. For example:

[B][FONT=Courier New] rm File Name~

rm "File Name"~[/FONT][/B] 

Result:

[FONT=Courier New]** rm: cannot remove `File Name': No such file or directory**
[/FONT] 
The solution?  I found the solution for the first one in the Ubuntu forums.  As suggested, I wrapped the file name in quotation marks:

**[FONT=Courier New] rm "File Name~"[/FONT]**

This did not work in the second example since it already had quotation marks.  After a lot of shots in the dark and some head scratching I recalled an old grammar lesson albeit incorrectly.  When quoting a quote within a quote you place double quotation marks around single quotations - which is correct.  I remembered this lesson the opposite way and placed single quotation marks around the double quotation marks:

**[FONT=Courier New] rm '"File Name"~'[/FONT]**

That solved it!  Poor grammar saved the day.  With this in mind I'm thinking of using bad math for my next income tax return and see if it's as successful.

---

