---
title: "How to make ubuntu to remember settings?"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by j2000 on 2006-04-23
How?:( 

Settings like DNS address or keyboard language...

---

### Post by adamkane on 2006-04-23
It's a moot point. Ubuntu asks for DNS and keyboard settings on every new install/re-install.

---

### Post by ssam on 2006-04-23
if this is with the live cd then it is not possible in breezy.

in dapper it is possible see [https://wiki.ubuntu.com/LiveCDPersistence](https://wiki.ubuntu.com/LiveCDPersistence), though it looks like quite a lot of work currently, you might want to look at puppy linux, dsl, or knoppix. or just install ubuntu

---

### Post by j2000 on 2006-04-23
no, i am not using liveCD or smth...and didnt reinstall it.
I'd just wanted to make it remember my settings after i reboot or turn off my machine...thats all](*,)

---

### Post by ssam on 2006-04-23
thats odd. how are you connecting to the internet?

---

### Post by j2000 on 2006-04-24
i am connecting through a router to my isp.
But, what's the difference?
I just asking for help to get my ubuntu to remember settings i've done.

---

### Post by Sokraates on 2006-04-24
The difference is, that Ubuntu (like any OS) should remember your settings. So what you encounter is a bug. Possibly due to some configuration gone wrong, since I haven't heard of this before.

Asking what should be remembered helps us to (hopefully) solve your problem, since we know where the information should be saved.

Now for some basics:
1) What version of Ubuntu do you use? Warty, Hoary, Breezy (recommended) or Dapper?
2) What desktop environment do you use? KDE, GNOME, something else?

---

### Post by j2000 on 2006-04-25
at last, someone who knows something about something :)

what's the possibilities that my ubuntu is encuntering a bug?
btw, i used Breezy with GNOME;

But, i've ruined my OS with allowing root to log in graphically... :(
maybe someone can help me with this...telling me ,what went wrong...

Now i am about to install Dapper beta,hoping that beta can be upgrated to full working version...

---

### Post by Rinzwind on 2006-04-25
I think I understand your problem and think I know what happend:

When you use root account to access graphical things you will create files with root-rights. If you then connect with a non-root account that user is not allowed to delete or change these files and you'll error out. 

It's desired behaviour tho... and thus not a bug. Tho very annoying :) 

Did you change those settings whilst using root? Cuz that would coincide with the problem I ran into a while ago (and what was cuz of that too): I accidently ran gnome with root and had a crash. The Xsessions file was created but not deleted leaving me with no way to log on. After deleting the file it worked again (ofcourse).

It's all about knowing what file to track down and delete or alter the rights of that file.

Oh and if someone with more experience than me contradicts my post believe him/her. I'm a newbie as much as alot of others here. ;)

---

### Post by Sokraates on 2006-04-25
First and foremost: allowing root to login by GUI does not ruin anything (unless you consider a somewhat less secure system ruined).

root is considered a further user and his account is saved in /root. Any other user will have their files saved in /home/*username*. Ubuntu doesn't have a root-account per default, so you've created it along the way.

I already suspected, that you've involuntarily changed some permissions. If Rinzwind's advise doesn't help you, please tell us, what you did after creating your root-account. Which files did you modify as root?

---

