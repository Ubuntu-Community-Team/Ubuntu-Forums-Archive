---
title: "Having a couple little problems"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2006-08-30
Hi everyone. I just re-installed Ubuntu again, after having tried out Kubuntu and then Zenwalk. Feels good to be back in this environment again, but there are a few kinks I need to work out now. 

The first problem is that I want to copy/paste a bookmark.html file from my external HD to my current firefox folder where the bookmark file is now. Only thing is, I'm not sure of 
A) Which profile folder it is, since there's more than one. One is /usr/lib/firefox and the other I believe is usr/share/firefox   Maybe there's more, I'm not sure.

B) I have to be root in order to do this right ? How do I actually achieve that ? I've opened the terminal, and typed su, but then after putting in my password (the same one that I log on with ?) it says that it can't be authenticated ? 

I'm not really sure of what's up there. Hope someone can help me out. 

Doug

---

### Post by taurus on 2006-08-30
Your personal bookmark for firefox is in ~/.mozilla/firefox/<numbers and letters>.default/bookmarks.html...

---

### Post by Anonii on 2006-08-30
> **Sweet Spot said:**
> Hi everyone. I just re-installed Ubuntu again, after having tried out Kubuntu and then Zenwalk. Feels good to be back in this environment again, but there are a few kinks I need to work out now. 

The first problem is that I want to copy/paste a bookmark.html file from my external HD to my current firefox folder where the bookmark file is now. Only thing is, I'm not sure of 
A) Which profile folder it is, since there's more than one. One is /usr/lib/firefox and the other I believe is usr/share/firefox   Maybe there's more, I'm not sure.

B) I have to be root in order to do this right ? How do I actually achieve that ? I've opened the terminal, and typed su, but then after putting in my password (the same one that I log on with ?) it says that it can't be authenticated ? 

I'm not really sure of what's up there. Hope someone can help me out. 

Doug

I'll help you in your second question. Ubuntu doesnt really "love" su, it prefers sudo, which gives you superuser (root) powahs for just one command. To have the powers of "su", to be permanently root, till you leave the console, you either use:
_"sudo su_"
or _"sudo -s -H"_

---

### Post by Sweet Spot on 2006-08-30
> **taurus said:**
> Your personal bookmark for firefox is in ~/.mozilla/firefox/<numbers and letters>.default/bookmarks.html...

I'm really sorry if this comes off as being dumb but, the only mozilla/firefox folders I see are in the /usr/lib and /usr/share   folders. And in those, the bookmark file is in the /defaults/profile folder. 

Secondly, thanks anonii for the tip. I can log in as sudo (guess I was doing "su" for too long in Zenwalk) now, but how exactly does this help me in transfering files back and forth ? I guess this is one aspect of either Linux/Ubuntu that I don't understand yet. 

I have to be root, in order to have write permissions for basic tasks such as copy/pasting in folders, but using the terminal is a separate process from working on the X windows right ? So how do I enable myself as root, when browsing my filesystem, so that I can do such simple things as pasting that .html file into the Firefox folder ?

I know that this means holding my hand and talking to me as if I was a little kid, but that's probably what I need right now, since most of the time I don't fully comprehend things when they're just "put out there" in a line of code. 

Doug

---

### Post by Anonii on 2006-08-30
Check:
man mv (cut-paste)
man cp (copy-paste)

For example to paste that .html in your Firefox folder you have to do:

> cd <directory_of_the_html_file>
cp <html_file>.html <directory_where_you_want_to_save_it>.html

Got it? :)

(Possibly missunderstood you ^_^)

---

### Post by Sweet Spot on 2006-08-30
Lol, not really but... If that's how I have to do it, I'll have to "get it". So, I can't just have temporary root access and simply right click on said .html file > copy > paste into desired directory ? Because that would just be much more simple. 

Because to be honest, what you typed, seems like an aweful lot of work for what I think should be such a simple thing to do. 

Doug

---

### Post by Anonii on 2006-08-30
> **Sweet Spot said:**
> Lol, not really but... If that's how I have to do it, I'll have to "get it". So, I can't just have temporary root access and simply right click on said .html file > copy > paste into desired directory ? Because that would just be much more simple. 

Because to be honest, what you typed, seems like an aweful lot of work for what I think should be such a simple thing to do. 

Doug
Then you will love my little friend:

**"gksudo nautilus"**

This will bring up Nautilus with root access. If you are using GNOME, of course.

Also, that command can be put in a launcher.

PS: If I misunderstood you again, you will have to get help from someone else, because I gotta go :/ I'll be back in 4-5hours, tho :P

---

### Post by mcduck on 2006-08-30
> **Sweet Spot said:**
> I'm really sorry if this comes off as being dumb but, the only mozilla/firefox folders I see are in the /usr/lib and /usr/share   folders. And in those, the bookmark file is in the /defaults/profile folder.If you have evere started firefox on that machine, there is a '.mozilla' directory in your home dir. Now, all files/firectories with a name starting with a dot are hidden, so you have to set Nautilus to show hidden files. The option is in View/Show Hidden Files (or just press ctrl-h).

As that directory is in your home, you won't need root/sudo privileges to copy your bookmarks there.

For root access, you should never need to use root on Ubuntu. To run commands with admin privileges put a 'sudo' before every command that would otherwise need to run as root. Then use your own password when sudo asks for one. For grapgical apps use gksudo instead of sudo, and you'll get a nice GUI message asking for the password. Passwords for sudo and gksudo are stored for 15 minutes so you won't actually need to type your password after every command. And, as mentioned, you can run 'gksudo nautilus' to open file manager as root. But be careful with it, and be sure to close it as soon as you don't absolutely need it.

---

### Post by Sweet Spot on 2006-08-30
Greeeat ! Thanks you guys. I will be careful should I ever do gksudo naut", but thankfully I didn't have to because of mcduck's tip. That was the trick which did it, thanks alot to both of you though for your time and patience. 

Now, on to another "little problem". 

Take care, 

Doug

---

