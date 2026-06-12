---
title: "Pen and tablet mouse"
date: 2005-10-22
forum: Art &amp; Design
---

### Post by ecto on 2005-10-22
Hello, I am an artist who is very much use to using a "pen and mouse tablet" to create various art using art programs like gimp. It helps me whenever i need to CG color a picture. However when i recently moved to linux (and happy i did) my pen portion of the mouse does not move. How do i se up the pen? The model is a Deleter XP PEN. If you know information on how to set up the pen or where i can find the driver then it would be greatly appreciated

---

### Post by ecto on 2005-10-25
Well I have formulated a couple of ways to go about doing this. However, i still need some help.

My tablet type is a Genius MousePen 5x4 tablet. If you know a driver for linux then please respond

I heard theres a way to set up a Pen using the GIMP. If there is any information on how to do this please respond.

I could set up a second pointer device. How would i go about configuring one and how would i switch between two pointer devices?

How can I configure a Pen in linux?

If anyone has information please respond!
If you know anyone good with hardware please ask them to view this thread.
           Truly greateful.
            The CG artist gone linux

---

### Post by werty on 2005-10-25
Hi
ok so there is one more who is having the same problem besides me.
I ve posted a thread in the Hardware forum "ubuntu hoary5.04 hardware help".....
See the post. It might help

[http://www.ubuntuforums.org/showthread.php?t=69496](http://www.ubuntuforums.org/showthread.php?t=69496)

---

### Post by pomalin on 2005-10-25
I have an aiptek tablet, and I did it to work under warty, long time ago it seems :D, I point you to the thread, see the last post to see how I did it, I know it's not the same hardware, but why don't give a try. 

[http://www.ubuntuforums.org/showpost.php?p=74331&postcount=3]("http://www.ubuntuforums.org/showpost.php?p=74331&postcount=3")

---

### Post by ecto on 2005-10-25
did you ever figure out how to fix that b00t problem?

---

### Post by pomalin on 2005-10-30
nope, and for the moment, the pen, that goes with my tablet is dead, so I cannot continu to play with and trying to deal with........:(

---

### Post by ecto on 2005-10-31
well i read somewhere on a how to wacom tablet on linux.org that gpm is needed... Do you think this is true?
Here is the link: [http://www.linux.org/docs/ldp/howto/Wacom-Tablet-HOWTO-4.html](http://www.linux.org/docs/ldp/howto/Wacom-Tablet-HOWTO-4.html)
Why don't you check it out give it a try and tell me what happens...
Perhaps GPM really is needed...
I tried to Private Message 23Meg who seems to have a great deal of knowledge on this subject but has not gotten back to me yet.

---

### Post by ecto on 2005-10-31
GREAT NEWS! 
This must be one of the fastest replies in history but i got some good help from linux.org, nalioth (ubuntu genius on irc), and crimsun (yet another genius mind). 
sudo apt-get gpm
if you type gpm -t help you can check if gpm supports your tablet! Now after this im not sure what to do from there but if you get any new info please reply!

---

### Post by BLTicklemonster on 2005-10-31
Subscribed.

I'm interested, because I picked up a tablet thingy a long time ago, and I'm eager to use it.

---

### Post by ecto on 2005-11-11
yep keeping the thread alive... anyone have any new information about how to run a tablet? I heard i have to do something with xconf or something... How would i go about doing this?

---

### Post by BLTicklemonster on 2005-11-12
I might just clear off some space here and dig mine out. I wonder if I still have the power adapter for it?

---

### Post by 23meg on 2005-11-14
A simple Google search revealed:

[http://www.genius-europe.com/service/faq/tuxtablet.htm](http://www.genius-europe.com/service/faq/tuxtablet.htm)
and in turn
[http://www.stud.fit.vutbr.cz/~xhorak28/index.php.iso-8859-1?page=WizardPen_Driver](http://www.stud.fit.vutbr.cz/~xhorak28/index.php.iso-8859-1?page=WizardPen_Driver)

It looks most certainly doable.

---

### Post by ecto on 2005-11-15
w007 i got the driver but i keep on getting this error 
   1.
      mv -f Makefile Makefile.bak
   2.
      imake -DUseInstalled -I/etc/X11/config/cf
   3.
      In file included from /etc/X11/config/cf/Imake.tmpl:2241,
   4.
                       from Imakefile.c:35:
   5.
      ./Imakefile:5: error: /usr/X11R6/lib/X11/config/Server.tmpl: No such file or directory
   6.
      imake: Exit code 1.
   7.
        Stop.

---

### Post by 23meg on 2005-11-15
I *did a search* for Server.tmpl in my system and it seems I have it in /etc/X11/config/cf . See if you have this file in this location as well, and if so, modify the makefile to point to this location instead.

---

### Post by 23meg on 2005-11-15
try this:```
 ln -s /etc/X11/config/cf/Server.tmpl /usr/X11R6/lib/X11/config
```

---

### Post by ecto on 2005-11-15
`23meg for some reason that doesnt do anything to fix the problem. Is there a way to check if i have it on my system? Do you know any other way to fix this problem?

---

### Post by 23meg on 2005-11-15
Sorry, forgot to say you have to put "sudo" as a prefix to that command; did you?

---

### Post by ecto on 2005-11-16
yeah i mounted sudo -s. The xmkmf file doesnt work... However something strange did happen. A directory known as config ended up in my home directory and so did a file known as Server.tmpl... What exactly happened? What should I do? also i got a message on the other board from a person named Spb_Nick telling me to replace a string here is the link... Can you tell me how to replace a string?
[http://www.stud.fit.vutbr.cz/~xhorak28/unb/forum.php?req=thread&postid=202&nocount](http://www.stud.fit.vutbr.cz/~xhorak28/unb/forum.php?req=thread&postid=202&nocount)

---

### Post by luopio on 2006-01-29
For aiptekers and ppl running clonetablets, I made a howto on getting the latest drivers that a WAY ahead of the ones in the current kernel and xorg. Find it [here]("http://www.ubuntuforums.org/showthread.php?t=122735").

---

