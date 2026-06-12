---
title: "[SOLVED] I dnt want to type sudo everytime"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by badguyanil on 2007-10-02
I dont want to type sudo everytime while executing a command. Is there a way tht i can login through root so that i can avoid typing in sudo every time.

---

### Post by hyper_ch on 2007-10-02
you can but there's a good reason that you have sudo. You don't need sudo all the time.

---

### Post by Perfect Storm on 2007-10-02
Aye, without it, you'll computer will be owned!

---

### Post by HermanAB on 2007-10-02
This is what you wanted to know:
$ sudo -i
password
#
(now you can do anything with root permissions)

Cheers,

Herman

---

### Post by badguyanil on 2007-10-02
Thx HermanAB .... i will give a try !!

---

### Post by nowshining on 2007-10-02
As others have suggested there  it is best to use sudo - :) - as you may very well regret it. Oh and gksudo nautilus will get u into a root nautilus window to browse and see and write and add/delete files as root.

edit: gksudo and hit enter will bring up a box where you can type any program in there and then hit ok/enter and then input the password and it will bring it up as root.

---

### Post by overdrank on 2007-10-02
> **Artificial Intelligence said:**
> Aye, without it, you'll computer will be owned!

I agree and if you would like to look at this thread
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Good luck!

---

### Post by viking777 on 2007-10-02
> 
I dnt want to type sudo everytime
I dont want to type sudo everytime while executing a command. Is there a way tht i can login through root so that i can avoid typing in sudo every time.



I know what you mean, I gave up using Ubuntu for a long time because of this annoyance, I only came back to it when I found a way around it. This is what you need (it is written for KDE as I don't use Gnome):


1) Go to System Settings/User Management. Click on the 'Administration Mode' button and enter your password.
2) On the Users tab click the checkbox that says 'Show System Accounts'
3)Find user 'Root' and highlight it.
4)Click the 'Modify' button.
5)In the dialog that opens up click the 'Enable' radio button.
6)Go to the 'Password' tab and enter a good strong password.
7)'OK' out of it and you are nearly done.

You now have 2 choices the easiest and best imho is to open Adept, search for and install 'Krusader' this in turn will also install 'Krusader Root Mode' and this will solve all similar such access problems in the future. The alternative is to right click your desktop, choose 'Create New'/'Link to Application'. Open the application tab and in the 'Command' line type
Code:

konqueror --profile filemanagement

Then click on the advanced options button and then the 'Run as a different user' radio button. For 'username' type
Code:

root

then 'OK' out. You now have a desktop shortcut to a root version of konqueror which will again stop these infuriating access problems.



Hope that helps

---

### Post by nowshining on 2007-10-02
to stop typing a root password for a certain program or all I think u'd have to edit the sudoers file with ur username and the path to the program or copy the above root one and paste below it and then change root to ur username.

edit: I still don't know why edit: u'd want to do it:edit- I continue to do it even tho my password is in random characters and is ABOUT 20 characters long.

---

### Post by n3tfury on 2007-10-02
i have to laugh at people that don't want to type sudo and enter a password for root privileges yet they can't do a simple google search to find the answer. <snip>

---

### Post by hyper_ch on 2007-10-02
> **n3tfury said:**
> i have to laugh at people that don't want to type sudo and enter a password for root privileges yet they can't do a simple google search to find the answer.  this is exactly the type of person that SHOULDN'T have root privileges.

That's why I gave no directions on how to do it ;)

---

### Post by badguyanil on 2007-10-06
Solved

---

### Post by SpiritIsReality on 2007-10-06
howdy
we're a caring bunch edit: some care that I don't mess up my system too easily and that I'm more secure. edit: some care that I want to know how not to have to use sudo all the time edit: I think it's all good and I thank all of you.
by the way, I guess it's kind of irritating having to read edit here and there?
edit: edit! haha!good humour laugh, how do you spell that anyway?

buds

---

### Post by nowshining on 2007-10-07
actually without at least a bios by default go into recovery mode and there u go no sudo no more, all ROOT access with the default ubuntu installs.

---

### Post by dptxp on 2007-10-07
> **hyper_ch said:**
> That's why I gave no directions on how to do it ;)

Can not give instructions on how to commit suicide. :)

---

### Post by SpiritIsReality on 2007-10-07
> **nowshining said:**
> actually without at least a bios by default go into recovery mode and there u go no sudo no more, all ROOT access with the default ubuntu installs.
good one
buds

---

### Post by SpiritIsReality on 2007-10-07
> **dptxp said:**
> Can not give instructions on how to commit suicide. :)good one
buds
dptxp ...nice web page ...there's no green with envy face, well maybe this one :mrgreen:

---

### Post by louieb on 2007-10-07
> **dptxp said:**
> Can not give instructions on how to commit suicide. :)

Naw, like a bad penny or Jason, He'll be back with a ***"what the hell did I do thread".   ***

---

### Post by dptxp on 2007-10-07
> **fmat said:**
> good one
buds
dptxp ...nice web page ...there's no green with envy face, well maybe this one :mrgreen:

Thanks, trying to put up something simple and useful. The basic stuff.

---

### Post by svdb on 2007-10-07
> **n3tfury said:**
> i have to laugh at people that don't want to type sudo and enter a password for root privileges yet they can't do a simple google search to find the answer.  this is exactly the type of person that SHOULDN'T have root privileges.

And you're the type of person who SHOULDN'T be here.
You probably didn't even notice this is the beginners section. The people you seem to despise are simply beginners asking legitimate beginner questions. So, unless you can explain how the root account puts one's computer at risk (other than the usual "they'll own your computer" crap), I suggest you go to some BSD forum and see how long it takes for you to get flamed yourself.

---

### Post by bapoumba on 2007-10-07
The thread is solved. I'm closing here. Some of the comments have not been very nice. When you do not have anything constructive to add, please do not post. Mockery is not an option. Thanks.

---

