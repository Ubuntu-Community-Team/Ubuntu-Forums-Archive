---
title: "file roller and 7zip encrypted files"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Kilarin on 2008-01-25
Hello!

File Roller opens 7zip archives for me just fine, UNLESS those 7zip archives were encrypted.  Then I get "an error occurred while opening the archive"

and clicking "Command Line Output" reveals: 
-------------------
7-Zip (A) 4.51 beta  Copyright (c) 1999-2007 Igor Pavlov  2007-07-25
p7zip Version 4.51 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)

Enter password (will not be echoed) :
Error: /media/disk/bkp3.7z is not supported archive

Errors: 1
-------------------

Of course, file roller never gave me a chance to enter the password.  7zip will decrypt these archives from the command line just fine, but it seems odd that File Roller crashes on it.

Does file roller not support encrypted 7zip archives?

Thank you for your help,

---

### Post by kplaxmaster on 2008-01-25
In File-Roller, you input the password by:
Opening the achieve in file-roller.  (Do **NOT** right click and just press "extract here."

Next, press "extract."  Select the location you wish to extract the files to.  Notice however, it now let's you give a password.  It will let you leave it blank, even if the files are decrypted but it will spit out an error.

Thus, put in the right password there, and *then* press extract.

It will now decrypt your files for you.  \\:D/

Notice that the GUI version of this is a little tricky.  This is why I like those CLI versions!

---

### Post by Kilarin on 2008-01-26
> In File-Roller, you input the password by:
Opening the achieve in file-roller. (Do NOT right click and just press "extract here."
Thats exactly how I opened the archive, double clicking the archive in Nautilus so that File Roller activates.

BUT, I figured out why we are getting different results.  The problem only occurs when you use the option to encrypt the header.   I wanted  the header encrypted so that even the names of the files would not be visible to an unauthorized user.  This seems just good sense to me since exposing the file names can sometimes give away important information.

If I encrypt the archive WITHOUT encrypting the header:
```
7z a -p"thepassword" /media/disk/bkp3/test-yeshdr.7z /media/tc1/temp/*.*
```

Then I can double click the archive and file roller will open up as usual, and I can click extract, enter the password, and it will extract.  It will attempt to extract even if I don't enter the password, which seems odd, but still, it works.

HOWEVER, if I encrypt the archive with the option turned on to also encrypt the header:
```
7z a -mhe=on -p"thepassword" /media/disk/bkp3/test-nohdr.7z /media/tc1/temp/*.*
```

Now I get the above mentioned error.  A double click on the archive results in "an error occurred while opening the archive", and displaying the Command Line Output reveals that 7zip asked for the password, but File Roller never asked the user to enter the password.  It just dies instead.

---

