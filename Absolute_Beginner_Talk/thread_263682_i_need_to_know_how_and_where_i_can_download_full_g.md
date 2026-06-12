---
title: "i need to know how and where i can download full good media players that auto install"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by shashank on 2006-09-23
i need to GOOD MEDIA PLAYERS THAT AUTO INSTALL AND A INSTALLER THAT INSTALLS THEM.

THIS IS WHAT I WANT TO DO--------------------
1)I DONT WANT TO CONNECT TO INTERNET TO INSTALL EVERYTHING
2) I WAnt PLAYER OF WHICH I HAVE WHOLE INSTALL FILE . (THAT DOES NOT NEED TO CONNECT TO INTERNET) AND WHICH I CAN DISTRIBUTE TO EVERY ONE USING UBUNTO 
AND THEN THEY SHOULD NOT BE REQUIRED TO CONNECT TO INTERNET AND INSTALL THOSE PLAYERS.

I KNOW THAT TOTEM PLAYER THAT IS THE PLAYER BY DEFAULT NEED SOME NON-FREE OR NON-RESTRICTED CODECS AND EVERY TIME I INSTALL UBUNTU IN SOMEONES PCS
I HAVE TO CONNECT TO INTERNET TO DOWNLOAD THEM.....

I LIKE THIS PLAYER CALLED XINE AND I STILL HAVE TO CONECT TO INTERNET TO INSTALL IT
*************************************************************
MY BOTTOM LINE QUESTION IS-------------------------------------

CAN ANY ONE TELL ME IS THERE ANY WAY I CAN ARCHIVE THEM AND INSTALL THEM ANYTIME AND ON ANY UBUNTU PC I WANT ?

---

### Post by jd65pl on 2006-09-23
Why don't you search for some .deb files they auto install after you have downloaded for the first time. You will probably also want to download the install files for the restricted formats also [see here]("https://help.ubuntu.com/community/RestrictedFormats")

J

---

### Post by bulldog on 2006-09-23
> **shashank said:**
> i need to GOOD MEDIA PLAYERS THAT AUTO INSTALL AND A INSTALLER THAT INSTALLS THEM.

THIS IS WHAT I WANT TO DO--------------------
1)I DONT WANT TO CONNECT TO INTERNET TO INSTALL EVERYTHING
2) I WAnt PLAYER OF WHICH I HAVE WHOLE INSTALL FILE . (THAT DOES NOT NEED TO CONNECT TO INTERNET) AND WHICH I CAN DISTRIBUTE TO EVERY ONE USING UBUNTO 
AND THEN THEY SHOULD NOT BE REQUIRED TO CONNECT TO INTERNET AND INSTALL THOSE PLAYERS.

I KNOW THAT TOTEM PLAYER THAT IS THE PLAYER BY DEFAULT NEED SOME NON-FREE OR NON-RESTRICTED CODECS AND EVERY TIME I INSTALL UBUNTU IN SOMEONES PCS
I HAVE TO CONNECT TO INTERNET TO DOWNLOAD THEM.....

I LIKE THIS PLAYER CALLED XINE AND I STILL HAVE TO CONECT TO INTERNET TO INSTALL IT
*************************************************************
MY BOTTOM LINE QUESTION IS-------------------------------------

CAN ANY ONE TELL ME IS THERE ANY WAY I CAN ARCHIVE THEM AND INSTALL THEM ANYTIME AND ON ANY UBUNTU PC I WANT ?

If you have the time,take a look at your keybord settings,it seems your Caps is stuck.

---

### Post by nalmeth on 2006-09-23
packages.ubuntu.com
watch for dependencies
you could make a script that installed the stuff you need, or do it manually. Ex, all the .deb's in one folder, cd to the directory, and enter
sudo dpkg -i *

OR

[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)

---

