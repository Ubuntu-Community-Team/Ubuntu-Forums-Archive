---
title: "Printing PDF files"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by richardward101 on 2006-08-29
I'm having trouble printing PDFs. I can print normal documents (gedit prints fine, test page prints fine), but when I try and print a PDF using document viewer, nothing happens. The icon appears for printing in the notification area, but thats it. If I click it, it says job stopped, and If I click resume, nothing changes. I've tried Document viewer, xpdf, kpdf, and get the same results!
The only thing that works is Adobe's viewer, but that won't print 4 pages to one side. I tried installing the lastest windows version under wine, but it said I needed internet explorer (version 5 works and prints but doesn't do 4 pages to one sheet).
Any help would be much appreciated
thanks.

---

### Post by whizbaby on 2006-08-29
What does /var/log/lp-errs and /var/log/lp-accts and 'lpq -Pprintername' say about your lost jobs? (sudo less /var/log/...)

Is your printer set as a default in CUPS ?
If you don't know it's probably not ...
Type:

sudo adduser YOURUSERNAME lpadmin <RETURN>
sudo adduser cups shadow    <RETURN>   (to allow cups to verify passwords)

then in your favourite browser type:

localhost:631               <RETURN>   (to get to the cups-frontend)

there you can verify all cups thinks about your printer and it's jobs.
Any of this helping/giving more insight?

---

### Post by richardward101 on 2006-08-29
Ok, the printer works in gedit and adobe and IS set as default. Didn't know about the web frontend to cups, quite interesting
I get the following problem with your instructions:
```
richard@AKIRA:~$ sudo adduser cups shadow
adduser: The user `cups' does not exist.
richard@AKIRA:~$ 
```
However, lloking at the error log, I only installed the printer a few hours ago, and the log is just full of the following line:
```
E [29/Aug/2006:13:55:39 +0100] cupsdAuthorize: Local authentication certificate not found!
```
And when I say full its there a few hundred (possibly thousand) times!

---

### Post by whizbaby on 2006-08-29
Ooooops, myfault@braindamage.

It's got to be 
sudo adduser cupsys shadow

(looked it up in my .bash_history)
I'm actually trying to remember the Ubuntu web page I got the information from...

---

### Post by whizbaby on 2006-08-29
Here it is

[https://help.ubuntu.com/community/HOWTO-enable-cups-browsing?highlight=%28cups%29](https://help.ubuntu.com/community/HOWTO-enable-cups-browsing?highlight=%28cups%29)

---

### Post by richardward101 on 2006-08-31
I've found a viewer, gpdf (which is apparently based on xpdf) which prints correctly. I have been unable to otherwise fix kpdf, etc. The however while gpdf prints properly, it doesn't display pdfs properly on the screen. V strange.

---

### Post by whizbaby on 2006-08-31
Only to get shure:
Is your printer the **default** printer in cups?
In xpdf, what do you see as **print command** in the window popping up when you click on print?

---

### Post by richardward101 on 2006-09-01
> **whizbaby said:**
> Only to get shure:
Is your printer the **default** printer in cups?
YES. It is the default printer and most things are printing fine with it.
> **whizbaby said:**
> 
In xpdf, what do you see as **print command** in the window popping up when you click on print?

lpr

BUT, I was mistaken before, xpdf actually prints fine, but it can't print four pages onto one sheet of a4, which is what I need. Gpdf can do that, and it doesn't render pages correctly, although it prints them fine.

---

### Post by whizbaby on 2006-09-01
Try putting the whole print command in applications you want to print from:

lpr -Pprinter 

(where **printer** has to be changed to the name of your printer, e.g. if it's john type **lpr -Pjohn**)
For example firefox usually has a bunch of variables and wildcards as printing command, which can lead to problems (e.g. wrong filter)

I don't know if this is very comfortable, but gimp can view/print pdf's, too ...

---

