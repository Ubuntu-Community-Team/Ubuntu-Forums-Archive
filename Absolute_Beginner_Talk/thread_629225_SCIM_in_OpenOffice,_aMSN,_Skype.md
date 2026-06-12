---
title: "SCIM in OpenOffice, aMSN, Skype"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by lanchongzi on 2007-12-02
on my Mandriva 2008 instal - using Gnome Desktop, as well as KDE -l all those problems were solved by merely creating a file called ".i18n" in side the home folder that contains the following

LC_TELEPHONE=en_US.UTF-8
LC_CTYPE=en_US.UTF-8
LANGUAGE=en_US.UTF-8:en_US:en
LC_MONETARY=en_US.UTF-8
LC_ADDRESS=en_US.UTF-8
LC_COLLATE=en_US.UTF-8
LC_PAPER=en_US.UTF-8
LC_NAME=en_US.UTF-8
LC_NUMERIC=en_US.UTF-8
SYSFONT=lat0-16
LC_MEASUREMENT=en_US.UTF-8
LC_TIME=en_US.UTF-8
LANG=en_US.UTF-8
LC_IDENTIFICATION=en_US.UTF-8
LC_MESSAGES=en_US.UTF-8
GTK_IM_MODULE=scim
QT_IM_MODULE=scim
XIM_PROGRAM="scim -d"
XMODIFIERS=@im=SCIM 

is there something similar in Ubuntu?
I mean that was bloody easy, just copy that file into your home folder and all the issues were solved.

how come in Gutsy it is that friggin hard?!?

could someone please tell me how to get it to work in Skype as well as in aMsn ( it does work in OO )

Thanks

---

### Post by kelvinn on 2007-12-02
It has been quite some time since I've used SCIM for input, but I think for Skype I had to install one of the QT plugins (scim-bridge-client-qt or scim-qtimm).  Best of luck!

---

### Post by TWO on 2007-12-26
> **kelvinn said:**
> It has been quite some time since I've used SCIM for input, but I think for Skype I had to install one of the QT plugins (scim-bridge-client-qt or scim-qtimm).  Best of luck!

What does the 'qt' plugin do?

---

### Post by seshomaru samma on 2007-12-31
I can use Chinese in every application in Gutsy . though it is a Feisty upgrade so as far as remember I didnt need to do anything.
How did you install SCIM?
Did you read[ this]("https://help.ubuntu.com/community/SCIM")?

---

