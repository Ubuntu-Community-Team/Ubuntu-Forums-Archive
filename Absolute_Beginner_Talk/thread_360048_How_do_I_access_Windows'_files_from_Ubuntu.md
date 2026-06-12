---
title: "How do I access Windows' files from Ubuntu?"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-02-12
I have Windows XP on one hard drive and Ubuntu on another drive. How can I access and use Window XP's files inside Unbuntu? I especially would like to start Word inside Unbuntu. I do editing for many people who use Word. :)

---

### Post by jvc26 on 2007-02-12
Can't you use OpenOffice? That can read and write to .doc format and would enable you to open the files and edit them. Remember, Ubuntu is not windows and therefore windows apps will not work for the most part with ubuntu. Some can work under [wine]("http://www.winehq.com/") and more may well work under [crossover office]("http://www.codeweavers.com/") but you have to pay for that. The short of it is, you cant run the majority of windows apps in linux. There are many alternatives, like OO which work very well. If you are having problems read-writing to your files you need to hunt down the ntfs drivers as Ubuntu cannot read/write to NTFS partitions by default because NTFS is a Microsoft proprietary FS.
Il

---

### Post by Maestro23 on 2007-02-12
Link for the OP to read/bookmark for future use: 

Mounting Windows Partitions: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by kittyhawk63 on 2007-02-12
> **Illuvator said:**
> Can't you use OpenOffice? That can read and write to .doc format and would enable you to open the files and edit them. Remember, Ubuntu is not windows and therefore windows apps will not work for the most part with ubuntu. Some can work under [wine]("http://www.winehq.com/") and more may well work under [crossover office]("http://www.codeweavers.com/") but you have to pay for that. The short of it is, you cant run the majority of windows apps in linux. There are many alternatives, like OO which work very well. If you are having problems read-writing to your files you need to hunt down the ntfs drivers as Ubuntu cannot read/write to NTFS partitions by default because NTFS is a Microsoft proprietary FS.
Il

Before I forget, I did not format with NTFS. I am editing for a book. The book has specific formatting for every chapter and page. I want to retain that formatting and be able to e-mail my editing back to the people who are using Word. Will OpenOffice allow me to do this? What is Wine? What does it allow me to do? Just a short answer will do on Wine.

---

### Post by Maestro23 on 2007-02-12
> **kittyhawk63 said:**
> Before I forget, I did not format with NTFS. I am editing for a book. The book has specific formatting for every chapter and page. I want to retain that formatting and be able to e-mail my editing back to the people who are using Word. Will OpenOffice allow me to do this? What is Wine? What does it allow me to do? Just a short answer will do on Wine.

If you click on the link he provided, you would find that wine allows you to run some Windows apps.

---

### Post by kittyhawk63 on 2007-02-12
> **Maestro23 said:**
> If you click on the link he provided, you would find that wine allows you to run some Windows apps.

Thank you for this soft reminder. I am now waiting for answers to my other questions.

---

### Post by Maestro23 on 2007-02-12
> **kittyhawk63 said:**
> Thank you for this soft reminder. I am now waiting for answers to my other questions.

Did some searching over at OpenOffice.org's forums and found a couple of threads about formatting issues between OO and MSOffice.  Here is one:

[http://www.oooforum.org/forum/viewtopic.phtml?t=51881&highlight=document+format+microsoft+office+open+office](http://www.oooforum.org/forum/viewtopic.phtml?t=51881&highlight=document+format+microsoft+office+open+office)

Might shed some light on some things or you can dig a little deeper over there.

Also you might want to open one of those documents you are talking about in OpenOffice, make some changes, and then email it back to your friends and see the results.  Just a thought.

---

### Post by kittyhawk63 on 2007-02-12
I've installed Wine and will give it a try. I will open a document, edit it, and then send it to myself via email into Windows and see what happens inside Word. Thanks for this suggestion.
Maestro23, we crossed each other in our post. We had the same idea. Thanks for your suggestion.

---

### Post by Maestro23 on 2007-02-12
> **kittyhawk63 said:**
> I've installed Wine and will give it a try. I will open a document, edit it, and then send it to myself via email into Windows and see what happens inside Word. Thanks for this suggestion.
Maestro23, we crossed each other in our post. We had the same idea. Thanks for your suggestion.

LOL... Two ships passing in the night.. 

Don't forget to save in the .doc format in OpenOffice.

Good luck.

---

### Post by brn on 2007-02-12
While Open Office can import and export .doc files, the fonts may be difficult to match.  I have a FAT32 partition where I exchange data between the platforms.  I have also been able to copy files directly from the ntfs-formatted WinXP partition into a Linux directory without trouble.  You will probably have less trouble simply doing the editing in Windows.  Wine will not run some Windows apps from within the Windows partition (or drive) because it cannot locate certain internal calls there.  "Compatibility" can only go so far.

---

### Post by kittyhawk63 on 2007-02-12
Thanks for all the suggestions. I guess the safest thing to do in my case is to stay with Gates for doing Word docs. Im closing this thread now.

---

