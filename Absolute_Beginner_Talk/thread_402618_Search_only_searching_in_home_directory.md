---
title: "Search only searching in home directory"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by limitedmage on 2007-04-06
Hi,

I've been having this problem that, when I want to search something, it will only look in my home folder. In Application>Accesories>Search, I have gone to the preferences window and added the whole root (/) directory. Still, it keeps searching only in home (/home/julip, in my case).

Any help would be greatly apperciated.

---

### Post by gilforsyth on 2007-04-06
I'm not quite sure how to fix that problem, but here are two alternate methods.  
In a terminal, you can type 
```
locate <filename>
```

or you can install Beagle, which is a great search program.  
Add the beagle repository to your source list
Terminal
```
sudo gedit /etc/apt/sources.list
```

Add the following line:
deb [http://beagle-project.org/files/ubuntu/edgy/](http://beagle-project.org/files/ubuntu/edgy/) ./

Save & Close

Then, in terminal
```
sudo apt-get update
sudo apt-get install beagle
```

Hope that helps.

---

### Post by limitedmage on 2007-04-08
Thanks, gilforsyth. It searches OK now when I choose the Search dock applet. However, when I open Applications>Accesories>Search, it has a permanent yellow notice that says that my files are being indexed. And I search and nothing is found. It's been like that for the past couple of days. Not that I use that way of searching, but it'd be great if anyone could help me fix it.

---

### Post by tom56 on 2007-04-08
The indexing will take a while on the first run. Try leaving your computer logged in when you're not using it to allow it to get the index done. Search (Beagle) only looks in your home folder by default for the simple reason that you are unlikely to need to look anywhere else.

Everywhere outside of home is read-only to stop you from damaging any system files by accident.

Not looking outisde of home also saves the computer from building a list of all your files; it instead just builds a list (index) of the files in home. this makes indexing quicker.

What were you looking for outside of home? locate will work as posted above but most system files will be in the same place on everyone's computer so if you ask where it is we can point you in the right direction.

Hope this helps!

---

