---
title: "Problem Installing Awn Curves"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by lookmomimonlinux on 2007-10-27
when i try to add this line:

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator



to my sourcelist i get


Could not save the file /etc/apt/sources.list.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

---

### Post by Maestro23 on 2007-10-27
> **lookmomimonlinux said:**
> when i try to add this line:

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator



to my sourcelist i get


Could not save the file /etc/apt/sources.list.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

You need root pemission, hence sudo or gksudo.

> gksudo gedit /etc/apt/sources.list

That file is owned by root.

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by lookmomimonlinux on 2007-10-27
oh, so how do i obtain root permission?

---

### Post by Maestro23 on 2007-10-27
> **lookmomimonlinux said:**
> oh, so how do i obtain root permission?

I told you.  You need** sudo or gksuo(graphical)** in front of you command.

You're using gedit to edit the file correct?  Then:

> gksudo gedit /etc/apt/sources.list

Make your changes, then save the file.

---

### Post by lookmomimonlinux on 2007-10-27
i believe so, but now it asks me for my sudo password in the terminal. i'm lost

---

### Post by Maestro23 on 2007-10-27
> **lookmomimonlinux said:**
> i believe so, but now it asks me for my sudo password in the terminal. i'm lost

That is your user password.  The one you created with your user account when you 1st installed Ubuntu.

---

### Post by lookmomimonlinux on 2007-10-27
yes, but when i type it, either nothing happens or it asks me for it again

---

### Post by Maestro23 on 2007-10-27
> **lookmomimonlinux said:**
> yes, but when i type it, either nothing happens or it asks me for it again

It's not going to show up when you type it.  Type it in, then hit ENTER.

---

### Post by lookmomimonlinux on 2007-10-27
alright, i pasted that line before the other one but it still says that i don't have permission?

---

### Post by lookmomimonlinux on 2007-10-27
little help please?

---

### Post by lookmomimonlinux on 2007-10-27
little help pleeease?

---

### Post by Frak on 2007-10-27
Okay, so when it asks for your password, you do enter the  password right?

---

### Post by lookmomimonlinux on 2007-10-27
yes, i figured that problem out though, i think. anyway i'll past the code to give me root permission before the line but it still says i don't have permission. i don't know how to solve this

---

### Post by Frak on 2007-10-27
Try
```
sudo gedit /etc/apt/sources.list
```

Instead

---

### Post by lookmomimonlinux on 2007-10-27
no dice:(

---

### Post by Maestro23 on 2007-10-27
> **lookmomimonlinux said:**
> no dice:(

Instead of copy/pasting the deb lines, try typing them in after you open up your sources.list.

Type them in, then save the file.

---

### Post by lookmomimonlinux on 2007-10-27
nada

---

### Post by stomponthis on 2007-10-27
Just to clarify....
To open the file to add the sources (a.k.a the sources.list file) you are typing 
```
sudo gedit /etc/apt/sources.list
```
Then adding the sources?
It sounded to me like you were trying to add "sudo gedit /etc/apt/sources.list" to the sources file itself?

---

### Post by lookmomimonlinux on 2007-10-27
i'm going by these directions: 

[http://ubuntuforums.org/showthread.php?t=572019&highlight=awn+curves](http://ubuntuforums.org/showthread.php?t=572019&highlight=awn+curves)

is there anything wrong there or an easier way to do this?

---

### Post by Frak on 2007-10-27
Try
```
sudo nano /etc/apt/sources.list
```
It will bring up a text based editor, it works just like the normal one, but without a scroll-bar.

Now, copy the deb lines, then go to the bottom of your document and press Shift+Insert to paste

Then press Ctrl+x, y, Enter

---

### Post by lookmomimonlinux on 2007-10-27
nothing happens when i type cntrl x y

---

### Post by llamakc on 2007-10-27
Have you opened /etc/apt/sources.list?

IN THE TERMINAL

```

sudo nano /etc/apt/sources.list

```

---

### Post by lookmomimonlinux on 2007-10-27
i'm in the sources.list(/etc/apt)-gedit
am i in the wrong place?

obviously things will take awhile for me to get used to,but i am wondering as a ubuntu user, are you subject to having to reconfigure terminals and source lists for hours when installing simple little tools/programs to play with when installation wigs out unexpectedly?

---

### Post by lookmomimonlinux on 2007-10-27
i have the terminal open and i've done all the steps leading up to where it requires me to 

stay in the awn-curves folder throughout all the instructions I give!
make sure you have your AWN repositories:

press ALT+F2,
type:

gksudo "gedit /etc/apt/sources.list"

Press Run then add the corresponding code at the bottom:

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator


i'm there. it says i don't have permission to do that last step

---

### Post by Maestro23 on 2007-10-27
> **lookmomimonlinux said:**
> i have the terminal open and i've done all the steps leading up to where it requires me to 

stay in the awn-curves folder throughout all the instructions I give!
make sure you have your AWN repositories:

press ALT+F2,
type:

gksudo "gedit /etc/apt/sources.list"

Press Run then add the corresponding code at the bottom:

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator


i'm there. it says i don't have permission to do that last step

Can you goto: System>>Admin>>Users & Groups

Click on your User Name, Then Properties, and finally User Privileges.  Is the "Administer System" Box checked?

---

### Post by lookmomimonlinux on 2007-10-27
also does anyone have a pidgin sn that would be able to help me out? this waiting for posts takes too long, i've been on here for a couple of hours and i still don't have this resolved. **** i'll pay pal $5 to whoever can help me

---

### Post by lookmomimonlinux on 2007-10-27
yes, it is checked

---

### Post by lookmomimonlinux on 2007-10-27
what are the repositories? did i dl them in the former steps?

---

### Post by lookmomimonlinux on 2007-10-27
ok, $10!

---

### Post by llamakc on 2007-10-27
Your issue isn't with Ubuntu. It's with trying to configure stuff post-install. It's no different than trying to install NON-MS programs in Windows.

A primer:

Ubuntu updates and downloads software through its package management system. The places on the internet that it looks for and grabs stuff from is dictated by the lines in the /etc/apt/sources.list file.

You're asked to edit the /etc/apt/sources.list file in those instructions. I just installed AWN-Curves after reading your post and it's working fine. 

You don't DOWNLOAD the repositories. You edit the /etc/apt/sources.list file to include the internet site where your computer would go look for software.

llamakc on AIM.

---

### Post by lookmomimonlinux on 2007-10-27
Does Anyone Have A Sn That Can Help Me!? I've Been On Here For 2 Hrs Trying To Figure This Out. Is There A More User-friendly/timely Way To Learn Ubuntu?

---

### Post by llamakc on 2007-10-27
> **lookmomimonlinux said:**
> Does Anyone Have A Sn That Can Help Me!? I've Been On Here For 2 Hrs Trying To Figure This Out. Is There A More User-friendly/timely Way To Learn Ubuntu?

Yes. Reading. I already gave you my nick for AIM.

See? You're not even reading the responses.

---

### Post by Frak on 2007-10-27
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

From our own Aysiu

---

### Post by nikoPSK on 2007-11-03
> **lookmomimonlinux said:**
> when i try to add this line:

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator



to my sourcelist i get


Could not save the file /etc/apt/sources.list.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

thats not a curves problem... its just a source code thing. If it doesn't work in alt+f4 try this in terminal:

```
gksudo "gedit /etc/apt/sources.list" 
```

i had already included gksudo. Please mark this as SOLVED.

---

