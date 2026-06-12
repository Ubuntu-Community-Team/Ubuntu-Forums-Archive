---
title: "Gnucash Report Crash"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by gdgardnerw on 2006-10-16
I have been running gnucash 1.8.12 for quite a few months and have been quite pleased with it...until of late.

The <Report><Custom> function on the menu as well as the Report Button on the button bar causes the whole program to crash. It used to work a few weeks ago and I haven't the slightest idea of what I did to make it do this.

I finally did jerry-rig the report I wanted: the cash flow for september. I thought I would save the report, since it was what I wanted. Now, not only is the report I saved no where to be found (fortunately I had the smarts to print it off before I saved it) but now I get no reports (text reports) at all! Only pie charts show up on the report menus!:confused: 

I tried reinstalling gnucash and it did not solve the problem! Can anyone help me? Without the report function for cash flow, this program is becoming gradually useless to me and I really like using it.

---

### Post by Marc Higgins on 2006-10-17
Sorry but I can not help yet :confused: ,  but I guess we are suffering from the same problem, when we try to print a certain invoice & the whole program crashes.

This is what is happening;

Backtrace:
In /usr/share/gnucash/scm/report.scm:
       ...
 167: 83259  (let ((options #)) (gnc:register-option options stylesheet) ...)
 167: 83260* [options-gen]
In /home/marc/.gnucash/saved-reports-1.8:
   5: 83261  (let ((options #)) (let (#) (# option)) options)
   5: 83262* [gnc:report-template-new-options/name "Printable Invoice"]
In /usr/share/gnucash/scm/report.scm:
 127: 83263  (let ((templ #)) (if templ (gnc:report-template-new-options templ) #f))
In unknown file:
       ...
   ?: 83264  [gnc:report-template-new-options #]
In /usr/share/gnucash/scm/report.scm:
 146: 83265  (let (# # #) (if # # #))
 153: 83266* [gnc:make-multichoice-option "General" "Stylesheet" ... ...
 157: 83267* [map #<procedure #f (ss)> ...
 164: 83268* [gnc:get-html-style-sheets]
In /usr/share/gnucash/scm/html-style-sheet.scm:
 271: 83269  (let ((ss #)) (hash-for-each (lambda # #) *gnc:_style-sheets_*) ...)
 274: 83270  [sort (# #) #<procedure #f (a b)>]
In unknown file:
   ?: 83271* [#<procedure #f #> # #]
In /usr/share/gnucash/scm/html-style-sheet.scm:
 276: 83272* [string<? ...
 276: 83273* [gnc:html-style-sheet-name #]
In unknown file:
   ?: 83274  (and (eq? (quote #) (record-type-descriptor obj)) (struct-ref obj 0))
   ?: 83275* [eq? #<record-type <html-style-sheet>> ...
   ?: 83276* [record-type-descriptor #]
   ?: 83277  (if (struct? obj) (struct-vtable obj) (error (quote not-a-record) obj))
   ?: 83278* (struct? obj)

<unnamed port>: In expression (struct? obj):
<unnamed port>: Stack overflow

---

### Post by gdgardnerw on 2006-10-18
Thanks for the details...even though I'm not sure I understand them. I'm not the sharpest tool in the shed when it comes to Linux.

I'm tempted to uninstall the program and reinstall it. But I am afraid of losing my financial information, so I am going to mull this option over before doing it.

I do notice, however, that there is a newer version of gnucash and I have seen some comments on how do install it on ubuntu. That's the good news. The bad news is (1) I'm not sure it will correct this problem and (2) I don't really understand the installation procedures to begin with!

---

### Post by gdgardnerw on 2006-10-18
Thanks for the details...even though I'm not sure I understand them. I'm not the sharpest tool in the shed when it comes to Linux.

My problem lies with even seeing the report on the screen! I can't even get to the printing part!

I'm tempted to uninstall the program and reinstall it. But I am afraid of losing my financial information, so I am going to mull this option over before doing it.

I do notice, however, that there is a newer version of gnucash and I have seen some comments on how do install it on ubuntu. That's the good news. The bad news is (1) I'm not sure it will correct this problem and (2) I don't really understand the installation procedures to begin with!

---

### Post by localuser on 2006-10-18
This is a reported bug that has to do with a duplicate report name in a report configuration file.

[http://bugzilla.gnome.org/show_bug.cgi?id=168250](http://bugzilla.gnome.org/show_bug.cgi?id=168250)

Here's the fix...

In your home directory there is a hidden file named ~/.gnucash/saved-reports-1.8

When you edit that file you will find an entry that looks like this:

(gnc:define-report 
  'version 1
  'name "Transaction Report"
  'options-generator options-gen
  'menu-path (list gnc:menuname-custom)
  'renderer (gnc:report-template-renderer/name "Transaction Report")))


In my file it was somewhere in the middle so you'll have to look carefully or you may miss it.  Change the name field of this entry...

(gnc:define-report 
  'version 1
  'name "Transaction Report NEW"   <==== changed field
  'options-generator options-gen
  'menu-path (list gnc:menuname-custom)
  'renderer (gnc:report-template-renderer/name "Transaction Report")))

restart gnucash and all your custom reports should work.

Give it a try and see if it helps.

~lu

---

### Post by gdgardnerw on 2006-10-18
Thank you VERY MUCH for your help! This solved the problem! I REALLY appreciate your guidance!

---

