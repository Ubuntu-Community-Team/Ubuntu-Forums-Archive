---
title: "Adobe reader fails to open password protected pdf in ubuntu"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by Murkhanand on 2007-09-27
[SIZE="6"][SIZE="6"]Hi Everyone,

Greetings

I have successfully installed adobe reader 7.0 in UBUNTU as well plugin in Firefox. I have received a pdf file which is password protected. Adobe Reader in Ubuntu opens normal pdf file happily so does the Firefox. However, Adobe Reader fails to open the password protected file and I receive the following  message meaning that there is no internet connect.  There is internet connection and Firefox can browse happily including visiting the site [http://www.adobe](http://www.adobe) .com itself. 

Has anyone come this problem and how to solve it?.

Thanks

Murkhanand

---

### Post by mcduck on 2007-09-27
Have you tried if the file opens in Ubuntu's own PDF viewer, Evince?

If not, you could just remove the password protection from the file. It can be done with 2 simple command-line tools, pdf2ps (that converts the file into PostScript document) and then ps2pdf (that converts it back into PDF again). The password protection is lost in the process and you should be able to open the new PDF file ;)

Both pdf2ps and ps2pdf should be in Ubuntu's repositories.

---

### Post by kerry_s on 2007-09-27
> **Murkhanand said:**
> [SIZE="6"][SIZE="6"]Hi Everyone,

Greetings

I have successfully installed adobe reader 7.0 in UBUNTU as well plugin in Firefox. I have received a pdf file which is password protected. Adobe Reader in Ubuntu opens normal pdf file happily so does the Firefox. However, Adobe Reader fails to open the password protected file and I receive the following  message meaning that there is no internet connect.  There is internet connection and Firefox can browse happily including visiting the site [http://www.adobe](http://www.adobe) .com itself. 

Has anyone come this problem and how to solve it?.

Thanks

Murkhanand

have you set the browser?
i use acrobat 8, but there should be a setting in 7.

---

### Post by Shinoda on 2007-11-08
I have a few encrypted PDFs myself I'd like decrypted. Evince opens them normally if I provide it with their passwords, pdftk complains about it needing the owner's password whether I specify it or not (works fine with another encrypted PDF though), and pdf2ps can't open any of the encrypted files saying they require a password for access. Any ideas or alternatives, please? I can give you the PDFs and passwords so you can test them yourselves if you want. TIA.

---

