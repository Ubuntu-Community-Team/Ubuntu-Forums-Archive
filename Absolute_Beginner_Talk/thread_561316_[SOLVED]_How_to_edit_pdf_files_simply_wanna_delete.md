---
title: "[SOLVED] How to edit pdf files? simply wanna delete a few pages"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by SabrinalovesUbun2 on 2007-09-27
I just need something simple, which lets me view the pdf documents, and I can choose to delete which ever pages I dont need (this was simple under windows) I dont know how to do it now :confused:

---

### Post by Niniel on 2007-09-27
No, it's not simple under Win, either, unless you have Acrobat the program, not just the reader. 

Anyway, Google is your friend:

[http://www.wikihow.com/Edit-PDF-Files-in-Linux-Using-PDFEdit]("http://www.wikihow.com/Edit-PDF-Files-in-Linux-Using-PDFEdit")

---

### Post by Beggar on 2007-09-27
Seriously, there is a huge post on the first page of the beginner forums. You have try really hard to not see it....

[http://ubuntuforums.org/showthread.php?t=543890](http://ubuntuforums.org/showthread.php?t=543890)

I know your new, but the best way to find an answer isn't always going to be ask, all your doing is spamming the forums with the same question over and over. Just search to see what other people have done in your situation. If you can't find your question asked somewhere else, then it is worth adding.

---

### Post by SabrinalovesUbun2 on 2007-09-27
> **Niniel said:**
> No, it's not simple under Win, either, unless you have Acrobat the program, not just the reader. 

Anyway, Google is your friend:

[http://www.wikihow.com/Edit-PDF-Files-in-Linux-Using-PDFEdit]("http://www.wikihow.com/Edit-PDF-Files-in-Linux-Using-PDFEdit")

Yes, Acrobat Pro + Windows = easy

ok anyway I'm downloading PDFedit [https://help.ubuntu.com/community/PDFedit](https://help.ubuntu.com/community/PDFedit)

It seems like a very large file

---

### Post by Dr Small on 2007-09-27
> **Beggar said:**
> Seriously, there is a huge post on the first page of the beginner forums. You have try really hard to not see it....

[http://ubuntuforums.org/showthread.php?t=543890](http://ubuntuforums.org/showthread.php?t=543890)

I know your new, but the best way to find an answer isn't always going to be ask, all your doing is spamming the forums with the same question over and over. Just search to see what other people have done in your situation. If you can't find your question asked somewhere else, then it is worth adding.
Hmm.
What begger says is wise, but if you can't find it, don't hesitate to post your question.

*Dr Small glances at begger.

---

### Post by Niniel on 2007-09-27
Somebody suggested to use OpenOffice since that can read and save PDF. If you have that already it might be worth a try.

---

### Post by Dr Small on 2007-09-27
OpenOffice can only create PDF documents from an ODT, or other format that OpenOfiice opens. It can not edit pdf's.
You're best bet, would be to stick with PDFedit, and see if it work.s (I have personally never tested it.)

Dr Small

---

### Post by SabrinalovesUbun2 on 2007-09-27
Installing PDFedit 0.3.1: Method 2

sudo apt-get update
sudo apt-get install alien
wget -c [http://downloads.sourceforge.net/pdfedit/pdfedit-0.3.1-1.i386.rpm](http://downloads.sourceforge.net/pdfedit/pdfedit-0.3.1-1.i386.rpm)
sudo alien -iv pdfedit-0.3.1-1.i386.rpm

[https://help.ubuntu.com/community/PDFedit](https://help.ubuntu.com/community/PDFedit)

---

### Post by Dr Small on 2007-09-27
Yes, I read that on the pdfedit page on the wiki...

---

### Post by SabrinalovesUbun2 on 2007-09-27
> **Beggar said:**
> Seriously, there is a huge post on the first page of the beginner forums. You have try really hard to not see it....

[http://ubuntuforums.org/showthread.php?t=543890](http://ubuntuforums.org/showthread.php?t=543890)

I know your new, but the best way to find an answer isn't always going to be ask, all your doing is spamming the forums with the same question over and over. Just search to see what other people have done in your situation. If you can't find your question asked somewhere else, then it is worth adding.

Sorry but I did, the threads I went through didn't provide a final answer, but the people were still unsure of which app to use, also I don't need any internal pdf editing, only wanna take some pages out here and there, anyways sorry for spamming, wasn't intended.

:(

---

### Post by Dr Small on 2007-09-27
As long as you are asking a resonable question, you most likely are not spamming.

---

### Post by SabrinalovesUbun2 on 2007-09-27
after installation, run =

$ pdfedit

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

### Post by Dr Small on 2007-09-27
Sounds like what virtualbox does to me, when I run it from the command line.
You can look around in your menus for PDFedit, or press ALT+F2 and type "pdfedit" in the run dialog box, and see if anything works that way.

Dr Small

---

### Post by stchman on 2007-09-27
> **SabrinalovesUbun2 said:**
> I just need something simple, which lets me view the pdf documents, and I can choose to delete which ever pages I dont need (this was simple under windows) I dont know how to do it now :confused:

Use cups-pdf.  Then do a print to PDF using Acrobat and specify a range like 1-20, 30-44.  Note that will delete pages 21-29.

---

### Post by SabrinalovesUbun2 on 2007-09-27
> **stchman said:**
> Use cups-pdf.  Then do a print to PDF using Acrobat and specify a range like 1-20, 30-44.  Note that will delete pages 21-29.

cups, ok now that gets me to my printer MFC-240C, ok I think I got the printer working, um would you know how to get the scanner working, XSane Image scanner installed.

---

