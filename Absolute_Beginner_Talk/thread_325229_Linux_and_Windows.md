---
title: "Linux and Windows"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by Smitty_203 on 2006-12-25
I tried e-mailing a paper on Open Office Word and tried opening it on Windows but it came up weird...is there a way for me to convert the file so that it can be read on Windows? It's probably a slow moment for me to ask now though...


Also: if there is a way, i have to create a PowerPoint presentation for a class and i won't be able to have time to get to a Windows computer so if i CAN conver the files, can i also create the powerpoint in a way that i can present it on a windows computer?

~1~Thanks in advance~1~

---

### Post by sylv3rblade on 2006-12-25
are you sure you saved the document as *.doc and not otherwise?

---

### Post by dbbolton on 2006-12-25
1. i would export the file as a pdf or doc and then email it.

2. use open office presentation, and export it as, say, a swf (flash movie) which can be played on internet explorer.

---

### Post by PurplePenguin on 2006-12-25
> **sylv3rblade said:**
> are you sure you saved the document as *.doc and not otherwise?

I agree that this is probably the solution.  OpenOffice always warns the user when saving to formats such as .doc and tries to talk you into using their native format (which, if you are saving files for personal use and don't need to send them to people with MS Office, is a really good idea).

So you actually do need to jump through a tiny hoop in order to save as .doc.  But it is possible and works quite well. :)

---

### Post by rsambuca on 2006-12-25
In Open Office, go to Tools --> Options.  In the window that opens up, click on Load/Save --> General.  On the Default format section, change Text Document to Microsoft Word 97/2000/XP, Presentation to Microsoft Powerpoint..., and Spreadsheet to Microsoft XL.

Yeah, I know it sucks, but 95% of those documents are in that format, so I'll will just make your life a lot easier if you change the defaults.  That way, you can just transfer them to another computer or to friends and know that they can use them.

---

### Post by rbhigday on 2006-12-25
> **rsambuca said:**
> In Open Office, go to Tools --> Options.  In the window that opens up, click on Load/Save --> General.  On the Default format section, change Text Document to Microsoft Word 97/2000/XP, Presentation to Microsoft Powerpoint..., and Spreadsheet to Microsoft XL.

Yeah, I know it sucks, but 95% of those documents are in that format, so I'll will just make your life a lot easier if you change the defaults.  That way, you can just transfer them to another computer or to friends and know that they can use them.

Thanks for the info I was wondering that myself as a newbie user about to install UBUntu for the first time :)

---

### Post by k1001001 on 2006-12-25
Also, be sure you've updated to OpenOffice 2.0. One of my friends said the previous version (1.whatever) had problems with the formatting in Windows, even when saved as a .doc. I haven't had this problem in 2.0 though.

---

### Post by dawg on 2006-12-25
Hey, I've got the latest version of OOo and to be honest with you, whenever i open up docs written in MS WORD, the document ends up looking like sh*t.  Why is this?  For example, I was looking at my friends resume which he typed up in word, in it looks fantastic.  He later emailed it to me, and since im going through my "i hate microsoft" phase I only use opensource programs, (but im guilty of running XP as we speak).  Well, I opened up the .doc, and everything changed, there are blocks where there weren't any, text is moved, you name it.  I always have to adjust the docs and to be honest i feel as though i waste more time fixing it than it would to have OFFICE running.  Whats the deeleo?

---

### Post by macogw on 2006-12-25
Do you have Windows fonts installed?  It might be having trouble translating Times New Roman special characters into Vera Sans or DejaVu Sans or whatever.

sudo apt-get install msttcorefonts

---

### Post by dawg on 2006-12-25
Im running it on XP PRO, i assume, i am.  I just looked at that same resume, and it looks better on my suse laptop.  running version 10.2.

---

### Post by dawg on 2006-12-25
Part of the problem i guess is my text boundries being on, not like thats much of a problem, just an eyesore, but its not like they get printed.  But sometimes i do have to make adjustments to the docs to make them look right.[http://www.geocities.com/marioishere/OOo.JPG]("http://www.geocities.com/marioishere/OOo.JPG")

---

### Post by macogw on 2006-12-25
The grey lines don't print.  They're just the "invisible" table boundaries.  I don't know about that line, except that it'd make plenty more sense to just set the formatting on that bit of border to "black" instead of "none".

---

### Post by Smitty_203 on 2006-12-27
oh, i didn't know that there was a formatting optiin for that. thanks, but if i get videos sent to me from a windows computer, can i get it to play on Ubuntu? it never shows for me...

---

### Post by lyceum on 2006-12-27
> **dawg said:**
> Hey, I've got the latest version of OOo and to be honest with you, whenever i open up docs written in MS WORD, the document ends up looking like sh*t.  Why is this?  For example, I was looking at my friends resume which he typed up in word, in it looks fantastic.  He later emailed it to me, and since im going through my "i hate microsoft" phase I only use opensource programs, (but im guilty of running XP as we speak).  Well, I opened up the .doc, and everything changed, there are blocks where there weren't any, text is moved, you name it.  I always have to adjust the docs and to be honest i feel as though i waste more time fixing it than it would to have OFFICE running.  Whats the deeleo?

At work I use MS office & OOo, as OOo does everything I want, except put the page numbers on the on the outside of the page. I always have to "fix" everything going from one to the other. When writing papers for school some of them are a little longer or shorter than when I send them from OOo to the prof's MS Word. Same fonts, same size, spacing etc.. I think it is just what happens in life when you use 2 different programs. But, if we shell out cash for MS Office then they will never switch to the open format (like they would anyway ](*,) )

---

### Post by rykel on 2006-12-29
I would like to add my 2 cents here...

Until this very day, with OpenOffice.org 2.0.4, I still have alignment and font problems between PowerPoint/Impress and Word/Writer. (Not sure about Access/Base and Excel/Calc)

This is one reason why I need to install at least PowerPoint on my system, be it Linux or Windows.

However, if Microsoft Office users are all using OpenOffice.org, then life would be a bed of roses, since the "errors" in the documents only arrive when I am exchanging files with Microsoft Office users.

I support OpenOffice.org and open formats all the way!!!   :D

---

### Post by anaconda on 2006-12-29
Why wont you install OO to your windows machine? its free!

---

### Post by rykel on 2006-12-29
> **anaconda said:**
> Why wont you install OO to your windows machine? its free!

I do!

I love OpenOffice.org!!!   = )

I am only saying that because there are still people who use PowerPoint, it forces me to install PowerPoint too, because far too often, OOo cannot seem to open PPT files well enough...

---

### Post by lyceum on 2006-12-29
> **rykel said:**
> I do!

I love OpenOffice.org!!!   = )

I am only saying that because there are still people who use PowerPoint, it forces me to install PowerPoint too, because far too often, OOo cannot seem to open PPT files well enough...

I have never had that problem. Just wondering, is there something common about the files that won't open, or is it a random thing?

:-k

---

### Post by rykel on 2006-12-30
> **lyceum said:**
> I have never had that problem. Just wondering, is there something common about the files that won't open, or is it a random thing?

:-k

No, not that the files won't open, but it's that the FONTS and ALIGNMENTS in the files are out... Sometimes, if the original PowerPoint file uses a certain Chinese font, it will show up as gibberish in Impress... the only way to solve the problem is to highlight all the messed up characters and change them to one of the Linux Chinese fonts.

---

### Post by macogw on 2006-12-30
> **lyceum said:**
> At work I use MS office & OOo, as OOo does everything I want, except put the page numbers on the on the outside of the page. I always have to "fix" everything going from one to the other. When writing papers for school some of them are a little longer or shorter than when I send them from OOo to the prof's MS Word. Same fonts, same size, spacing etc.. I think it is just what happens in life when you use 2 different programs. But, if we shell out cash for MS Office then they will never switch to the open format (like they would anyway ](*,) )

could the length have to do with OOo defaulting to .79" instead of 1" (it thinks in A4 instead of Letter format)?

Has anyone tried OOo 2.1 rather than 2.0.4 and gotten better conversion?

rykel, about the Chinese: maybe they're using a specific Chinese font that doesn't switch right.  When I open files I typed in Japanese on Windows on a different Windows computer that shows up as gibberish too.  If the computer doesn't have the same fonts installed, adjustments have to be made regardless.

---

### Post by Sef on 2006-12-30
> Do you have Windows fonts installed? It might be having trouble translating Times New Roman special characters into Vera Sans or DejaVu Sans or whatever.

sudo apt-get install msttcorefonts

Thanks for the tip.

---

### Post by lyceum on 2006-12-31
> **rykel said:**
> No, not that the files won't open, but it's that the FONTS and ALIGNMENTS in the files are out... Sometimes, if the original PowerPoint file uses a certain Chinese font, it will show up as gibberish in Impress... the only way to solve the problem is to highlight all the messed up characters and change them to one of the Linux Chinese fonts.

That makes sense. I guess there really isn't much you can do about that. :???:

---

