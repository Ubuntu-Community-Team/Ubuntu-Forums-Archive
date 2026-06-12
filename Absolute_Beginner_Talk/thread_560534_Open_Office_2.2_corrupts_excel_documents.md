---
title: "Open Office 2.2 corrupts excel documents"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by biomedtech on 2007-09-26
Not sure why, but Open Office will open Excel files which were created in Windows, but cannot save the file back as Excel 97/2000/xp without the following warning. 

"This document may contain formatting or content that cannot be saved in Microsoft Excel 97/2000/xp file format. Do you want to save the doc in this format anyway?

- click 'yes' to save in MS Excel 87/2000/xp file format
- click 'no' to use the latest Open Document file format and be sure all formatting
and content is saved correctly. "

Why wouldn't OO be able to save an Excel file in .xls that was opened from an .xls to begin with?

Even if I save a Windows Excel file just opened, without changing a thing, Open Office will show this warning.  Clicking Yes creates a blank document which cannot be recovered. 

My employer emails labor requests to me, via XP version of Excel.  Since adopting Feisty as my main Internet OS, I hoped I could return Excel invoices back to my employer using Open Office. 

Please help.

---

### Post by bigken on 2007-09-26
just select 
- click 'yes' to save in MS Excel 87/2000/xp file format

I have used open office to repair corupted excel files for clients with great sucsess

---

### Post by Delkster on 2007-09-26
I don't actually know how OpenOffice.org internally works, but let me give an educated guess:

If you open an Excel sheet in OpenOffice.org, it is imported (converted) to the internal run-time representation that OpenOffice.org has for spreadsheets. When you re-save the file, OpenOffice.org saves the file using its own routines based on the understanding the developers have about the Excel document. It also re-encodes all formatting and other such data.

Hence, the file may differ from the original, although it should still be compatible with Excel. However, if there's for example any special formatting in the original file that OpenOffice.org does not support for Excel documents, that formatting is lost because OO.org encodes the file on its own and thus the formatting that will end up in the resulting file depends on the ability of OO.org to encode Excel files, not only on what was in the original file, even if you don't make any modifications.

Note that the warning doesn't necessarily mean that any formatting will be lost, and definitely it does not automatically mean that any severe corruption would take place. The file may end up displaying in Excel exactly the way it was before. However, since the Excel format (particularly the traditional one) is both proprietary (no public documentation available) and pretty complex (meaning that figuring it out without documentation is even more difficult), the support is not perfect and not all formatting may be retained. You probably want to save a copy first and check that the results are what you want before overwriting anything critical.


Edit: Let me add that i've modified Excel files using OpenOffice.org both at work and at home, and the result has been pretty good. Not even any formatting has been lost, at least as far as I've been able to observe.

---

### Post by biomedtech on 2007-09-26
Every .xls file I've opened in OO displays properly. I have not seen any special formatting that was out of place. It's when I want to save them (as .xls), that each files has been corrupted. no exceptions.

So then I went to one of the forum FAQs, and learned about Gnumeric Speadsheet. It has no problems with the same files, opening or saving as Windows version. Gnumeric didn't complain about special formatting. It just opened the file, allowed me to make changes, then saved it back as 97/2000/xp file

At this point, I have to give Open Office a big rasberry, while Gnumeric receives a standing ovation. 

Can Open Office be re-installed over the top of a previous copy, or does it need to be completely removed first?  Thank You.

---

### Post by bigken on 2007-09-26
you can use add/remove to remove and re-install

---

### Post by Linux_Man on 2007-09-26
No for OOo you need to use synaptic to remove it. Because I tried removing it before. Not sure if the command line works or not.

---

### Post by Delkster on 2007-10-01
> **biomedtech said:**
> Every .xls file I've opened in OO displays properly. I have not seen any special formatting that was out of place. It's when I want to save them (as .xls), that each files has been corrupted. no exceptions.

Did they indeed get corrupted, or did you just get the warning? OpenOffice.org gives the warning pretty much every time you save something in a format that is foreign to OO.org, and that doesn't mean the file actually is going to get corrupted or even lose anything.

If you have evidence that the files have actually been corrupted, that's another story, but the warning is pretty much routine in OO.org and doesn't mean anything by itself.

---

### Post by ugm6hr on 2007-10-01
> **biomedtech said:**
> Every .xls file I've opened in OO displays properly. I have not seen any special formatting that was out of place. It's when I want to save them (as .xls), that each files has been corrupted. no exceptions.

So then I went to one of the forum FAQs, and learned about Gnumeric Speadsheet. It has no problems with the same files, opening or saving as Windows version. Gnumeric didn't complain about special formatting. It just opened the file, allowed me to make changes, then saved it back as 97/2000/xp file

At this point, I have to give Open Office a big rasberry, while Gnumeric receives a standing ovation. 


That's bizarre, cos my experience is exactly the opposite! 

As a Xubuntu (and former PuppyLinux) user, I think Gnumeric is great.  It opens 10 times faster than OO.org, and I don't need the complex formula stuff of Excell/OO.org most of the time.  However, Gnumeric always made Excel files smaller (in kb) than Excel or OO.org, and the saved files opened just fine in Gnumeric *and OO.org*, but Excel never recognised them as Excel files.

So now I have to use OO.org (and it's slow pace) to ensure that my Excel rota uploads to my PDA properly (Windows Mobile 5).

I would love to return to Gnumeric if it worked for me.......

---

### Post by EmoDx on 2008-02-29
> **biomedtech said:**
> Not sure why, but Open Office will open Excel files which were created in Windows, but cannot save the file back as Excel 97/2000/xp without the following warning. 

"This document may contain formatting or content that cannot be saved in Microsoft Excel 97/2000/xp file format. Do you want to save the doc in this format anyway?

- click 'yes' to save in MS Excel 87/2000/xp file format
- click 'no' to use the latest Open Document file format and be sure all formatting
and content is saved correctly. "

Why wouldn't OO be able to save an Excel file in .xls that was opened from an .xls to begin with?

Even if I save a Windows Excel file just opened, without changing a thing, Open Office will show this warning.  Clicking Yes creates a blank document which cannot be recovered. 

My employer emails labor requests to me, via XP version of Excel.  Since adopting Feisty as my main Internet OS, I hoped I could return Excel invoices back to my employer using Open Office. 

Please help.

I have had decent success going to and from Excel spreadsheets in Oo. But I have only had to use it for very basic spread sheets. No more that a hundred line items with 4-5 sortable columns. No formatting except colors and fonts. I did import one checkbook style register w/o any dificulties. But there was only one equation. IT wasnt a true spreed sheet with multiple equations/dependencies.

If there was ever a problem with Excel opening your sent .xls, your employer could open it in Oo. It is free to install on a XP machine.

Emo

---

### Post by RJ Hythloday on 2008-02-29
I've had no problem opening any m$ file in ooo but I was sent a .doc, edited it, saved it as a 98/2000/xp .doc and sent it back. They couldn't open it. Does any one know why.

---

