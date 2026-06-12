---
title: "Help with symbolic links please? maybe?"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by itzpapalotl on 2007-07-16
Hey! So I just had a bit of a brainstorm, and I'm hoping this is possible.
One of the major advantages I am hoping to obtain by going POSIX at my school, is the ability for people to get at their stuff from home without punching holes through my ALICE unit with gotomypc or any of the other incomprehensible VPN garbage out there.

Now. We have a server. Its a heck of a machine, and it is being used to basically run the whole show. Meaning that the server holds all of our school documents, and well as being our web server. 

Now... I'm thinking, but I don't know..
I can make a directory /var/www/userhome
and in that directory I can have password protected folders for each user. I can then use a symbolic link (ln -s i think) from the users folder in /var/www/userhome to their folder in /home. That way they can open up a directory of their /home folder from the web yes but without having to store the information in two places?

Does this sound right?
Anybody done this?
Is this Kosher?
Security implications I should be worried about?
Also... like what would my commands look like to set this up ...say for user "Jimbob"who has /home/jimbob and needs that to be sybolically linked to /var/www/userhome/jimbob

is it just:

ln -s /www/var/userhome/jimbob /home/jimbob

This just seems to good to pass up, and a heck of a lot more reliable than VPN

---

### Post by Warren Watts on 2007-07-16
I personally think a more secure solution would be to set up an FTP server (like vsftp).  This would allow your users to be "chrooted" to their individual home folders, and would allow them easily download and uplload files to their home folder.

I have vsftp set up in just that manner on my system.  My daughter loves it.  She can access all her files from any computer anywhere.

---

### Post by itzpapalotl on 2007-07-16
Seee... that's why I post these things here... 

You are right. That is the way to go. I probably even knew that somehow in the back of my head.
Heh... I just had one of those "Well HEY!!!" moments. Yeah. I'll use ftp. You know... designed to do what I want to do and all.

But for the record, it IS possible the way I described yes?

---

### Post by Warren Watts on 2007-07-16
Perhaps...  But through the browser, users could only download files that were already there; they wouldn't be able to upload anything.

---

### Post by HermanAB on 2007-07-16
Apache won't follow links out of it's document root if it is installed properly.

Vsftp or proftp is a much better idea, but make sure that your users have proper random passwords with 9 or more characters or you *will* get hacked (I use 16 characters, semi pronounceable).

If you want to have a web based solution, then look at Owl:
[http://owl.sourceforge.net/](http://owl.sourceforge.net/)

or docman:
[http://docman.sourceforge.net/](http://docman.sourceforge.net/)

Cheers,

Herman

---

