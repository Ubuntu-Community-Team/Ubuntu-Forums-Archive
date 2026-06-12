---
title: "What's the best IM?"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by ajmorris on 2007-01-07
I was just wondering what your opinions on the best Instant Messenger are? I don't particularly like Gaim. I have used Kopete which is pretty good and amsn which is also good.

---

### Post by Vorian on 2007-01-07
Yahoo!

(too bad you couldn't hear me sing that)

---

### Post by ajmorris on 2007-01-07
is there an ubuntu repository for that?

---

### Post by Cariboo1938 on 2007-01-07
> **Vorian said:**
> Yahoo!

(too bad you couldn't hear me sing that)
Does it work for Ubuntu6.10-amd64?

---

### Post by tchoklat on 2007-01-07
I prefer Kopete - meets my needs!

---

### Post by Vorian on 2007-01-07
> **ajmorris said:**
> is there an ubuntu repository for that?

> **Cariboo1938 said:**
> Does it work for Ubuntu6.10-amd64?

download it, install it.  It's available in a .deb file:mrgreen:

[http://messenger.yahoo.com/](http://messenger.yahoo.com/)

---

### Post by solracarevir on 2007-01-08
ill go with amsn all the way down, for me is the best.

---

### Post by shooh on 2007-01-08
> **Vorian said:**
> download it, install it.  It's available in a .deb file:mrgreen:

[http://messenger.yahoo.com/](http://messenger.yahoo.com/)

dpkg -i ymessenger_1.0.4_1_i386.deb 
Unpacking ymessenger (from ymessenger_1.0.4_1_i386.deb) ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libgtk1.2 (>= 1.2.0); however:
  Package libgtk1.2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger

---

### Post by shanepardue on 2007-01-08
I'm a big kopete fan other than the fact that mac users see "style=" before every message I've sent. Gaim is solid too just not as pretty as kopete.

---

### Post by wildkarde on 2007-01-08
I was not happy with gaim either and was looking for something else.
I tried ayttm but found it to be too buggy. 

Today i use centericq.  
[http://thekonst.net/centericq/](http://thekonst.net/centericq/)

---

### Post by po0f on 2007-01-08
shooh,

Install the missing packages.  From a terminal, run:
```
[FONT="Courier New"]$ sudo aptitude update && sudo aptitude install libgdk-pixbuf2 libgtk1.2 libssl[/FONT]
```

Alternatively, you could search for those packages in Synaptic and install them that way if you feel more comfortable with a GUI.

I couldn't find xlibs in the repos, it looks like it is just a transitional package for upgrading from Debian.  It depends on libx11, which I think would already be installed.

---

### Post by IYY on 2007-01-08
I like Gossip best, but it's only for Jabber (Google Talk), while most of my friends use MSN. So, Gaim it is for me.

---

### Post by mahy on 2007-01-08
No matter which IM service u prefer, use Gaim because of the OTR encryption. :cool:

---

### Post by Goliash on 2007-01-08
I think the best IM for KDE user is SIM. Many options, many protocols.
```
sudo apt-get install sim
```

---

### Post by ajmorris on 2007-01-08
> **wildkarde said:**
> I was not happy with gaim either and was looking for something else.
I tried ayttm but found it to be too buggy. 

Today i use centericq.  
[http://thekonst.net/centericq/](http://thekonst.net/centericq/)

i just went to the site and tried to download the debian one but i get this error
[PHP]sudo dpkg -i centericq_4.21.0-16_alpha.deb 
dpkg: error processing centericq_4.21.0-16_alpha.deb (--install):
 package architecture (alpha) does not match system (i386)
Errors were encountered while processing:
 centericq_4.21.0-16_alpha.deb
[/PHP]

should i just get the tar.gz?

---

### Post by wildkarde on 2007-01-08
> **ajmorris said:**
> i just went to the site and tried to download the debian one but i get this error
[PHP]sudo dpkg -i centericq_4.21.0-16_alpha.deb 
dpkg: error processing centericq_4.21.0-16_alpha.deb (--install):
 package architecture (alpha) does not match system (i386)
Errors were encountered while processing:
 centericq_4.21.0-16_alpha.deb
[/PHP]

should i just get the tar.gz?

My mistake.  I only posted the link so you guys had something to read in case you wanted more details about centericq.

Application is available in the repos.  :)

---

### Post by ajmorris on 2007-01-08
> **wildkarde said:**
> My mistake.  I only posted the link so you guys had something to read in case you wanted more details about centericq.

Application is available in the repos.  :)

lol. thanks. i should have checked those first.

---

### Post by wildkarde on 2007-01-08
> **ajmorris said:**
> lol. thanks. i should have checked those first.

hehe, no problem.  let me know if you like it.

---

### Post by Pobega on 2007-01-08
How can someone not like Gaim? I understand if you're on KDE (Because GTK apps look fugly), but on a GTK based environment how can you dislike it? It supports virtually every protocol, it's quick and efficient, and supports *almost* every feature available on the normal instant messenging clients (With that exception of the **annoying** nudge feature from MSN).

But when something goes wrong with my install I use pebrot, which I do think is available in the repositories. Terminal IM clients are fun to use :)

---

### Post by wildkarde on 2007-01-08
In my case there is one thing that bugs me enough about gaim to make me stop using it and that is a new feature implemented in their latest beta (in the repos, i believe beta5 is out) in which you cannot set text to a specific font size.  It has incremental choices (smaller, medium, larger -- something along those lines) which makes the text in my messages appear particularly larger than usual for my buddies.  I guess i can try the latest beta...

---

yeah, i'll try beta5

---

### Post by Cariboo1938 on 2007-01-08
> **shooh said:**
> dpkg -i ymessenger_1.0.4_1_i386.deb 
Unpacking ymessenger (from ymessenger_1.0.4_1_i386.deb) ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libgtk1.2 (>= 1.2.0); however:
  Package libgtk1.2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger:confused: Please post what you are doing to solve the dependency problems?!:confused:

---

### Post by CCBalla10 on 2007-01-08
gAIM is the way to go...really nice

---

### Post by Obor on 2007-01-08
> **Cariboo1938 said:**
> :confused: Please post what you are doing to solve the dependency problems?!:confused:

Read the previous page :-? :) 

> **po0f said:**
> 
shooh,

Install the missing packages. From a terminal, run:
Code:

$ sudo aptitude update && sudo aptitude install libgdk-pixbuf2 libgtk1.2 libssl

Alternatively, you could search for those packages in Synaptic and install them that way if you feel more comfortable with a GUI.

I couldn't find xlibs in the repos, it looks like it is just a transitional package for upgrading from Debian. It depends on libx11, which I think would already be installed.


---

### Post by ajmorris on 2007-01-08
> **wildkarde said:**
> hehe, no problem.  let me know if you like it.

Just a very noobie question. How do i open centericq?

The attached screenshot is what happens when i run it from a shell.

And also if i do a centericq --options it doesn't have an option to execute the application.](*,)

---

### Post by seijuro on 2007-01-08
I used Gaim in Gnome and Kopete in KDE both are quite good but I tend to favor Kopete.

---

### Post by pissedoffdude on 2007-01-08
> **ajmorris said:**
> i just went to the site and tried to download the debian one but i get this error
[PHP]sudo dpkg -i centericq_4.21.0-16_alpha.deb 
dpkg: error processing centericq_4.21.0-16_alpha.deb (--install):
 package architecture (alpha) does not match system (i386)
Errors were encountered while processing:
 centericq_4.21.0-16_alpha.deb
[/PHP]

should i just get the tar.gz?

you need to do a sudo dpkg -i --force-architecture* packagename_i386*.deb

---

### Post by hendoc on 2007-01-08
Kopete works great and has all my Yahoo friends covered.

---

### Post by darweth on 2007-01-08
I use gAIM.  I would use Kopete if it supported Direct IM.  I would use Adium if it was available for Linux. :x

---

### Post by wildkarde on 2007-01-08
> **ajmorris said:**
> Just a very noobie question. How do i open centericq?

The attached screenshot is what happens when i run it from a shell.

And also if i do a centericq --options it doesn't have an option to execute the application.](*,)

before you can start using the application, you gotta set the options.  If everything looks good, click on the [done] button.  It will then ask you for your account information.  After you finish, click done again and you'll be set.  :)

---

### Post by ajmorris on 2007-01-09
> **wildkarde said:**
> before you can start using the application, you gotta set the options.  If everything looks good, click on the [done] button.  It will then ask you for your account information.  After you finish, click done again and you'll be set.  :)

how do i click the done button?

When i try nothing happens. And i can't tab to it either.

---

### Post by ajmorris on 2007-01-09
nvm i just found out.

lol
You just press sideways when at the bottom of the list.

---

