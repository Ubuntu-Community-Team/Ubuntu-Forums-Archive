---
title: "Adduser peculiarities"
date: 2005-08-13
forum: Absolute Beginner Talk
---

### Post by marsbt on 2005-08-13
Hello Ubuntians,

this is my first time I setup Ubuntu on a computer. It was just for testing purposes and  in the end it was an educating experience. Well done to the developers.

I have a question that most of the people might know the answer to. When adding a new user via a terminal by adduser, the new user is added along with the group of the same name. It does not add user to other important groups like audio, cdrom, floppy, etc. I know that can be done by giving the relevant options in the command line, but the useradd command seems to be pretty interactive. Also, if I add a user via the System > Administration > Users and Groups it does the same and it is only when I add the groups manually does the user get added to cdrom, floppy, and audio.

These days when installing a desktop version of Ubuntu (or Linux in general) why don't we get a basic user when adding one. A complete newbie wouldn't know if the group addition of audio is needed for new users! Just imagine a new user whose account is just created and wants to play some music....."duh! this linux thing can't even play my music out of the box. Bye bye ubuntu/linux"

---

### Post by suziequzie on 2005-10-19
I too have encountered some "Adduser" peculiarities.

I tried to add my roommate to Kubuntu, (using Kuser) and I copied over the groups that I am in, so that I can teach him how to use it and install his own packages, etc, etc. 

Unfortunately, I get a kmserver (I think that's the right word) crash when I try to log in through his account. 

I am suzie, uid is 1000.   he is bobby, and the uid number it gave him is 500. I gave him the adm, admin, audio, cdrom, dialout, dip, floppy, lpadmin, plugdev, scanner, and video groups (same as mine). 

But still, it causes a crash when I try and log in with his account. 

Any suggestions would be wonderful, thanks.

Suzie Quzie

---

