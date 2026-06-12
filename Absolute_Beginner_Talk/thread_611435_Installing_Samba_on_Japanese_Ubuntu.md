---
title: "Installing Samba on Japanese Ubuntu"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by Beatbreaker on 2007-11-12
Hi i'm getting a Japanese friend into Ubuntu and he would really like to use it for networking particularly with Samba. We've come into a really weird problem though

he has installed Ubuntu in Japanese for himself - he is running it of a virtual PC form within WinXP. I have a dual boot system with Ubuntu and XP.

He's trying to install samba - and types the simple command

> sudo apt-get install samba

he always gets a message back saying that the database could not be accessed or something, i can't read the reply because it's in Japanese. I tried the same command on my Ubuntu and it worked.

so i thougt it was his sources.list - I've since replaced all of this sources.list with my sources.list and tried the command again and it still doesn't work - it gives the same reply back.

so what's going on here? if this command won't work is there is step by step guide on how to install the tar.gz version on a machine? sorry i'm a real noob and don't remember how to do an instillation of tar.gz files (herein lies the pros and cons of having a good GUI less reliant on the terminal)

cheers!

---

### Post by Henaro on 2007-11-13
Can you paste the error message here?  I consider myself somewhat proficient in the Japanese language (I've been taking it for almost 4 years now).  

Also if you want to compile the source (by tar.gz) just run:
./configure 
make 
make install 

as super user.

---

