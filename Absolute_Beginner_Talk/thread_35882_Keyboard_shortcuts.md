---
title: "Keyboard shortcuts?"
date: 2005-05-20
forum: Absolute Beginner Talk
---

### Post by Insinion on 2005-05-20
I just installed Ubuntu together with windows xp on a dual boot  \\:D/  I've got all the hardware working but i still feel like a 6 year old kid that doesn't know the basics of windows... Is there any page where i can find some shortcuts to use? like on windows i always use 'windows key+d' to get back to my desktop, 'windows key+s'  to search. Would be great to know the combination for the root terminal, getting quite annoying to keep going to apps > sys tools> root. These are probably the easiest things but oh well everyone has to start somewhere right  O:)

edit: btw the smilies aren't functioning properly here lol

---

### Post by Kyral on 2005-05-20
Couple of them are standard. Like Alt-Tab for Window Switching, Alt-F4 to kill a window, etc. But to see and set them all, go System > Preferences > Keyboard Shortcuts

For the Root Terminal, you also just drag it out onto the "Quick Launch" (Windows term) area of the top panel. Or you can just sudo su in a normal terminal

---

### Post by Insinion on 2005-05-20
[QUOTE=Kyral]Couple of them are standard. Like Alt-Tab for Window Switching, Alt-F4 to kill a window, etc. But to see and set them all, go System > Preferences > Keyboard Shortcuts

For the Root Terminal, you also just drag it out onto the "Quick Launch" (Windows term) area of the top panel. Or you can just sudo su in a normal terminal[/QUOTE]
 cheers mate :D your help is appreciated!

---

### Post by Insinion on 2005-05-20
ok i have another question i'm trying to install gftp now and i need to compile it. i extracted everything and typed ./configure in my terminal but i need a C compiler 'configure: error: no acceptable C compiler found in $PATH'. Can any of you help me to install this software?

---

### Post by sethmahoney on 2005-05-20
You don't need to compile GFTP.  Just open up synaptic (System->Administration->Synaptic Package Manager) and search for GFTP or, at the command line, type

[FONT=Fixedsys]sudo apt-get install gftp[/FONT]

If you do want to install a C compiler anyway,

[FONT=Fixedsys]sudo apt-get install gcc[/FONT]

should work.

---

### Post by Kyral on 2005-05-20
Well, first off, you can Apt-Get gFTP.

The second thing is, if you want to compile anything, you will need to apt-get the build-essientials package (dunno if I spelled that right). Use Synaptic if you don't want to use the command line.

And welcome to the Wonderful World Of Linux :D

---

### Post by Insinion on 2005-05-20
Thanks guys i'll try it asap i need to do some other work now  :-| If i run into any other problems i'll know where to ask   :-#

---

### Post by Insinion on 2005-05-20
[QUOTE=Insinion]Thanks guys i'll try it asap i need to do some other work now  :-| If i run into any other problems i'll know where to ask   :-#[/QUOTE]
 Here i am again :p I installed Gftp succesfully i know how to install stuff on linux the right way now (hurray for me...) I still need to figure out how to add a shortcut taskbar. I downloaded some anime from a ftp i'm using but i can't view it cause i don't have any divx/xvid codec installed? Is there a better player that can play these files or do i have to search for the codecs themselfs?

---

### Post by Kyral on 2005-05-20
Another anime fan eh? NICE

Anyway, here is what I did

Apt-Get the w32codecs package, the totem-xine package, and the xine-ui package

that should do it.

If you need Matroska (.mkv) its in Synaptic, can't remember the package

---

### Post by sethmahoney on 2005-05-20
[QUOTE=Insinion]Here i am again :p I installed Gftp succesfully i know how to install stuff on linux the right way now (hurray for me...) I still need to figure out how to add a shortcut taskbar. I downloaded some anime from a ftp i'm using but i can't view it cause i don't have any divx/xvid codec installed? Is there a better player that can play these files or do i have to search for the codecs themselfs?[/QUOTE]
 The shortcut usually appears when you restart Gnome (CTRL+ALT+BACKSPACE).

As far as codecs go, you need to enable the universe and multiverse repositories, which you can do by going to System->Administration->Synaptic Package Manager.  Once in Synaptic, click on Settings->Repositories and check all the boxes that say "universe" or "multiverse" in tiny print.  Installing the codecs themselves is covered here: [http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats)

---

### Post by Insinion on 2005-05-20
[QUOTE=Kyral]Another anime fan eh? NICE

Anyway, here is what I did

Apt-Get the w32codecs package, the totem-xine package, and the xine-ui package

that should do it.

If you need Matroska (.mkv) its in Synaptic, can't remember the package[/QUOTE]
 Yeah i'm a big anime fan i'm trying to rewatch one of my favorite series on linux (Tsukihime). If you could be a bit more detailed for this newbie that should help a lot lol :D I tried sudo apt-get install w32codec, but it couldn't find it and i also couldn't find anything in the package manager :(

edit: i saw sethmahoney's post to late lol gonna try that first now

---

### Post by Kyral on 2005-05-20
Its w32codecs, gotta add a 's"

---

### Post by Insinion on 2005-05-20
still won't work i'm trying to figure that other way out now :)

---

### Post by Kyral on 2005-05-20
hmm, do you have all the Repositories added?

You should try the Automated Script in the Hoary Tips and Tricks forum. It does that and a lot more

---

### Post by Insinion on 2005-05-20
the Automated Script thing worked fine :) i can view it now although i would have learned more if i did it myself  :-# cheers man  :)

---

### Post by Kyral on 2005-05-20
No prob man. I used the script too after my 3rd reinstall (I tend to toy around too much)

Enjoy Linux, and if you need help the Forums is the place to be :D

---

### Post by Insinion on 2005-05-20
Ok i have a small last question lol yeah i'm a bit annoying hehe.. Is it possible to use my own display picture in GAIM(msn messenger)? I can see other peoples images but i can't use my own :(

---

### Post by Kyral on 2005-05-20
That one I can't help you with. I know how to do it on the aim protocol, but I don't touch MSN (or MS for that matter :P)

---

### Post by bruizer on 2005-05-20
You may also find that sometimes the system will just hang if you Ctrl + Alt + Backspace as this kills the gnome session al together. You can just recycle the gnome panel by going to terminal and using
sudo killall gnome-panel

---

### Post by Kyral on 2005-05-20
You don't need the sudo to use killall gnome-panel

---

### Post by Insinion on 2005-05-20
[QUOTE=Kyral]That one I can't help you with. I know how to do it on the aim protocol, but I don't touch MSN (or MS for that matter :P)[/QUOTE]

The problem is all my friends are using it so i'm forced to use it too :) oh and bruizer thanks for the additionial information  :grin:

edit: found it [http://gaim.sourceforge.net/faq.php#q74](http://gaim.sourceforge.net/faq.php#q74)

---

### Post by bruizer on 2005-05-20
Kyral... your right, thanks... I've been doing extra keystrokes without needing them.

---

### Post by Kyral on 2005-05-20
no prob. Always good to lessen the keystokes :D

---

### Post by bruizer on 2005-05-20
especially when the thread is about keyboard shortcuts ;-)

---

### Post by Kyral on 2005-05-20
lol

---

### Post by fng on 2005-05-21
Adding and changing display pictures is hidden very well in gaim.

Start gaim

press ctrl + a

If you dont have an account : make 1
IF you allready have an account : select it and click on 'modify'

in the middle of the account preference screen, you can change the 'Buddy icon'

---

### Post by Insinion on 2005-05-21
here i am again  :) i can finally play windows games using cedega  :grin: I'm getting the hang of linux now. A few friends of mine where impressed with ubuntu so i have to teach them the things i learned the last couple of days. 

I have this problem everytime i start linux any idea how i can fix this? Gftp is working but i think i removed my first install of gftp?
[[IMG]http://img279.echo.cx/img279/2800/screenshot1qh.th.png[/IMG]](http://img279.echo.cx/my.php?image=screenshot1qh.png)

My 2nd question is i only gave linux 5gigs of space when i made my multiboot but i'm beginning to like it more then windows is there any way to add some extra space to my partition where linux is on? 

thanks for helping this newbie with millions of questions  ](*,)

---

### Post by Kyral on 2005-05-21
I dunno about the gftp thing, but the only way you are gonna be able to add more space to your Linux part is to expand its partition. Which might mean shrinking the Windows partition. Also be careful. You will mess up your Linux install if you change where the Linux partition **starts**. Same for XP.

Nice wallpaper BTW :P

---

### Post by Insinion on 2005-05-22
still need some help about the gftp thing and partition size increase :grin:

---

### Post by Kyral on 2005-05-22
/me points to his above post


If you need a PROGRAM, then use QtParted

---

