---
title: "root,sudo,su....what the....?"
date: 2007-04-07
forum: Apple PPC Users
---

### Post by machead5 on 2007-04-07
Hi all
I hope someone can explain this. 
I'm using 6.06 and I'm new to Ubuntu. The first thing that struck me was the lack of a root password until I discovered that some stuff can be done with sudo. The problem is I don't seem to have write access to most all directories and if I try and save anything I get a permissions error! 

So then how do I get to permissions to allow me to edit files? 

Thanks in advance

---

### Post by ZoiaGuyver on 2007-04-07
Well sudo should give you pretty much root privalages but in a more secure manner. 

You should be able to edit and save through terminal using the command

sudo nano <file name>

sudo vi <file name>

Or for graphical editing with gedit or kate

sudo gedit <file name>

sudo kate <file name>

You should be able to write to all directories with the sudo command infront (this does get awkward when using the gui filemanagers though) if you need or wanna use root acess you can do

sudo passwd root


This will ask for a New password for root and allow you to su rather than sudo. I will say though that the GUI by default will not allow root logins (tbh you wont want them to either it's a big security issue).

Hope this helps

---

### Post by machead5 on 2007-04-07
Thanks ZoiaGuyver
I'll experiment and let you know how I go.

Cheers
:)

---

### Post by PriceChild on 2007-04-07
[uwiki]RootSudo[/uwiki]for more info

---

### Post by bapoumba on 2007-04-07
You may want to read [this]("http://https://help.ubuntu.com/community/RootSudo?highlight=%28rootsudo%29").
Feel free to ask questions.

Edit: Hello, Pricey, I'm being slow again :D

---

### Post by ZoiaGuyver on 2007-04-07
:oops: yeah forgot there was that on the wiki aswell

---

### Post by machead5 on 2007-04-07
Thanks PriceChild for the link, it's very useful.
Hey bapoumba, I didn't get the https info... is it really relevent?

Cheers

---

### Post by Tylo on 2007-04-07
In the Nautilus file browser you can also right click files and folers and open them as root using one of the options under the context menu. I'm not in Ubuntu at the moment...but I think it's under the "Scripts" option in the context menu.

---

### Post by bapoumba on 2007-04-07
> **machead5 said:**
> Hey bapoumba, I didn't get the https info... is it really relevent?

Cheers
:shock: 
I pasted the same link as PriceChild (the [RootSudo]("https://help.ubuntu.com/community/RootSudo") one). I have no idea what happened! Sorry, and cheers to you too :)

---

