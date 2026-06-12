---
title: "How do I Install Word 2000 in Ubuntu"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-03-26
I need to install MS Word 2000 into Ubuntu. It is the only program that keeps me tied to MS Windows. How do I install it into Ubuntu, or can I? 

Note: I have a **stand-alone** program of Word 2000. I do _not_ need MS Office to install it. Since Word 2000's install is an .exe file, how do I go about installing it to Ubuntu? 

Do I copy the entire program to a folder and work from there? Or, do I try to use the setup.exe file to install it? I have Crossover, but have not yet used it. 

To answer the inevitable question beforehand: I need Word 2000 to do editing for 30+ authors who have written their books in Word.

Any help would be greatly appreciated. :)
kh

---

### Post by igknighted on 2007-03-26
> **kittyhawk63 said:**
> I need to install MS Word 2000 into Ubuntu. It is the only program that keeps me tied to MS Windows. How do I install it into Ubuntu, or can I? 

Note: I have a **stand-alone** program of Word 2000. I do _not_ need MS Office to install it. Since Word 2000's install is an .exe file, how do I go about installing it to Ubuntu? 

Do I copy the entire program to a folder and work from there? Or, do I try to use the setup.exe file to install it? I have Crossover, but have not yet used it. 

To answer the inevitable question beforehand: I need Word 2000 to do editing for 30+ authors who have written their books in Word.

Any help would be greatly appreciated. :)
kh

Your only good choices are to buy Crossover to install it, or create a windows VM with vmware or some other virtualization software.  Wine really isn't up to the task (at least I wouldn't trust it when doing something important like that).

And I have to say it... did you even try using OO.o first?  I see no reason why it wouldn't handle that task with ease.

---

### Post by NESFreak on 2007-03-26
check crossover for running ms word or use openoffice writer as an alternative

NESFreak

---

### Post by kittyhawk63 on 2007-03-26
Ok. Let's see if I can clear up a few things. 

I have Crossover but have not yet used it. 

Has anyone used 000 to edit Word documents and know if it is completely compatible? I doubt that it is. Remember, I am not wiritng letters, I am editing for authors of books who use footnotes and endnotes and special inserts. They have already written their books in Word and I am editing these books. Will 000 allow editing without messing up the Word format?

Note: Crossover says it can run Word 2000 "viewer." I don't think that is the same thing as running the full program. Am I wrong on this?

---

### Post by r4ik on 2007-03-26
As igknighted mentioned there is nothing Oo can't do (even better)
If you can handle Linux and  do not see any problems to switch over.

---

### Post by igknighted on 2007-03-26
> **kittyhawk63 said:**
> Ok. Let's see if I can clear up a few things. 

I have Crossover but have not yet used it. 

Has anyone used 000 to edit Word documents and know if it is completely compatible? I doubt that it is. Remember, I am not wiritng letters, I am editing for authors of books who use footnotes and endnotes and special inserts. They have already written their books in Word and I am editing these books. Will 000 allow editing without messing up the Word format?

There shouldn't be any issues.  You might want to get the latest OO.o to be safe (it's included in feisty).  I would be more concerned about using Office 2000.  Its three generations old now, and MS has a history of breaking backwards compatibility to older MS Office documents.

---

### Post by kittyhawk63 on 2007-03-26
> **r4ik said:**
> As igknighted mentioned there is nothing Oo can't do (even better)
If you can handle Linux and  do not see any problems to switch over.

I am using Linux. That is what I am using right now. My question is will Crossover install Word 2000 without a hitch. I will try 000, but I doubt that it keeps all the formatting pecularities of Word.

---

### Post by ceeg on 2007-03-26
OpenOffice can read and write Word documents just as well as Microsoft Word can. The interface takes no getting used to either, so have at it!

---

### Post by igknighted on 2007-03-26
> **r4ik said:**
> As igknighted mentioned there is nothing Oo can't do (even better)
If you can handle Linux and  do not see any problems to switch over.

Well, it hasn't cleaned my desk yet and I left it open all day for just that task... oh well.  At least it writes my documents.

As for the footnotes/endnotes concern... In my experience (using these frequently in university) that OO.o handles them better than MS does.  I'm not sure what you mean by special inserts.

Sorry for the DP... should have mutiquoted.

---

### Post by kittyhawk63 on 2007-03-26
Ok, I will give 00.0 a try.
kh
Thanks guys.

---

### Post by r4ik on 2007-03-26
> **kittyhawk63 said:**
> Ok. Let's see if I can clear up a few things. 

I have Crossover but have not yet used it. 

Has anyone used 000 to edit Word documents and know if it is completely compatible? I doubt that it is. Remember, I am not wiritng letters, I am editing for authors of books who use footnotes and endnotes and special inserts. They have already written their books in Word and I am editing these books. Will 000 allow editing without messing up the Word format?

Note: Crossover says it can run Word 2000 "viewer." I don't think that is the same thing as running the full program. Am I wrong on this?

Writer - tools -options - load and save general - text document  (always save as) 
Word 97/2000/xp

---

### Post by juantovarm on 2007-03-26
Open Office is perfectly compatible as long as you decide to save your work as a .doc file. Some minor things might change, if any.

---

### Post by Snowmayne on 2007-03-26
> **r4ik said:**
> As igknighted mentioned there is nothing Oo can't do (even better) 

Have to disagree with you on that one. Have you ever tried doing a copy/paste of an html page with either editor? Word is pretty straightforward. OO, on the otherhand....

As to compatibility.... aside from some slight font and margins changes there isn't much to complain about. They both can read each other's footnotes and make changes if needed and both can save natively in .doc format

---

### Post by newlinux on 2007-03-26
> **juantovarm said:**
> Open Office is perfectly compatible as long as you decide to save your work as a .doc file. Some minor things might change, if any.

As one who has worked a bit in the writing industry, these minor differences might be major. The formatting of documents is critical for authors submitting documents to publishers. That said, Word has some formatting quirks that make it difficult for authors to make submittals anyway. Can't hurt to try OO.

---

### Post by igknighted on 2007-03-26
> **Snowmayne said:**
> Have to disagree with you on that one. Have you ever tried doing a copy/paste of an html page with either editor? Word is pretty straightforward. OO, on the otherhand....

As to compatibility.... aside from some slight font and margins changes there isn't much to complain about. They both can read each other's footnotes and make changes if needed and both can save natively in .doc format

Good point, make sure you have all the MS TTF fonts installed.  Otherwise you could run into some issues.

---

### Post by kittyhawk63 on 2007-03-26
> **newlinux said:**
> As one who has worked a bit in the writing industry, these minor differences might be major. The formatting of documents is critical for authors submitting documents to publishers. That said, Word has some formatting quirks that make it difficult for authors to make submittals anyway. Can't hurt to try OO.

You're right about the quirks. I can't afford the time to mess around with font changes, margin differences, and any other formatting quirks. Even though on one book where there are many contributors to the book and having given explicit instructions on how to format their work for the book, everyone has different levels of abilities. I've spent months reformatting their work so everything will looke the same in the book. I also resend my deited work back to them for their approval and any changes they want made. I then have to re-edit their work. this goes on until everyone is happy and we are all in agreement to the final copy. Only then does it go to the publisher.

That is why I want to know how to install Word 2000 into Ubuntu or how I can use it with Ubuntu. I know nothing about vmware. I will look into it. I have crossover but do not know how to install Word 2000 using it.

---

### Post by kittyhawk63 on 2007-03-26
I just did a fresh install of Ubuntu a day or two back and it did not properly install. Totem is messed up and none of OpenOffice's apps will start. This is the first time that this has happened using this Live CD. Glad that it is a simple install. Sort of.
kh

---

### Post by igknighted on 2007-03-26
> **kittyhawk63 said:**
> You're right about the quirks. I can't afford the time to mess around with font changes, margin differences, and any other formatting quirks. Even though on one book where there are many contributors to the book and having given explicit instructions on how to format their work for the book, everyone has different levels of abilities. I've spent months reformatting their work so everything will looke the same in the book. I also resend my deited work back to them for their approval and any changes they want made. I then have to re-edit their work. this goes on until everyone is happy and we are all in agreement to the final copy. Only then does it go to the publisher.

That is why I want to know how to install Word 2000 into Ubuntu or how I can use it with Ubuntu. I know nothing about vmware. I will look into it. I have crossover but do not know how to install Word 2000 using it.

I have only used Cedega, and Cedega has a nice gui to install apps.  I assume the same is true for Crossover.  VMware is really easy.  Go to their website and get VMware Server, install it (you need the kernel source package installed), and then run any commands it says to finish the config.  Then start VMWare, put in your windows disc and install to a virtual machine.  Once done you have a fully working windows install, inside your ubuntu install.

---

### Post by ac7ss on 2007-03-26
I use OOO for working with MS Word docs all the time. the only tricks I can see are:
Set the default save format to Word2000 and make sure you have the same fonts avalable.

---

### Post by kittyhawk63 on 2007-03-26
> **igknighted said:**
> I have only used Cedega, and Cedega has a nice gui to install apps.  I assume the same is true for Crossover.  VMware is really easy.  Go to their website and get VMware Server, install it (you need the kernel source package installed), and then run any commands it says to finish the config.  Then start VMWare, put in your windows disc and install to a virtual machine.  Once done you have a fully working windows install, inside your ubuntu install.
Thanks
kh

---

### Post by kittyhawk63 on 2007-03-26
> **ac7ss said:**
> I use OOO for working with MS Word docs all the time. the only tricks I can see are:
Set the default save format to Word2000 and make sure you have the same fonts avalable.

I'll give it a try. Thanks.

---

### Post by shaft350x on 2007-03-26
Not that I want to be a nay-sayer.  [Only used OO.o for about a year and Ubuntu for a few months]  I have experienced some odd little quirks when trying to get back and forth between documents made in Word and then opened in OpenOffice.  Tables and bulleted lists have often appeared off-set so much that that are off of the page.  Also there is no vertical alignment option, so to center something requires a bunch of carriage returns or some other "fix".

Also I don't know how much editing that you do in the kind of "shared" document style, where you can make changes or suggest changes and the other person can see what you've changed.  I haven't seen that option implemented into OO.o, yet.

Before I got my network working properly my wife would write her papers in Word and then save them to her USB, from which I would try to open them up in OO.o and sometimes they would be quite different.  So it may take some tweaking, no matter which way you go about it.

Also just so people know I'm not trying to knock OpenOffice, I use it exclusively, and I look forward to the next version where hopefully some of these things will be taken care of.

---

