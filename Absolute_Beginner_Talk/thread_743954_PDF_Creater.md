---
title: "PDF Creater"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by miykle on 2008-04-03
G'Day   Firstly I have a duel boot system, 2 X HD's , one with windows XP the other with Ubutu, because of the interface between the two systems I can access the files on windows when running Ubutu, BUT, the windows files are .txt, what I'm looking for is a program for Ubutu which will convert .txt to PDF, is there such a thing for Ubutu.
 The other thing is when I download a program instead of installing, the archive manager opens and then I don't know what to do, can anyone help please.
  Do I need a firewall or not, some say yes some no, need a definite if possible.
many blessings Miykle

---

### Post by TeoBigusGeekus on 2008-04-03
1) Open .txt files with Openoffice and print them as pdf.
2)If the extracted file is a .deb file, then double click it and it will be automatically installed. Otherwise, we need additional information about the extracted files. Also, try to install software from Add/Remove programs or from Synaptic Package Manager.
3)You allready have a firewall: iptables. The question is, do you need a gui to alter its settings or not?
The most popular gui for configuring the Ubuntu firewall is Firestarter, I believe you can find it in the Add/Remove programs. If you use bittorrent for example you might wanna open some ports, etc. Firestarter is the thing for you...

---

### Post by miykle on 2008-04-03
Strewth that was quick, Thanks for the reply.
 I'll have to have a play with Open Office and see how I go, 
 The fire wall, being already installed, will be fine for now.
  As to the downloads, it was a .tar.gz file (??) click on open in the downloader and the archive manager opens, then I'm stumped .
Blessings Miykle

---

### Post by hyper_ch on 2008-04-03
don't install firestarter... it's more trouble than help...

---

### Post by TeoBigusGeekus on 2008-04-03
A .tar.gz file is a compressed archive, something like .zip or .rar files. When you open it with archive manager, you need to extract its content somewhere, your Desktop for example. Post us the contents of the archive - we might be able to help you.

---

### Post by Delkster on 2008-04-03
> **miykle said:**
> what I'm looking for is a program for Ubutu which will convert .txt to PDF, is there such a thing for Ubutu.
Ubuntu has a pseudo-printer that can be used to "print" any file into a PDF. That also works with the Text Editor for .txt files.

When you have a file open, try going to "File > Print" and see if you have PDF listed as a printer. If there's one, just select it as the printer and "print" to it, and the file will appear in a folder called "PDF" within your home folder.

If you don't have PDF as an option in the print dialog, you need to install the cups-pdf package. I'm not sure if it's installed by default, but in case you don't have it, here's how you can install it:

1. Open **System > Administration > Synaptic Package Manager**.
2. Use the search to find "**cups-pdf**" and select it for installation by double-clicking on it.
3. Apply the change by clicking on "**Apply**". After the file has been downloaded and installed, you should be done and there should be a PDF option in the print dialog.

---

### Post by njparton on 2008-04-03
+1 re Firestarter!!

---

### Post by Delkster on 2008-04-03
> **miykle said:**
> The other thing is when I download a program instead of installing, the archive manager opens and then I don't know what to do, can anyone help please.

Which program are you trying to install and from where?

---

### Post by miykle on 2008-04-03
I can't believe how quick off the mark you guys are, marvellous!!! 
 
 QUOTE :
" Ubuntu has a pseudo-printer that can be used to "print" any file into a PDF. That also works with the Text Editor for .txt files.

When you have a file open, try going to "File > Print" and see if you have PDF listed as a printer. If there's one, just select it as the printer and "print" to it, and the file will appear in a folder called "PDF" within your home folder."
  
 I tried that and "what do ya know" it worked !!!  funny that !! 

 The further I go with Linux the more I like it,it's much more flexible than windows, faster to 
 
 One more question if I might, when I want a certain program, do I do like windows and go looking for it or do I enter a description of what I want into synoptic or terminal and have the program find it for me.
Blessings Miykle

---

### Post by TeoBigusGeekus on 2008-04-03
> **miykle said:**
>  
 QUOTE :
 One more question if I might, when I want a certain program, do I do like windows and go looking for it or do I enter a description of what I want into synoptic or terminal and have the program find it for me.


You should first go to Add/Remove applications and Synaptic to find a program that is supported by the Ubuntu community. If you don't find what you are looking for, you can then just Google. 
But be cautious with third party software...

---

### Post by mali2297 on 2008-04-03
> **miykle said:**
> 
 One more question if I might, when I want a certain program, do I do like windows and go looking for it or do I enter a description of what I want into synoptic or terminal and have the program find it for me.


The official repositories should be the first place to look. That is, use Synaptic.

More info on installing software:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by miykle on 2008-04-03
Well ; Thanks so much for all your help guys, it's good to know there is help here when needed, especially for the uninitiated, the more I learn the more i like this OS, 

  One last question, there's always one more, is there a program similar to "iso burn" which I have in windows ??
Many Blessings Miykle      :popcorn:

---

### Post by Delkster on 2008-04-03
> **miykle said:**
> One last question, there's always one more, is there a program similar to "iso burn" which I have in windows ??

I don't know exactly what that software does, but if it's used for burning ISO images on CDs or DVDs, in Ubuntu you can do that by right-clicking on the ISO file and selecting "Burn to CD/DVD" or so, right in the file manager.

---

### Post by mali2297 on 2008-04-03
> **miykle said:**
> 
  One last question, there's always one more, is there a program similar to "iso burn" which I have in windows ??


I'm not an experienced Windows user. Please describe the features of this program.

---

