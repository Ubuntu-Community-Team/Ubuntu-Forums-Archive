---
title: "[SOLVED] openoffice question"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by dondad on 2007-09-08
Does anyone know if there is a way to get the openoffice spreadsheet to save as a tsv (tab separated variable) text file rather than csv? I have a spreadsheet that I use to track links on a website and the conversion script on the server requires input as a tab separated text file. I do not see any option to do that with openoffice. Right now, this is about the only thing that I use Excel for and would like to be able to use the openoffice version instead. I don't have the option of modifying the script.

---

### Post by Chris S. on 2007-09-08
I tried this.  I put some random data in a spreadsheet.  Save As.  Picked .csv, edit filter options,  and gave it a name.  Clicked "save" or "ok", basically affirmative to any boxes coming up.

Eventually something appeared saying "Export of text files" with the options "character set", "field delimeter", "text delimeter".  I left character set as is, changed field delimeter to tab, and erased the text delimeter.  Saved and got a "tsv" format.  Try it out and experiment.

Otherwise, you could always save as .csv and write a script that searches the csv file via regex, replacing all commas with tabs.  I don't know the proper way to do it, but I know it would be very simple ... maybe not as simple as the above though, but alternatives are nice to have.

---

### Post by dondad on 2007-09-08
> **Chris S. said:**
> I tried this.  I put some random data in a spreadsheet.  Save As.  Picked .csv, edit filter options,  and gave it a name.  Clicked "save" or "ok", basically affirmative to any boxes coming up.

Eventually something appeared saying "Export of text files" with the options "character set", "field delimeter", "text delimeter".  I left character set as is, changed field delimeter to tab, and erased the text delimeter.  Saved and got a "tsv" format.  Try it out and experiment.

Otherwise, you could always save as .csv and write a script that searches the csv file via regex, replacing all commas with tabs.  I don't know the proper way to do it, but I know it would be very simple ... maybe not as simple as the above though, but alternatives are nice to have.

Thanks, I will try that. I thought about the global replace of commas, but some of the data has commas in it, so that would be a bit tricky as there are several thousand lines in the file.

---

### Post by dondad on 2007-09-08
That fixed it, thanks. I did not notice the filter box.

---

