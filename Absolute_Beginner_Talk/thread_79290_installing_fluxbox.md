---
title: "installing fluxbox"
date: 2005-10-19
forum: Absolute Beginner Talk
---

### Post by fuscia on 2005-10-19
ok, so far i've gotten the package untarred to my desktop. i did sudo apt-get install Desktop/fluxbox-0.1.14 as well as just plain fluxbox-0.1.14 and in both cases, everything was fine except for being able to find the package. (and no, i don't really know what i'm doing.  what an adventure, eh?)

---

### Post by albertoramirez on 2005-10-19
in a terminal issue the following

sudo apt-get install fluxbox

and then close the session and then star a new one.  In the session button, choose fluxbox

---

### Post by fuscia on 2005-10-19
[QUOTE=albertoramirez]in a terminal issue the following

sudo apt-get install fluxbox

and then close the session and then star a new one.  In the session button, choose fluxbox[/QUOTE]


the problem is: when i put in 'sudo apt-get install fluxbox', i receive an error message saying the package can't be found. it's on my desktop. i'm guessing it need to be in an another location for it to be installed?

---

### Post by andyluo on 2005-10-19
$sudo dpkg -i "path of fluxbox"
don't contain the quote.

Oops, the fluxbox file should be a .deb

---

### Post by stuporglue on 2005-10-19
[QUOTE=fuscia]the problem is: when i put in 'sudo apt-get install fluxbox', i receive an error message saying the package can't be found. [/QUOTE]

Have you enabled universe repositories? I don't think you even need multiverse for fluxbox. 

You can do it through Synaptic (ask if you prefer the GUI!), or edit /etc/apt/sources.list and uncomment the universe repos.

---

### Post by fuscia on 2005-10-20
[QUOTE=andyluo]$sudo dpkg -i "path of fluxbox"
don't contain the quote.

Oops, the fluxbox file should be a .deb[/QUOTE]

ok, i went back to get the debian package and discover the ubuntu package. i downloaded it, type in the above and got back an error saying that package libstdc++5 is not installed and that fluxbox is dependent on it, leaving fluxbox unconfigured.

---

### Post by fuscia on 2005-10-20
[QUOTE=stuporglue]Have you enabled universe repositories? I don't think you even need multiverse for fluxbox. 

You can do it through Synaptic (ask if you prefer the GUI!), or edit /etc/apt/sources.list and uncomment the universe repos.[/QUOTE]

i looked up just in time to see this go sailing over my head. what your saying is not totally foreign to me, but i really don't know what you're talking about. sounds important. please tell me more.

---

### Post by patrick295767 on 2005-10-20
[QUOTE=andyluo]$sudo dpkg -i "path of fluxbox"
don't contain the quote.

Oops, the fluxbox file should be a .deb[/QUOTE]

I did used apt-get ... 

I downloaded fluxbox on the web site ... then 
as mentioned above: 
[http://fluxbox.sourceforge.net/](http://fluxbox.sourceforge.net/)

dpkg -i fluxbox_file.deb

And that's it !
(cos I also got Broken packages)

Enjoy Fluxbox !

---
I use now fvwm, and customize like H..... !!

---

### Post by fuscia on 2005-10-20
starting over again, i went to [http://logicvortex.net/debian/fluxbox/](http://logicvortex.net/debian/fluxbox/) and downnloaded the package for ubuntu breezy. i opened my terminal and entered "sudo dpkg -i Desktop/fluxbox_0.9.14-1_i386.deb". everything looked ok until this error message appeared...

[i]"Unpacking replacement fluxbox ...
dpkg: dependency problems prevent configuration of fluxbox:
 fluxbox depends on menu (>= 2.1.19); however:
  Package menu is not installed.
 fluxbox depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
dpkg: error processing fluxbox (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fluxbox"[/i]

i logged out and tried to log back in for a fluxbox session (the option was listed). i then received and error message refering to the missing package, libstdc++5. what's my next move?

---

### Post by fuscia on 2005-10-20
[QUOTE=stuporglue]Have you enabled universe repositories? I don't think you even need multiverse for fluxbox. [/QUOTE]

uh...i don't know.:confused:

---

### Post by fuscia on 2005-10-20
DOH! i found it in synaptic. now all i need is some menu (>=2.1.19).

---

### Post by wishyjr on 2005-10-20
ok matey, looks like you need some c++ lib package install as well. When an app/program (i.e. in this case Fluxbox) need something extra its called a dependancy. you got this:

fluxbox depends on libstdc++5 (>= 1:3.3.4-1); however:
Package libstdc++5 is not installed.

that to me says you need some sort of c++ package. I dunno but try:

sudo apt-get install build-essential

see if that helps


EDIT: oops, too late :)!!

---

### Post by fuscia on 2005-10-20
[QUOTE=wishyjr]EDIT: oops, too late :)!![/QUOTE]

thanks for the response. i can't find this menu (>= 2.1.19). any ideas on that?

---

### Post by wishyjr on 2005-10-20
i can't find this menu (>= 2.1.19). any ideas on that?

what is it? a version of something i presume. can you post up a copy of some code?

---

### Post by fuscia on 2005-10-20
[QUOTE=wishyjr]i can't find this menu (>= 2.1.19). any ideas on that?

what is it? a version of something i presume. can you post up a copy of some code?[/QUOTE]

i don't even know what it is. i just got an error message saying it was missing. i assume as with that other thing, it must be something outside of fluxbox that i have to install. it's not in synaptic, as far as i can tell.

---

### Post by fuscia on 2005-10-20
i found libsasl2-modules version 2.1.19-1.5ubuntu4 pluggable authentication modules for sasl. is that at all related, or is it just a coincidence?

---

