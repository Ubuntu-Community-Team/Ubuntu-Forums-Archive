---
title: "&quot;Open with&quot; does not work on FTP"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by larsdk on 2008-03-14
Hi there,

I use bluefish to develop webpages. However there seems to be a difference between filetypes locally and on a FTP (using FTP through "connect to server") since doubleclicking on a ASP-file on the server does not make the file appear in bluefish (as it does if I open an ASP-file on my desktop). Any suggestions?

Lars

---

### Post by glennric on 2008-03-14
What ftp program are you using?

---

### Post by larsdk on 2008-03-14
as I wrote I don't use a FTP program. I use the "connect to server" and mount the folder on my desktop... :)

---

### Post by glennric on 2008-03-14
So you are using nautilus then.  You are always using some program to access ftp sites. 
There are differences on how nautilus treats files that are local or remote.  One thing that might be causing the issue is password authentication.  I have had issues with certain files not being able to open with certain applications because of some password request.
When you double click on the asp file what application does it open in?

---

### Post by glennric on 2008-03-14
Just to clarify what I mean, here are some examples.

On my system text files open by default in gvim.  If I have an ftp site open in nautilus and double click on it, then it works as expected (albeit a bit slower).
The default for ods files is openoffice calc.  When I double click on these files on an ftp site, all I get is a dialog saying "general input/output error".
The default for pdf files is evince.  If I double click on those in an ftp site I get a dialog to enter my password and then the file opens as expected.  
So different applications have different ways of dealing with authentication.  gvim and evince at least have ways of dealing with it.  Open office doesn't, hence the error.  

It is possible that bluefish just balks entirely at the attempt.  I don't know.

---

