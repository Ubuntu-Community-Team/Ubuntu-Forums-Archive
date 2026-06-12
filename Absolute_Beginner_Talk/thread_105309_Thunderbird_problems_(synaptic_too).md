---
title: "Thunderbird problems (synaptic too)"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by blacklantern on 2005-12-18
Hello all - I've just installed ubuntu, and I'm trying to install thunderbird. I downloaded the zipped file from the thunderbird website, but when I extract the files, I'm not seeing any file that jumps out at me as an install file. In my search to discover what I've been doing wrong, I saw things about this synaptic package manager. When I try to run it, I get no response. Furthermore, when I type "sudo apt-get install mozilla-thunderbird" in the command line, I get no response there either. Any suggestions?

-poor linux newbie just trying to make ends meet- :p

---

### Post by xmastree on 2005-12-18
[QUOTE=blacklantern]I saw things about this synaptic package manager. When I try to run it, I get no response.[/QUOTE]What did you do to try to run it?
It should be there in the **System>Administration** menu. If that doesn't work, open up a terminal and type ```
sudo synaptic
```You should be asked for the password, and synaptic should open. If it doesn't, there ought to be an error message.
Post that error here and we'll see if we can find your problem.

---

### Post by blacklantern on 2005-12-18
Absolutely nothing happens when I type that in. And when I run the 'thunderbird' executable in the terminal, the terminal pops up for a split second and disappears.

-edit- oh, and going through synaptic through system->administration gets no response either. 

hlpplzthx! :p

---

### Post by xmastree on 2005-12-18
Nothing? Very strange... :confused:

If snaptic isn't installed for some reason, you would get **command not found** as a response. 
Type this in a terminal and post the response here.
```
ls -l /usr/sbin/sy*
```Mine gives:
```
chris@ubuntu:/usr/sbin$ ls -l /usr/sbin/sy*
-rwxr-xr-x  1 root root 774952 2005-04-06 06:39 /usr/sbin/synaptic
-rwxr-xr-x  1 root root   3758 2005-04-05 23:10 /usr/sbin/syslogd-listfiles
-rwxr-xr-x  1 root root   3984 2005-04-05 23:10 /usr/sbin/syslog-facility
```

---

### Post by blacklantern on 2005-12-18
Same for me, for the most part.

mford1@mfordcomp:~$ ls -l /usr/sbin/sy*
-rwxr-xr-x  1 root root 939208 2005-10-06 17:46 /usr/sbin/synaptic
-rwxr-xr-x  1 root root   3758 2005-09-23 15:08 /usr/sbin/syslogd-listfiles
-rwxr-xr-x  1 root root   3984 2005-09-23 15:08 /usr/sbin/syslog-facility

-edit-
Update - when I actually went to the folder in the filebrowser, I got the following error when trying to run synaptic:

"You must run this program as the root user."

---

### Post by xmastree on 2005-12-18
So, synaptic is there, top of the list.

What happens if you try to run it as a regular user?
```
/usr/sbin/synaptic
```you should get an error saying you must be root.

---

### Post by blacklantern on 2005-12-18
[QUOTE=blacklantern]
-edit-
Update - when I actually went to the folder in the filebrowser, I got the following error when trying to run synaptic:

"You must run this program as the root user."[/QUOTE]


I get that error when running the command from the terminal or within the filebrowser with the gui.

---

### Post by xmastree on 2005-12-18
Good. you should get that error.
Now, type ```
sudo synaptic
``` in a terminal and that will run the program as root, it will ask for your password.

---

### Post by blacklantern on 2005-12-18
you know what? for some reason, synaptic doesn't start when I put the sudo command in the command line within the panel. However, when I do it in the terminal, it starts up. In any case, I'm all good. Thanx, xmastree!

---

### Post by blacklantern on 2005-12-18
[QUOTE=blacklantern]I get that error when running the command from the terminal or within the filebrowser with the gui.[/QUOTE]

*laughs* beat you to it. Thanx!

---

### Post by wfx on 2005-12-18
Do you use Breezy?
Post some output (mark it with the left mouse button and press the middle here).
#1 Terminal: cat /etc/apt/sources.list

Maybe some one will hit me but do also
#2 Terminal: sudo su (and type in youre user-password)
#3 Terminal:  apt-cache search mozilla-thunderbird

If apt found the thunderbird client then
#4 Terminal:  apt-get install mozilla-thunderbird

---

### Post by xmastree on 2005-12-18
Now, get rid of that zipped thunderbird you downloaded, find thunderbird in synaptic and install it from there. Also, you ought to enable the extra repositories so you can install all the other good stuff, like video/sudio codecs and the like.

---

### Post by blacklantern on 2005-12-18
*has just woken up* Done and done. I have another question, and I guess I'll just put it here now so it has time to stew during my drive back home from school. The resolution seems to be off a little bit - the right side of the windows adn the panels hang off the screen just a bit. I had to put a new panel on the right side just so I can see all of the window, and even that new panel hangs off a bit. Any ideas?

---

### Post by bigtexjc42 on 2005-12-30
I have the same problem blacklantern had on the Synaptic run.  I'm with both of you in terms of settings and feedback all the way to sudo synaptic.

In the terminal mode, just like when I run it from the GUI, it asks me for password, which I provide, then all I get is another prompt.  If I retry sudo synaptic, I don't even get the password request, just another prompt.

I've also tried to run Add Applications in the same fashion, and same result - why would I be getting locked out?

---

### Post by Brigrat on 2005-12-31
xmastree,

     Are you familiar with evolution?  I have both evolution and thunderbird installed and want to move my old mail into thunderbird is the an easy way to do this???

---

### Post by xmastree on 2005-12-31
Sorry, I've never used Evolution. :confused: 

However, if you look [**here**](http://www.mozilla.org/support/thunderbird/faq#q2.9), you'll see a way to import messages in standard mbox format.
All you need to do is figure out how to export them from evolution.

---

### Post by Brigrat on 2005-12-31
Thanks I'll give it a try.

For got how to say thanks in tagalog...

---

