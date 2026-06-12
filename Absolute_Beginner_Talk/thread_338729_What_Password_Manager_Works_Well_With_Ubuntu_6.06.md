---
title: "What Password Manager Works Well With Ubuntu 6.06?"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by jimalan on 2007-01-14
I'm a newbie looking for a good password manager for use with Ubuntu 6.06 and FF 2.0.  What do you recommend?  I need something that remembers passwords and fills in forms and hopefully the URL so I can just click and go.  Does the FF Password Manager work OK?  How about Figaro?  The Figaro site tells me to download the file but where do I put it?  At the moment my downloads all go to the Desktop.  Can I unzip it and extract the file directly to a directory?  Do I need any additional files or libraries to make it work?  Thanks for any help or recommendations you can offer.

---

### Post by euler_fan on 2007-01-14
I personally don't like letting Firefox manage my passwords (except for a few that are defacto public anyway--long story). I don't have a technical reason for that, just paranoia. Thus, I use KeePassX (avaliable via the applications) to manage mine and simply memorize them. I also don't have that many :rolleyes: Also can't say I've tried Figaro, but might take a look since you mentioned it.

I know there are a number of them on [www.mozilla.com](www.mozilla.com) here [URL="https://addons.mozilla.org/search.php?cat=12&app=firefox&appfilter=firefox&type"]Firefox Extentions Privacy and Security
[/URL]
if you are willing to sift through them. I haven't tried any of them for the aforementioned reason, but have looked at them and there appears to be a good variety of them with a wide variety of capabilities. 
Hope that's helpful. 
EDIT: See [URL="http://www.securityfocus.com/infocus/1883"]Password management concerns with IE and Firefox Part 2
[/URL] for a reason to be paranoid. I linked only part two because it links part 1 in the first line or so. I just downloaded Password Hasher add-on for FF2 and it says it uses the browser's secure database, which should make it vulnerable to the kinds of attacks described in the article. By the by, I use FEBE (Firefox Extension Backup something or other, can be found in same listing linked above) which will back up the password database, and since Password Hasher uses the database that would let you back up your passwords against random destruction.

EDIT: I'm not a security expert, but Figaro looks decent. I have read Blowfish is one of the better algorithms, especially on smaller files (which is probably your situation) and since it says it can handle you bookmarks when set up correctly looks like a good possible solution. Unfortunately, the edgy repos don't have it, but who knows about the dapper ones (if you are using dapper)? 

EDIT CON'T Otherwise install you have two choices: alien (to use the .rpm files) or download the .tar.gz file to your desktop, go into the terminal, cd to the desktop (cd ~/Desktop) then untar the file (tar -xvzf <filename with extensions>,  type cd, type cd <the name of the new folder it made in your /home/<myname> folder, type ./configure, get the packages it tells you to (via synaptic probably), repeat until it says everything is fine, type make, then if that works type sudo make install and that should be it. You may have to find the start-up command and run it command line, but if they build a nice gui for gnome I am thinking they probably already took care of making it show up in your application menu. There are plenty of guides to installing from source floating around here if you want some more detail than what I just gave. Good luck!

---

### Post by mdsmedia on 2007-01-14
I've found that Firefox does a good job of autocompleting form entries for you.

I've also used the password manager in Firefox and I quite like it. You can set a main password that locks the password manager, so you have to remember your main password but not the others.

I've found it helps when you go back to a site after not using it for some time and it will autofill, or you can ask it to show passwords so you can look down the list...which is therefore kept for you and there's no need to have a hard copy of passwords.

I'm not sure of the criteria, but some secure sites will not allow Firefox to remember your login. I think that's a good thing, but for other sites I don't want to have Firefox remember, I just click on "never for this site" in the options given.

---

### Post by kerry_s on 2007-01-14
There's a couple in the repos "gpass", "mypasswordsafe" and "keepass" just make sure you have all your repos turned on. then just do a search in synaptic. I just use Firefox's built in one, but i'm simple i don't have a lot of password sites to enter. I just did a search using "password" in synaptic.

---

