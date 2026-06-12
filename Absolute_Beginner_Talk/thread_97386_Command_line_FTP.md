---
title: "Command line FTP"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by TheAnonymousx on 2005-11-30
Okay, so I know I can use any GUI based FTP client, but if I'm put into a situation in which that's not a viable option then I'm SOL. So my question is this...when using command line FTP, how do you show the progress of the file(s) you're pulling? I've got navigating down, but that I do not have down...also, is it just me or can I not get files with spaces in them?

---

### Post by cwaldbieser on 2005-11-30
[QUOTE=TheAnonymousx]Okay, so I know I can use any GUI based FTP client, but if I'm put into a situation in which that's not a viable option then I'm SOL. So my question is this...when using command line FTP, how do you show the progress of the file(s) you're pulling? I've got navigating down, but that I do not have down...also, is it just me or can I not get files with spaces in them?[/QUOTE]
If you use "wget", I believe that shows a progress indicator by default.  I think you can show a progress indicator with "curl" as well.  The vanilla ftp client doesn't show any kind of progress-- it is finished when you get the prompt back.  You could put it in the background and do a "watch ls -hl filename" when downloading.

---

### Post by harisund on 2005-11-30
If you are using just "ftp" I think there is something called hashing which can be enabled typing 

hash

at the ftp command prompt. Then on, any file transfer you do will be shown with a list of #'s .. 

Do check that and post back ! 
Thanks

---

### Post by TheAnonymousx on 2005-11-30
[QUOTE=harisund]If you are using just "ftp" I think there is something called hashing which can be enabled typing 

hash

at the ftp command prompt. Then on, any file transfer you do will be shown with a list of #'s .. 

Do check that and post back ! 
Thanks[/QUOTE]

Yeah same result. Basically it's ignoring the rest of the information after the white space. Hmm.

---

### Post by TheAnonymousx on 2005-11-30
ah some intuitiveness (or however it's spelled) did it
Simply use double quotes
cd "White Stripes"

:D

---

