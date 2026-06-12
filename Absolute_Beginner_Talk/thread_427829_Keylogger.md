---
title: "Keylogger"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-04-29
Can someone please post a download to a linux keylogger

---

### Post by Sef on 2007-04-29
Why do you want to download a GNU/Linux keylogger?

---

### Post by mojo123 on 2007-04-29
to see the activity on my computer from other users

---

### Post by starcraft.man on 2007-04-29
LOL... Uh, are you paranoid? If you make seperate accounts they will stay outta your stuff... More to the point key loggers will give you only text typed and is mostly used for hacking other people's accounts...

---

### Post by mojo123 on 2007-04-29
my sister likes to download stuff and i wanna prove to my parents she cant go on my pc

---

### Post by starcraft.man on 2007-04-29
Put a nice random password on your account and that will lock her out... why do you need a key logger?

---

### Post by mojo123 on 2007-04-29
because shes forced to do her homework can i set a password for downloading?

---

### Post by Kingsley on 2007-04-29
You could edit your /etc/hosts file to block download sites that you know she goes on.

---

### Post by starcraft.man on 2007-04-29
Hmmm, I see... I don't really think that you can stop her from downloading if you allow her to browse with firefox. You are the admin though, and I assume she can't install or alter anything if she's just a user. So, long as you don't tell her the root pass she can't modify the comp. And I assume at worst she can download files to her usr folders.

I'd just make her account for her and know the password, long as she doesn't know the root pass she can't reset it either I don't believe >.>. Isn't that good enough?

Edit: The problem with that solution Kingsley is one would have to manually block each site, not very practical unless you have lots of time on your hands... and she can always find a site you haven't blocked.

---

### Post by zetsumei on 2007-04-29
Tell your parents shes not using your computer.  One reason why I switched to linux was to keep my family out of my freaking computer.  My family hardly knows how to use Windows, let along Linux.  So heres what you do.

1) tell your parents shes not using your computer
2) put a random password on the root account and your account
3) make her a account with limited access and block those download sites

A keylogger won't be helpful much because theres a chance you could get infected trying to keep her off your computer.  Either make a keylogger yourself or just do the steps above.

---

### Post by supersonicdarky on 2007-04-29
google is your friend

[http://sourceforge.net/projects/lkl/](http://sourceforge.net/projects/lkl/)

just installed it and it works

---

### Post by aysiu on 2007-04-29
Make her home directory a separate partition and make the partition size small.

You can have Ubuntu's / be 100 GB, for example, and then have /home/sister be 50 MB. Then she won't be able to download anything except small stuff.

---

### Post by starcraft.man on 2007-04-29
Good ol' source forge and LOL at Zatesumi. :p

Edit: *smacks self for not thinking of aysiu's answer*

---

### Post by mojo123 on 2007-04-29
omg thank you guys so fast replies! BTW how do i install it?

---

### Post by starcraft.man on 2007-04-29
No problemo, I think everyone tries their best :D.

---

### Post by supersonicdarky on 2007-04-29
the keylogger needs a keymap... what is it and how do i choose one?

---

extract from archive > ./configure > sudo make install

---

### Post by aysiu on 2007-04-29
I still don't understand how a keylogger helps in this situation.

Can't you download things without pressing keys? Isn't that what a mouse is for?

---

### Post by Jeff24K on 2007-04-29
> **mojo123 said:**
> my sister likes to download stuff and i wanna prove to my parents she cant go on my pc

Keyloggers won't help you here, as most downloads are clicked links. No keys to log. Regardless of that, for every measure you take to block/monitor usage there's a countermeasure. You're heading down the path of an arms race neither of you can ultimately win.

At risk of sounding like a preacher, and without knowing any of hte facts, I think you're attacking the problem from teh wrong angle. The spy stuff will do more damage than good. Better to resolve differences in a civil manner. She's family, after all. ;)

---

### Post by mojo123 on 2007-04-29
im sorry im a newbie but what? ^^

---

### Post by supersonicdarky on 2007-04-29
> **mojo123 said:**
> im sorry im a newbie but what? ^^
download the .tar.gz
extract it (either right click > extract here or in terminal **tar zxvf *<filename>***
go to the folder (lkl)
in terminal: **./configure**
when done, use the command **sudo make install**

---

### Post by starcraft.man on 2007-04-29
I think the point trying to be made here mojo, is a person doesn't actually have to click anything to download a file, though I suppose the keylogger would record the website unless it was a bookmark. The basic problem is a key logger is more passive and after the fact, it can't actually stop her from doing anything... whereas the small partition would limit her. Maybe even less than 50 mb if you wanna be mean :p.

---

### Post by mojo123 on 2007-04-29
You guys are right i should take this another angle but i just want this to be quick and easy, its a one time thing (just have to prove)






alan@alan-laptop:~/Desktop/lkl$ sudo make install
cd . \
          && CONFIG_FILES= CONFIG_HEADERS=config.h \
             /bin/bash ./config.status
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands
make[1]: Entering directory `/home/alan/Desktop/lkl'
/bin/bash ./mkinstalldirs /usr/local/bin
  /usr/bin/install -c lkl /usr/local/bin/lkl
make[1]: Nothing to be done for `install-data-am'.
make[1]: Leaving directory `/home/alan/Desktop/lkl'

How do i run it

---

### Post by supersonicdarky on 2007-04-29
**sudo lkl -h ** for help on the prog

---

you should listen to other people tho, a keylogger is not an answer here

---

### Post by zetsumei on 2007-04-29
> **starcraft.man said:**
> Good ol' source forge and LOL at Zatesumi. :p

Edit: *smacks self for not thinking of aysiu's answer*

What was so funny :(

*sick of not being taken seriously* :(

---

### Post by mojo123 on 2007-04-29
guys i know ^ i need a quick and easy way
I installed it where is the output to see the log

---

### Post by starcraft.man on 2007-04-29
> **zetsumei said:**
> What was so funny :(

*sick of not being taken seriously* :(

Awwww, sorry zetsumei, I wasn't laughing at ya... I just thought it was funny you moved to linux to stop parents from getting on your pc. 

Come on, I'm always being silly :)

---

### Post by zetsumei on 2007-04-29
LOL.  I did move though I got tired of parents and my brothers getting on my pc to "do homework/work"  so I'm like it'll give me a reason to go back to linux LOL

---

### Post by mojo123 on 2007-04-29
3 pages wow

---

### Post by zetsumei on 2007-04-29
it kinda got offtopic LOL...I'm not helping am I?

---

### Post by mojo123 on 2007-04-29
not at all

---

### Post by apjone on 2007-05-21
[http://dansguardian.org/](http://dansguardian.org/)

You can block sites / phrases / extensions and file types. I use it with squid.

---

### Post by fakie_flip on 2007-05-28
> **mojo123 said:**
> Can someone please post a download to a linux keylogger

Enable universe.

```
sudo apt-get install lkl
```

---

### Post by fakie_flip on 2007-05-28
lkl doesn't work for usb keyboards. i was going to test this with my usb keyboard, but i can't get it to compile.

[http://www.thc.org/releases.php?q=logger&x=0&y=0](http://www.thc.org/releases.php?q=logger&x=0&y=0)

---

### Post by apjone on 2007-05-29
I think it would be better to set up a proxy server and content filter like squid & dansguardian as this would track, block, any site she went on to.

---

### Post by coldstatue on 2008-06-12
What is it about keyloggers that make people get so paranoid? It wasn't a moral question. Good thing this doesn't happen more often. If someone wants to know who is using their computer while away, or that their spouse is getting drugs from craigslist, that's THEIR BUSINESS. This isn't a religious board. 

"You want an audio editor? WHYYYY? IT MUST BE FOR NEFARIOUS PURPOSES!!!"

---

