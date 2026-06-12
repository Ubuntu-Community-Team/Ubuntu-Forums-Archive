---
title: "How do I install... anything?"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by qwew on 2006-06-26
I just started dual-booting Ubuntu today, and after updating and going through the wiki I'm still unable to install pretty much anything. Earlier I managed to mess up my entire install by messing around with some drivers, so I'm kinda reluctant to try out anything now . :neutral: 

Anyway, I've tried installing stuff through any of the ways described in the wiki. I used the add/remove tool to install a random program (adept), and while the OS tells me that everything went fine and dandy whenever I try to start the program I'll get the following: "Details: Failed to execute child process "kdesu" (No such file or directory)" It doesn't seem to be able to find back any of the stuff on the "File System" drive. Some of the programs that come installed with the package (eg. Bittorrent) and are shown in the add/remove tool to be installed also seem to be missing completely, there is no link in any of the menus and searching the File System turns up no results. Where do the folders go when a program is installed anyway? I can't make anything of the way it's ordened.

This is but one of the things I just can't seem to change. The resolution of my screen won't be turned higher than 1024x786 for who knows what reason, I've downloaded some tarballs and can extract them but that's as far as it goes, can't install them. Did I miss something after the install, do I need to change more settings somewhere before I can actually use this OS? I'm unable to do practically anything here.

Any help is appreciated.

---

### Post by Kimm on 2006-06-26
I suggest you use "Synaptic Package Manager" to install/remove software. You have a quite large library of software there.

For tarballs:
You need to build the program, open a terminal and type:

cd <folder where files are extracted>
./configure
make
make install

./configure may (and probably will at first) throw some errors at you, complaning about missing libraries, that means you need to install *-dev packages before you can build the program.
Its uncommon that you need to build software in Ubuntu (unless you are like me, and want top-of-the-line stuff.)

---

### Post by Irony on 2006-06-26
This tell you how to install things; [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by MaximB on 2006-06-26
just b/z I've posten it afew hours ago - I copy/paste my instructions :

here is a very easy way to install programs in ubuntu - at the first time I tried to install somthing I sat for 2 hours just learning the new programs I can get for free.
go to applications (it's on the top left of your screen , if you are using "gnome" )
there in the bottem you will see add/remove programs - click on it.
let the list update (it will ask you to go to tje internet , you MUST have an internet for this or you couldn't download progrms )
now - on the left side of the new panel that opened you will see categories
like games , programing , graphics - chose what you intersed in and you will see TONS of programs to chose from , but before you do so I recommend you to check to bottem 2 boxes so you can have many more programs. (it's restricted and somthing ,I can't remmember now )

now just chose what you want and click install
for advanced mode click on "advanced" - but for now it will just confuse you.

hope I helped.

---

### Post by ira miles on 2007-04-16
I just installed ubuntu as my only OS on my G4 Quicksilver. Understanding that things would probably be slow for me, I have other computer options around the house. Fortunately, I can already do all the things I need to do for work on Ubuntu! 
I have had no luck installing new software. When I open the add/remove software as indicated above, it begins to load and then just disappears as if I never launched it. Any suggestions. 
As well in this process I have tried to expand my repositories using Synaptic Package Manager, but the interface is totally different than what the tutorial screenshots had. Am I so different because I am using a PPC architecture....please help a noob, respond today!

---

