---
title: "PhpMyAdmin to Excel Spreadsheet"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by paulizaz on 2007-04-02
Hi,

I need to import/export data from SQL database usually managed by PhpMyAdmin to an Excel Spreadsheet.

Any advice on how to do this? 
Can I import/export the data to a particular layout on the spreadsheet?
Can I automate this process so it does it itself every month? - I heard a driver can do this?

Lost and confused but appreciate any help....

---

### Post by indytim on 2007-04-02
I'll address the basic export to Excel question.

Within phpMyAdmin, select the database and then the table you want to export.
At the top of the tabbed page (it varies by version of phpMYAdmin you're running), select the "Export" tab.

Once you're at the export screen, usually off to the left, make sure you have selected the CSV for MS Excel data.

Modify the conditions of the parameters on the right (ie structure, data etc).

During the export, you should get prompted for where to plunk your exported csv file in.

After the export has been completed, open MS Excel and do the file open from the Excel file menu.  Browse to where you plunked your file and select it.  Your export should now load into Excel.

IndyTim

---

