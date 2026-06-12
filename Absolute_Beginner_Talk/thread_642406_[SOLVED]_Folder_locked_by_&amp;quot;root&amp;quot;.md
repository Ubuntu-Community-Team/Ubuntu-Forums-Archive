---
title: "[SOLVED] Folder locked by &amp;quot;root&amp;quot; ??"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by rock0nman on 2007-12-16
How do I unlock my "Desktop" Folder?    It has a lock simbol on it and i can't change anything on it or in it.

---

### Post by diatribe on 2007-12-16
chown to your username

---

### Post by rock0nman on 2007-12-16
chown?

---

### Post by diatribe on 2007-12-16
type 

man chown 

in a terminal to learn about it, it changes ownership, you will also need to use sudo with chown seeing as root is the owner of the folder

---

### Post by coffeecat on 2007-12-16
It may not necessarily be locked by root. The permissions may have been changed to read only, but still owned by you. That would be one reason for a lock symbol.

Open your home folder and right-click on the Desktop folder. Click on the 'permissions' tab. If it's still owned by you, you can change it to read/write yourself. If it's owned by root, then open a terminal and:

```
sudo chown yourusername: /home/yourusername/Desktop
```Don't forget the colon after yourusername - that's to reset to the correct group.

---

### Post by rock0nman on 2007-12-16
That still didn't help any.  The current owner of the desktop folder is "root"   With the owner being root i can't access the folder.   I just need to know what to type to change the folder back to normal

---

### Post by diatribe on 2007-12-16
sudo chown yourusername: /home/yourusername/Desktop

you were told exactly what to do already

---

### Post by rock0nman on 2007-12-16
> **coffeecat said:**
> It may not necessarily be locked by root. The permissions may have been changed to read only, but still owned by you. That would be one reason for a lock symbol.

Open your home folder and right-click on the Desktop folder. Click on the 'permissions' tab. If it's still owned by you, you can change it to read/write yourself. If it's owned by root, then open a terminal and:

```
sudo chown yourusername: /home/yourusername/Desktop
```Don't forget the colon after yourusername - that's to reset to the correct group.

Outstanding!  Thanks a bunch man.

---

### Post by rock0nman on 2007-12-16
> **diatribe said:**
> sudo chown yourusername: /home/yourusername/Desktop

you were told exactly what to do already

I hadn't refreshed the page when i replied.

---

### Post by diatribe on 2007-12-16
> **rock0nman said:**
> That still didn't help any.  The current owner of the desktop folder is "root"   With the owner being root i can't access the folder.   I just need to know what to type to change the folder back to normal

and also if you had bothered reading the man page you would have been able to figure out the syntax of the command

---

### Post by coffeecat on 2007-12-16
**rock0nman** - glad it's sorted.

Just for the record, I got something wrong.

> **coffeecat said:**
> The permissions may have been changed to read only, but still owned by you. That would be one reason for a lock symbol.

If the folder was read only, you wouldn't be able to change contents, but I don't think there would be a lock symbol. I'm posting from my Mac at the moment, so I wasn't able to check. Getting a bit absent-minded. :wink:

---

### Post by rock0nman on 2007-12-17
> **diatribe said:**
> and also if you had bothered reading the man page you would have been able to figure out the syntax of the command

If that's all the help you're going to provide a beginner then keep it to yourself.  I read the man page and couldn't figure it out.  I'm not exactly thrilled with the quality and complexity of this operating system.  IMO it has a long way to go before it could ever "replace" windows.  However, it is fun to toy around with and see that there is hope of squashing the Microsoft monopoly some day.

---

### Post by rock0nman on 2007-12-17
> **coffeecat said:**
> **rock0nman** - glad it's sorted.

Just for the record, I got something wrong.



If the folder was read only, you wouldn't be able to change contents, but I don't think there would be a lock symbol. I'm posting from my Mac at the moment, so I wasn't able to check. Getting a bit absent-minded. :wink:

Thanks again.   It wasn't locked.  The ownership changed to root for some reason when I ran an auto-install from some program.  There's a lot of kinks in this system still.

---

### Post by macogw on 2007-12-17
> **rock0nman said:**
> Thanks again.   It wasn't locked.  The ownership changed to root for some reason when I ran an auto-install from some program.  There's a lot of kinks in this system still.

If you installed the program from your desktop and had to do it as root, *maybe* whatever program it was had a messed up script that changed things it shouldn't have.

The suggestion to read the manpage is a good one, but the problem is it takes a while to understand those things.  I learned how they worked by reading manpages for things I already knew how to use (like apt-get), so I could get a grip on the format of it.  RTFM isn't something that's supposed to be said in the Ubuntu community though.

---

### Post by rock0nman on 2007-12-17
> **macogw said:**
> If you installed the program from your desktop and had to do it as root, *maybe* whatever program it was had a messed up script that changed things it shouldn't have.

The suggestion to read the manpage is a good one, but the problem is it takes a while to understand those things.  I learned how they worked by reading manpages for things I already knew how to use (like apt-get), so I could get a grip on the format of it.  RTFM isn't something that's supposed to be said in the Ubuntu community though.

I did learn quite a bit from reading the man..specifically how to change the owner to root.  But couldn't find my specific problem.  This is a great forum and provides a hoard of information.  Ubuntu wouldn't survive without it.  I'm pretty good with computers but have had to turn to this forum more than i've ever had with anything else i've worked on.

---

### Post by philinux on 2007-12-17
> **diatribe said:**
> and also if you had bothered reading the man page you would have been able to figure out the syntax of the command

Bit of a grouch, must be having a bad day . :lolflag:

---

### Post by diatribe on 2007-12-17
> **philinux said:**
> Bit of a grouch, must be having a bad day . :lolflag:

no it has nothing to do with that, its the fact that people are too ignorant/lazy to bother trying to figure out something for themselves and are completely reliant upon other to do even the simplest of tasks.  and quotes like:

If that's all the help you're going to provide a beginner then keep it to yourself. I read the man page and couldn't figure it out. I'm not exactly thrilled with the quality and complexity of this operating system. IMO it has a long way to go before it could ever "replace" windows. However, it is fun to toy around with and see that there is hope of squashing the Microsoft monopoly some day.

only go to further my position.  the fact of the matter is that I told him what command to use, then the EXACT syntax of the command was given to him, but he was too impatient to bother refreshing the page to check.  The problem is that people need to learn to do things for themselves, not have everything spoon-fed to them.

Edit: anyway this is going nowhere this thread should be marked as solved and closed.

---

### Post by aysiu on 2007-12-17
This link may help you in terms of not having folders suddenly becoming owned by root:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by rock0nman on 2007-12-17
> **diatribe said:**
> no it has nothing to do with that, its the fact that people are too ignorant/lazy to bother trying to figure out something for themselves and are completely reliant upon other to do even the simplest of tasks.  and quotes like:

If that's all the help you're going to provide a beginner then keep it to yourself. I read the man page and couldn't figure it out. I'm not exactly thrilled with the quality and complexity of this operating system. IMO it has a long way to go before it could ever "replace" windows. However, it is fun to toy around with and see that there is hope of squashing the Microsoft monopoly some day.

only go to further my position.  the fact of the matter is that I told him what command to use, then the EXACT syntax of the command was given to him, but he was too impatient to bother refreshing the page to check.  The problem is that people need to learn to do things for themselves, not have everything spoon-fed to them.

Edit: anyway this is going nowhere this thread should be marked as solved and closed.

So you're one of those people.  If you don't like my actions then ignore them please.  I learn better when I hear it from first hand accounts than from reading a manual.  Just my style.   When I learn this program I will be more than willing to help someone out as these fine people have assisted me.  :guitar:

---

### Post by rock0nman on 2007-12-17
> **aysiu said:**
> This link may help you in terms of not having folders suddenly becoming owned by root:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Thanks.  I'll keep that one bookmarked.

---

