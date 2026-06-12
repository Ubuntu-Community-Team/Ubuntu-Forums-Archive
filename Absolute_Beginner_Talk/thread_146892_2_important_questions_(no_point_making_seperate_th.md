---
title: "2 important questions (no point making seperate threads)"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by yatesDELTA on 2006-03-19
okay then i suppose this has been covered before but my first question is how do i install a printer. it is a lexmark and i have heard rumours of ocmplete incompatibility (i hope not cos i need to print my homework)

my second question is can i install a diferent interface? I got a live cd of pclinuxos and i really like it. But i dont wnat to go through the agro of installing it andl osing more data. So cn anyone tell me how to install KDE?

thanks, anyhelp would be appreciated

(The second question might make me stay here, not move to pclos if i can do it)

---

### Post by alamba on 2006-03-19
Lexmark Printer - Other than the usual point and click to install a printer I wouldn't be able to guide you much further.

KDE - Assuming that you have Ubuntu (GNOME) installed, the following would install KDE:

sudo apt-get update
sudo apt-get install kubuntu-desktop

A

---

### Post by Sef on 2006-03-19
> okay then i suppose this has been covered before but my first question is how do i install a printer. it is a lexmark and i have heard rumours of ocmplete incompatibility (i hope not cos i need to print my homework)

Lexmark is generally not supported. Best bets are Epson and HP.  To check if your printer is supported or not, go here:  [http://linuxprinting.org/]("http://linuxprinting.org/")

What type of Lexmark printer do you have?  Someone might have gotten it up and running and could help you with your printer.

> my second question is can i install a diferent interface? I got a live cd of pclinuxos and i really like it. But i dont wnat to go through the agro of installing it andl osing more data. So cn anyone tell me how to install KDE?

Applications > Accessories > Terminal > then type first > sudo apt-get update > password > then when it finishes, type this > sudo apt-get install kubuntu-desktop > enter

When logging in, click on the session menu and you will have choice of which desktop to run.

---

### Post by yatesDELTA on 2006-03-19
edited post. my silliness

---

### Post by yatesDELTA on 2006-03-19
I am now on KDE. Now how the hell do i configure it?

(this is much better)
oh is kubuntu a seperate operating system?
also why did it install diferent programs. becuase i want to remove some of them

---

### Post by steve.horsley on 2006-03-19
Not sure what you mean by how do you configure it. What are you trying to do?

Same operating system. Two different desktops - Gnome and KDE. They are just the graphical window system on top of the O/S. Due to CD space constraints, you don't get both on one installer disk. 

Gnome and KDE tend to have their own suite of graphical utilities that come along with them.

---

### Post by WoodyMahan on 2006-03-19
SO after you install KDE can you still use GNOME if you want?  Can you switch back and forth between them?

---

### Post by aysiu on 2006-03-19
Lexmark's generally not got that great compatibility, but there is [a Lexmark HowTo](http://ubuntuforums.org/showthread.php?t=49714&page=1) on these forums. Your printer may be in there.

Once you've installed KDE, log out, click on the word *Sessions* and select KDE. Then log back in again.

You can uninstall any unwanted programs using Adept, Synaptic Package Manager, or apt-get.

And, no, Kubuntu and Ubuntu are not separate operating systems--they are the same operating system with different desktop environments and different default programs.

---

### Post by yatesDELTA on 2006-03-19
thanks for the help poeples

---

