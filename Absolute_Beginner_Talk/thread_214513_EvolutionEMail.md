---
title: "EvolutionEMail"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by prisley on 2006-07-12
Well I did it and gotr a copy of the new Kubuntu ver 6.06 from Amazon because K3b would not copy my dvd files. So I decidied to upgrade from ubuntu 5.1 and figured that K3b would work better on a KDE desktop. 

It did not and I am back to Ubuntu and Gnome for now. But I lost the old desktop configuration and now have to reset up everything although I do have my evolution files. But I must put the old files back in the new setup evolution program. 

The question is, where are the data files kept in Evolution? I can not find where that program keeps its e mail message files. Need to know so I can put my old files there.  

Hope someone can give me a heads up on this.

Peter

---

### Post by Ctrl+Alt+Del on 2006-07-12
they are kept in .evolution/ in your home directory

---

### Post by prisley on 2006-07-12
Thanks for the reply.  I sent you a reply  but it got eat by the dog. My fault.

I found the place but could not figure out how to import kmail messages into Evolution. I suspect you can not do that. Is that so?  I found two folders that had messages on them. One that had all of them in a huge file and one that was a cache that had folders with one file or more in them. I do not understand how Evolution sorts its messages and so I am afraid I will not be able to just drop those kmail message files into the evolution folders.

I guess it takes the right script and that would have to go through import on evolution which I have no idea how to work.

Thanks for the heads up, it was useful.

Peter

---

### Post by prisley on 2006-07-19
Here is the latest. I found .evolution file and found that the in box was in local and so I went to the backup and copied that file over to the running .evolution file. It worked!

But the permissions on the newly created file did not allow my evolution to open it up. the message headers were in the inbox but the text was empty! I checked the files in local and found that they had changed the level of permissions So I changed the permissions in Natulis and that did the trick.

Why were the permissions changed so that the text will not show up? 

I also am unable to backup some files because the K3b program tells me I have insufficient permissions to read the following files......

Why would I have insufficient permissions when I sign with my password? I thought I was root. 

Perhaps my dvd/cd RW is not registered as root? I can not figure this out. I am sure it is the dvd/cd because when I open up the properties box for that device I get a permission box I am unable to change and it is half lite up. 

How do I get the permissions changed on that device so that it will read all the files? Otherwise I can not make a complete backup.

Peter

---

