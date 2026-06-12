---
title: "How do I configure extra mouse and keyboard functions to work in Ubuntu?"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by nala on 2006-03-01
I have a Logitech MX1000 laser moue and a Microsoft Naturals 4000 usb keyboard. They work as a mouse and keyboard basically should in Ubuntu, however, there are a lot of extra features on both the mouse and keyboard that I would really like to use. 

I've tried to figure this out myself but I'm lost. Manually configuring keyboard shortcuts only got me so far. I didn't find any drivers available from Microsoft or Logitech. Repeated bouts of Googling didn't help much either. 

Is there anything I can do? Please go very slowly, as I just installed Ubuntu days ago and I am not at all familliar with commands for the terminal, where files are located and so forth.

---

### Post by gborzi on 2006-03-01
There is a multimedia keys howto in the wiki, but you can also try keytouch at:
[http://keytouch.sourceforge.net/index.html](http://keytouch.sourceforge.net/index.html)
I used the howto to configure the (few) extra keys on my laptop, and keytouch for my Logitech MX3000 keyboard.

---

### Post by Xaviar on 2006-03-01
That looks like a great idea.  I've downloaded it but I don't know how to install it.

---

### Post by nala on 2006-03-01
[QUOTE=gborzi]There is a multimedia keys howto in the wiki, but you can also try keytouch at:
[http://keytouch.sourceforge.net/index.html](http://keytouch.sourceforge.net/index.html)
I used the howto to configure the (few) extra keys on my laptop, and keytouch for my Logitech MX3000 keyboard.[/QUOTE]

Thank you very much. I will try that out. Hopefully I can get something to work with my extra mouse buttons...

---

### Post by Coelocanth on 2006-03-01
> **Xaviar]That looks like a great idea.  I've downloaded it but I don't know how to install it.[/QUOTE]

Here's the instructions from the How To on the website where you got the program  said:**
> 

Before you are going to install keyTouch you have to be sure that the following is installed on your system:
- GTK 2
- gksu
- X11 and Xlib
The compiling and installation procedure differs a bit from the common procedure. Read the following steps:

   1. Go to the unpacked directory.
   2. Run:

      ./configure

   3. Run to compile:

      make

   4. Run (as root) to install:

      make install

   5. Go to the directory keytouch-config by running:

      cd keytouch-config

      ... and repeat steps 2-4.
   6. Go to the directory keytouch-keyboard in the unpacked directory by running:

      cd ../keytouch-keyboard

      ... and repeat steps 2-4.

**NOTE: If you are using Ubuntu (or another sudo using distribution) open keytouch-keyboard/keytouch-keyboard in your favorite text-editor and replace "gksu" by "gksudo".**

**EDIT* Note: these instructions are for Keytouch 2.

---

### Post by Xaviar on 2006-03-02
Thanks Coelocanth.  This is where I show how wet behind the ears I am.  When you say 'go to the unpacked directory' do you mean go to it by opening a window and clicking on it or do I have to start a terminal and type in an address?  This must be annoying and I know that before too long I'll be astounded by how simple it is but right now I have no clue.

---

### Post by Coelocanth on 2006-03-02
[QUOTE=Xaviar]Thanks Coelocanth.  This is where I show how wet behind the ears I am.  When you say 'go to the unpacked directory' do you mean go to it by opening a window and clicking on it or do I have to start a terminal and type in an address?  This must be annoying and I know that before too long I'll be astounded by how simple it is but right now I have no clue.[/QUOTE]

No problem; not annoying at all. I'm basically a noob at this myself, having only been using Ubuntu/Linux for about 3 weeks. Where the guide says to go to the unpacked directory: when you dpkg the .deb file, it will install into the proper directory (it should indicate this with the text output when you run the unpackaging command).

Just cd to that directory in terminal, then follow the commands the guide gives. Any command that requires root priveleges will require you to type sudo as the beginning of the command. So,

sudo *command*

As you can tell from my explanation, I'm very noobish too, so forgive me if it's vague or even if it turns out to be erroneous. Good luck!

---

### Post by Xaviar on 2006-03-03
Thanks for the advice but I'm still stuck.  I have the programme downloaded and have unpacked it.  It is in my Home folder.  I open a terminal and I type

cd ./ keytouch-2.1.0 ./configure

and I hit return, now the Terminal wants me to type something else and hit return.  When I type 
make (return) or 
make install (return) or 
sudo make install (return) or 
sudo keytouch-2.1.0 make install (return) or 
sudo ./ keytouch-2.1.0 make install (return) 
the Terminal says no rule to make target install or command not found.  Can you please tell me the exact text I need to type as the guide is confusing the hell out of me.  It presupposes that I know the basic premise behind command line computing and I very much don't.  Is there really no way for me to simply open a window and double click on an icon to make this programme install?  I have an A4 Tech (RFKB-25) multimedia keyboard with a lot of useless buttons right now and the System > Preferences > Keyboard Shortcuts menu doesn't allow me to really get specific (which I'm hoping this programme will).  A lot of people migrating from the frustration of Windows bring with them a basic knowledge of DOS or MS-DOS but I don't.  I've been at this for 2 days now (embarrassingly enough) and my cats are beginning to point and giggle.

---

